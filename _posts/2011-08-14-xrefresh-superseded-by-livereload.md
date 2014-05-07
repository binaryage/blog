---
layout: post
title: XRefresh superseded by LiveReload
tags: [xrefresh]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/xrefresh-128.png" class="intro-icon"/>

**[XRefresh](http://xrefresh.binaryage.com) is a productivity tool for web developers.<br>It will continuously refresh a web page in a browser due to a local source file editing.**

#### LiveReload is the next evolution of XRefresh

There is a new tool inspired by XRefresh called [LiveReload](http://livereload.com). I have been watching [its development](https://github.com/mockko/livereload) for some time and decided to deprecate XRefresh in favor of LiveReload. Simply it is a better version of XRefresh done the way I would implement it today. 

#### LiveReload 2.0 will be a commercial update

[Andrey](https://github.com/andreyvit) and [other contributors](https://github.com/mockko/livereload/contributors) have put a lot of effort into making LiveReload cross-browser. They also implemented support for the latest hot technologies like various Javascript and CSS pre-processors. They are also working on a convenience GUI app for managing watched directories.

#### XRefresh retired

As you can see from [the changelog](http://xrefresh.binaryage.com/#changelog), I started XRefresh in 2007. It was in times when I was doing a lot of web development. Maybe you remember it was the time when Firefox with Firebug was ruling the web developers' world. In 2008 as a fresh web developer I flocked with Ruby on Rails kids and switched from Windows to Mac. I didn't want to lose XRefresh so I implemented a simple command-line XRefresh server in Ruby. But since then Chrome and Safari popularity has risen greatly. What I see today is that many developers are switching from Firebug to Web Developer Tools in Safari/Chrome and XRefresh popularity is fading out. LiveReload actually started as an XRefresh alternative for Safari users and served those users pretty well. Today it supports Firefox as well, so switching should be a no-brainer.

#### Long live the LiveReload

Originally I had a plan to commercialize some future XRefresh version because I strongly believe it brings a great value to developers and I've put quite some effort into packaging it into a usable product. But I had more ambitions. Two years ago I wrote an article about [my future vision for XRefresh](/xrefresh-future-direction).

But my path was different. The success with TotalFinder determined that I'm doing more of a Mac development these days than I'm doing a web development. And I don't have time and motivation to maintain XRefresh when I'm not using it on a daily basis. TotalFinder deserves more of my dedication.

So I'm happy to redirect XRefresh users to LiveReload. I'm sure they will be in good hands :-)