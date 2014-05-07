---
layout: post
title: Future direction of XRefresh
tags: [xrefresh, ideas]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/xrefresh-128.png" class="intro-icon"/>

**[XRefresh](http://xrefresh.binaryage.com) is a simple tool which is able to refresh a web page in the browser in reaction to a file modification.**

#### Here is the problem

> I want to prototype HTML and CSS changes on live page (Firebug), but I don't want to manually sync the changes back to my original sources.

XRefresh is especially useful on dual monitor system. You can stay in your favorite editor and as you type it will preview the page automatically on a secondary monitor in open browser window.

#### The implementation

XRefresh is implemented as a browser extension and a filesystem monitor. These two components talk to each other using TCP connection. Whenever something changes, the monitor notifies the extension which then instructs the browser to do a full refresh of the page.

This solution has some advantages:

* it is independent of the text editor or IDE you are using for web development
* is is independent of the server-side stack (you can run locally any server technology you want)
* it is possible to use XRefresh over a network (in case you are editing files on a remote box)

Full page refresh is a robust solution and works pretty well for simple static pages, but it has one big drawback for dynamic pages. After refresh you usually lose state of the web application. Let's say you have AJAX application, which has some dynamic UI. Say, a HTML dialog opened after clicking on a button. For prototyping such an UI you have to first click through application to get into the required state. But XRefresh does a full refresh which forces you to this again and again after every tiny change to a file. This destroys the original productivity workflow. As I was doing more and more complex pages I was thinking how to solve this problem...

The first idea was to use some kind of macro recorder and replay user actions after every refresh automatically. This seemed as a pretty general solution in theory but didn't work in reality. In Firefox I tried to implement simple listener for user events like mouse clicks and key strokes and then tried to replay them on top of new page. This approach had terrible timing issues and also failed because not all events were 100% reproducible. Some products like iMacros, Selenium or other tools are trying to implement something like that. Maybe they have found some way how to do it well, but from this experience I doubt it is a robust solution in more complex cases.

The second idea was to solve this just for CSS prototyping. In case the page uses externally linked CSS files, it is easily possible to refresh just external CSS file and let browser do the hard work of updating styles without full refresh. This worked surprisingly well. With TextMate on OSX I was able to get to a Firebug-like CSS prototyping experience. The only drawback is that it puts constraints on XRefresh user: it works only for CSS, you have to reference CSS files externally, no CSS dependencies via @import and you have to keep to a simple URL mapping schema (I'm using fuzzy filename&lt;-&gt;url matcher to decide what CSS references to update).

#### But what about live HTML update? 

This is still an open problem and much harder. I'm thinking about a solution for this. It is not robust but I believe it should be useful for 99% of cases (at least when user learns safe editing patterns).

The idea is to have some kind of smart diff algorithm. Whenever file changes don't do a full refresh, but instead reload just affected HTML file into the browser in the background. Because we know the original HTML source and the new HTML source we can do a diff of these. This way we can identify modified chunks. With the knowledge of HTML parsing we can extend these chunks into some kind of "address plus modification descriptor". Address can be selector, xpath or something like anchoring regexp. Modification is something like "replace aaa with bbb" or "insert xxx after yyy" or even "set innerHTML of addressed node" in case the change went across HTML node boundaries. In javascript we can then implement updater function which is able to consume these patches and apply them to live DOM.

Of course, this is far from a robust solution. But we don't need a robust one, we need __good enough solution__(tm). Smart diff encoding which maps well on DOM is one important task. The other difficult problem is having these changes not interfere with dynamic page functionality. As you can see obvious complication is event handlers attached to existing DOM nodes. Less obvious is javascript expando properties on DOM nodes: with replacing whole DOM subtrees we are going to lose them. But this may be not as bad as it seems. The updater can be smart enough to reuse existing nodes whenever possible. Or Firefox 3.6 has a new API for iterating event handlers on nodes. Theoretically we can collect important expando javascript properties and event handlers and re-apply them on new nodes. Yeah, sounds like a lot of troubles and there are probably more problems I quite don't see right now. But the problem is really challenging (at least for me).

I'm thinking about a proof-of-concept project where we can test this idea.

#### The idea

**Create a web-based editor for HTML and CSS with live-update feature**

* Create a bookmarklet which enables user to inject 'updater.js' javascript file into any HTML page.
* Implement updater.js
  * it opens a new browser window and embeds there Bespin code editor (they released standalone embeddable version a few days ago), put parent page's HTML in there
  * it implements protocol for incrementally changing live page by accepting and applying
    * CSS "patches"
    * HTML "patches"
* In the code window implement watcher.js, which watches changes in the code editor, continuously making diffs and translating them into a series of patches (if applicable)
* Implement simple communication channel between parent window and code window (as simple as window.opener.update(jsonMessage) ). 
  Wire watcher.js to send messages to updater.js.

#### The challenging parts:

* design protocol for communication between watcher and updater
* implement smart diff analyzer or maybe full HTML/CSS parser on watcher side
* implement efficient updater (use DOM APIs for incrementally updating HTML and CSS or some suitable library)

#### Keep in mind:

* by "patches" I don't necessarily mean unified patches but rather
high-level JSON descriptions of what to change (a good granularity for
CSS may be CSS-rules level, for HTML minimal enclosing innerHTML-like
snippets addressed by XPaths or CSS selectors?)
* updater.js should be as simple as possible and not pollute global
namespace (imagine inclusion into really messy pages), patching
intelligence should be shifted more towards watcher.js side (imagine
watcher implementation server-side)
* the protocol should possibly work well over the network

#### Possible applications I see right now:

* the next version of XRefresh of course :-)
* web-based HTML code editors (there are plenty of them in the wild and to be honest I'm also working on one of them)
* replacement for Firebug's feature for rewriting pieces of HTML or live Bespin-based CSS editor in Firebug
* development tool for PhoneGap based mobile applications (watcher sends updates directly into running page in webkit in the iPhone simulator)

#### Is this viable?

I'm not going to write such a thing right away. It definitely does not look like a weekend project. I'd like to validate this idea and ideally gather like-minded hackers to evaluate it. What do you think?