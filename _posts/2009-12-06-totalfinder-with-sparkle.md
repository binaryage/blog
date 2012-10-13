---
layout: post
title: TotalFinder with Sparkle (v0.3)
tags: [totalfinder, testing]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**I have made some progress on [TotalFinder](http://totalfinder.binaryage.com) during the weekend. This is mostly a maintenance release.** 

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.3.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.3.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

I wanted to make stable install/uninstall experience and fix bugs reported by early adopters. Thank you guys! I've added a new feature of updating TotalFinder via [Sparkle](http://sparkle.andymatuschak.org). It was really easy to integrate. Kudos Andy!

#### ALPHA v0.3 changes

<ul class="changes">
    <li><b>NEW:</b> Sparkle updating system. </li>
    <li><b>NEW:</b> Added red face preventing continuous crashing during startup (because Finder is being restarted after crash by launchd).</li>
    <li><b>NEW:</b> Added uninstall script. </li>
    <li><b>FIXED:</b> Changed TotalFinder window level so that auxiliary floating windows are visible on top of it (<a href="http://getsatisfaction.com/binaryage/topics/deactivate_always_on_top_window">more info</a>).</li>
    <li><b>FIXED:</b> Fixed Echelon registration into startup items. Previously Echelon wasn't started again after restart.</li>
    <li><b>FIXED:</b> Desktop icons should persist during Finder restarts. I'm restoring important .DS_Store files to original locations during restart.</li>
</ul>

#### Unhappy red face

The Finder is being automatically restarted after a crash by the launchd process. This is usually a good thing. The user is not confused that her Finder is missing.

<img class="blog-image" src="{{site.url}}/images/sad-red-face.png" style="float: left; margin-right: 20px" title="Sad red face in status menu area">

The problem with TotalFinder is that it may be unstable and crash on some machines during Finder startup. This would lead to infinite cycle of restarts and crashes. I've implemented sad red face, which appears as menu item if Finder crashes during the first ten seconds after launch. If you feel lucky, you may try to re-launch it again. Anyway, don't forget to "send me":mailto:antonin@hildebrand.cz your crash report.

#### Persistent desktop settings

In v0.2.1 you might lose your desktop icons positions and other settings during system restart. This applies only when in .DS_Store redirect mode.

I did investigation of what is happening during system launch. The problem was that TotalFinder is not injected into Finder.app immediately but with some delay.  In this time period Finder looks for .DS_Store on desktop, but there is no such a file, because it was redirected last time when TotalFinder was live. So Finder creates brand new .DS_Store on desktop and resets settings to defaults.

My solution to this problem is to copy important .DS_Store files back to original places when TotalFinder is about to be terminated. This works pretty reliably. Right now I'm restoring .DS_Store on user's desktop and in user's home folder. This seems to be working fine for me. Let me know if there is another important .DS_Store file which should be restored during Finder restart.

#### Towards stable TotalFinder

My goal for next week is to make TotalFinder really stable. Do some refactoring and lay out good foundation for next big feature: dual-panel mode. I know this will be hard to implement, but I'm still quite optimistic.

Thank for your time testing v0.3.