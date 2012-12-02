---
layout: post
title: REBUG - Record the bug and replay it later 
tags: [general, ideas]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

> What if you could travel back in time?

I want to share with you an idea for a new tool I've had during my work for <a href="http://transpond.com">Transpond</a>. 
In a nutshell, Transpond is building web-based tool for making Facebook applications. Sound exciting? 

Have you developed anything for Facebook before? A Facebook application is a piece of code living on your own server but heavily talking to Facebook APIs. 
And Facebook is unfortunately something you cannot take home and run it on your own local server for debugging purposes. 
You need to develop and debug your application against the live site (or the sandbox they provide).

And here is the problem. There is a class of bugs caused by Facebook (i.e. they break something during updates) 
and a class caused by specific data (e.g. encoding problems because a user entered text with diacritics). These bugs are tricky to reproduce. 
The first type is reported by QA but gets fixed before the developer sees it. The second type is hard because the 
developer may be not able to reproduce exactly the same state (for example a newsfeed causing the bug is already replaced with newer content which is not exposing the bug, or the developer is logged in under different account than QA tester).

Many times these bugs are really trivial. I can look at the Net panel in Firebug or javascript console and the cause is obvious. 
But this information is not available when reading a bugreport in Bugzilla. Sometimes I would a give fortune for a link moving me back in time and in front of the browser with the bug exposed...

#### Meet Rebug

> A tool which is able to reproduce browser state for debugging purposes

Example usage scenario (heavy AJAX web app with many requests to the cloud)

**A Tester's session:**

* Tester installs browser extension "Rebug"
* Tester does QA work and if she encounters a bug:
  * she clicks "REBUG" button</span>
  * this will serialize the browser state onto remote server and put a URL into the clipboard
  * tester opens an issue in her favorite issue tracker (as she would normally do) and pastes the generated link along with description for later inspection by a developer

**A Developer's session:**

* Developer installs browser extension "Rebug"
* Developer opens the issue and clicks the rebug link
  * Developer sees realtime replay of tester's session
  * Browser ends in the same state as when rebug button was pressed by the tester
 
#### What real-world problem does it solve?

* Debugging complex, javascript-heavy AJAXy apps is hard. Especially when the app operates in the cloud by communicating with various APIs and services.&nbsp;
* QA people will get a no-brainer tool to store "crash dump" of their browser session after the fact. Programmers will get an easy tool to restore a broken session in their development environment (Firefox+Firebug in the first phase).
* Better dev-team productivity.

#### The Implementation

The Implementation consists of two fundamental parts:

- proxy server (provided as a service)
- macro recorder (browser extension)

**Proxy server**

* During tester's session the proxy server is recording all HTTP traffic. When the Rebug button is clicked, a new record is created by "zipping" all traffic data into one package and giving it a unique session ID.
* During developer's session every request is served back from zip file (effectively mocking "internet" at the time the session was recorded).

**Macro recorder**
    
* During tester's session macro recorder is recording all the user's actions and generating reproducible script.
* During developer's session recorded script is played back.

The technology of macro recorders was already developed by extensions like iMacros or Selenium. I've also made one attempt for <a href="http://xrefresh.binaryage.com">XRefresh extension</a> in the past (a very challenging problem).

#### Possible setups:

**Fully hosted solution:**
<img class="blog-image" src="/images/drawing_sV0QB63mkDgRXGUKF-UyLZg_153.png" title="Fully hosted solution">

**Serviced solution:**
<img class="blog-image" src="/images/drawing_sY_p-Pz7WbcM4w8OOXKaI3Q_51.png" title="Serviced solution">

**Near proxy solution:**
<img class="blog-image" src="/images/drawing_sPkzVArT9_K6tqbFWjwCWIg_48.png" title="Near proxy solution">

**Decentralized solution:**
<img class="blog-image" src="/images/drawing_s53VQRbszouhzGpRAnSMJ-g_119.png" title="Decentralized solution">

**Single machine setup:**
<img class="blog-image" src="/images/drawing_sarVlC_ISonwxJB-Df3SmhQ_18.png" title="Single machine solution">

#### Implementation notes

* decouple reading proxy from saving proxy
* decouple session storage from proxies
* multi-platform proxy implementation
* recorded script should be applicable to different browsers
* recorded session should be editable ...
  * test-case creation?
  * mapping requests to filesystem?
  * session storage as git repo?
* developer session should run bypassing all caches

External browser inputs should be simulated as closely as possible (browser version, platform, date/time, screen size?, etc.) and the developer should be unobtrusively notified about differences between his setup and the user's setup - but it is not expected the developer will have exactly the same setup as testing user (for example developer has the Firebug extension which may not be the case of tester).

#### Future direction

REBUG can be used as a mockup server for automated testing infrastructure. Browser sessions can be generated synthetically and consumed by defined test suites. Recording and hand-making approaches can be mixed. Thanks to storage being a git repo, it can be edited independently on the saving proxy. Reading proxy then can be used by automated tests runner.

Note: Recent <a href="http://www.softwareishard.com/blog/firebug/http-archive-specification/">HTTP Archive initiative</a> is a move in a good direction. Look forward to seeing more tools tackling this problem.