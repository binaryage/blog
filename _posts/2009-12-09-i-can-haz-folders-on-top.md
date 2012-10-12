---
layout: post
title: I can haz folders on top
tags: [totalfinder, testing]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/base/img/icons/totalfinder-64.png" class="intro-icon"/>

**Yes, the new version of [TotalFinder](http://totalfinder.binaryage.com) supports <a href="http://getsatisfaction.com/binaryage/topics/show_folders_always_on_top">Folders on Top feature</a>.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.4.dmg"><img src="{{site.url}}/base/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.4.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### Folders on Top

Go to Tweaks section in TotalFinder preferences.

<img class="blog-image" src="{{site.url}}/images/folders-on-top.png" style="float: left; margin-right: 20px" title="'Folders on Top' preferences"> 

#### Toggling hidden files

Right now you have to restart Finder to make "Show Hidden Files" toggle effective. This is annoying, especially because I want to make this toggle available on a keyboard shortcut in the future.

Unfortunately the Finder.app author reads related plist settings in the beginning after program launches and stores the value in-memory. Unfortunately the method for reloading this toggle is not exposed. I was at least able to detect the exact position in-memory for the current version and successfully refresh the browser view, but this would be very fragile solution. The problem is that this may change for every binary and any Finder update could break it. I'm looking for better solution. Ideas?

#### Sparkle experience

Installing update via Sparkle has one problem. I expect Finder to quit during install. But this is not the case when you run installer via Sparkle update screen. Sparkle keeps Finder alive and relaunches it after installer finish. Need to find some solution to initiate the installer "from outside" and let Finder quit gracefuly before install.