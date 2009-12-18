---
layout: post
title: TotalFinder polishing
tags: [totalfinder, releases]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/totalfinder-logo.png" width="80" style="float: left; margin-right: 20px"> 

This is just maintenance release of [TotalFinder](http://totalfinder.binaryage.com). Christmas time is busy and I really didn't manage to save few evenings to dig deeper into Finder internals.
Next expiration is set to January 11, 2010 and this gives me some time to work on dual-panel browser during holidays.

### [https://dl.getdropbox.com/u/559047/tf/TotalFinder-0.5.dmg](https://dl.getdropbox.com/u/559047/tf/TotalFinder-0.5.dmg)

#### ALPHA v0.5 changes

<ul class="changes">
    <li><b>NEW:</b> Added tweak option "Don't customize Dock Icon".</li>
    <li><b>NEW:</b> Installer displays warning if SIMBL is not detected.</li>
    <li><b>NEW:</b> Archive contains compatible SIMBL package (for case TotalFinder.dmg is found on Planet of the Apes).</li>
    <li><b>FIXED:</b> Quick TotalFinder restart from Preferences Pane is not counted as a crash.</li>
    <li><b>FIXED:</b> Using latest Sparkle which supports asynchronous package installation. This fixes installer choking when updating via Sparkle's "Install and Relaunch" button.</li>
</ul>

#### TotalFinder is pretty stable

I'm using TotalFinder for more than month and I have no crash-related issues so far. Even system restarting is peaceful (since version 0.3).
There are maybe some window activation issues. For example when you do CMD+TAB, TotalFinder's main window should slide up in my opinion. 
Or when some app wants to open folder in Finder, it should not open brand new window, but reuse TotalFinder 
and slide up instead. But these are details I will work out during next month(s).

#### Tabs would be great

Do you remember tabs in a title bar from Safari 4 beta?

<img src="/images/safari-beta-tabs.jpg"> 

I know it is against usability, but Visor and TotalFinder are special case apps. These are system-wide windows sliding from "nowhere". 
So they couldn't be treated as apps following usability guidelines anyway. 
I like the idea of tabs in the title bar because it does not interfere with existing
Finder UI, I'm concerned especially about the toolbar of course. Also it is perfect fit for TotalFinder sliding from bottom.

I'm looking for some open source implementation of Cocoa app tweaking title bar section of the main window. 
Haven't found any implementation with safari-like tabs. 
But I'm going to look at Chromium project. Mac version of Chrome browser has nice tabs and does some kind of custom window titlebar rendering.

---

Please test v0.5 and better don't use Sparkle "Install and Relaunch" button, that should be fixed from 0.5 up.