---
layout: post
title: REBUG - Record the bug and replay it later 
tags: [general, ideas]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

> What if you could travel back in time?

I want to share with you idea for a new tool I've got during my work for <a href="http://transpond.com">Transpond</a>. 
In a nutshell, Transpond is building web-based tool for making Facebook applications. Sound exciting? 

Have you developed anything for Facebook before? Facebook application is a piece of code living on your own server but heavily talking to Facebook APIs. 
And Facebook is unfortunately something you cannot take home and run it on your own local server for debugging purposes. 
You need to develop and debug your application against the live site (respectively sandbox they provide).

And here is the problem. There is a class of bugs caused by Facebook (i.e. they break something during updates) 
or caused by specific data (i.e. encoding problems because a user entered a text with diacritics). These bugs are tricky to reproduce. 
First type is reported by QA but gets fixed before developer looks at it. Second type is hard because 
developer may be not able to reproduce exactly the same state (for example newsfeed causing the bug is already replaced with newer content which is not exposing the bug or developer is logged under different account than QA tester).

Many times these bugs are really trivial. I can look at Net panel in Firebug or javascript console and the cause is obvious. 
But this information is not available during reading bugreport in Bugzilla. Sometimes I would give fortune for a link moving me back in time in front of the browser with the bug exposed...

#### Meet the Rebug

> A tool which is able to reproduce browser state for debugging purposes

Example usage scenario (heavy AJAX web app with many requests to the cloud)

**A Tester's session:**

* Tester installs browser extension "Rebug"
* Tester does QA work and in case she encounters a bug:
  * clicks "REBUG" button</span>
  * this will serialize browser state onto remote server and put URL into clipboard
  * tester opens an issue in favorite issue tracker (as she would normally do) and paste generated link along with description for later inspection by a developer

**A Developer's session:**

* Developer installs browser extension "Rebug"
* Developer opens the issue and clicks the rebug link
  * Developer sees realtime replay of tester's session
  * Browser ends in the same state as when rebug button was pressed by the tester
 
#### What real-world problem does it solve?

* Debugging complex javascript-heavy AJAXy apps is hard. Especially when the app operates in the cloud by communicating with various APIs and services.&nbsp;
* QA people will get no-brainer tool to store "crash dump" of their browser session ex-post. Programmers will get easy tool to restore broken session in their development environment (Firefox+Firebug in the first phase).
* Better dev-team productivity.

#### The Implementation

The Implementation consists of two fundamental parts:

- proxy server (provided as a service)
- macro recorder (browser extension)

**Proxy server**

* During tester's session proxy server is recording all HTTP traffic, when Rebug button is clicked, new record is created by "zipping" all traffic data into one package giving it unique session ID.
* During developer's session every request is served back from zip file (effectively mocking "internet" at the time the session was recorded).

**Macro recorder**
    
* During tester's session macro recorder is recording all user's actions and generating reproducible script.
* During developer's session recorded script is replayed back.

Technology of macro recorders was already developed by extensions like iMacros or Selenium. I've also done one attempt for <a href="http://xrefresh.binaryage.com">XRefresh extension</a> in the past (a very challenging problem).

#### Possible setups:

**Fully hosted solution:**
<img class="blog-image" src="{{site.url}}/images/drawing_sV0QB63mkDgRXGUKF-UyLZg_153.png" title="Fully hosted solution">

**Serviced solution:**
<img class="blog-image" src="{{site.url}}/images/drawing_sY_p-Pz7WbcM4w8OOXKaI3Q_51.png" title="Serviced solution">

**Near proxy solution:**
<img class="blog-image" src="{{site.url}}/images/drawing_sPkzVArT9_K6tqbFWjwCWIg_48.png" title="Near proxy solution">

**Decentralized solution:**
<img class="blog-image" src="{{site.url}}/images/drawing_s53VQRbszouhzGpRAnSMJ-g_119.png" title="Decentralized solution">

**Single machine setup:**
<img class="blog-image" src="{{site.url}}/images/drawing_sarVlC_ISonwxJB-Df3SmhQ_18.png" title="Single machine solution">

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

External browser inputs should be simulated as closely as possible (browser version, platform, date/time, screen size?, etc.) and developer should be unobtrusively noticed about differences between his setup and user's setup - but it is not expected developer to have exactly same setup as testing user (for example developer has a Firebug extension which may not be the case of tester).

#### Future direction

REBUG can be used as a mockup server for automated testing infrastructure. Browser sessions can be generated synthetically and consumed by defined test suites. Recording and hand-making approach can be mixed. Thanks to storage being a git repo, it can be edited independently on saving proxy. Reading proxy then can be used by automated tests runner.

Note: Recent <a href="http://www.softwareishard.com/blog/firebug/http-archive-specification/">HTTP Archive initiative</a> is a move in a good direction. Look forward to see more tools tackling this problem.