---
layout: post
title: Towards stable TotalFinder
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/base/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.7.1 update is ready for download.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.7.1.dmg"><img src="{{site.url}}/base/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.7.1.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

**Warning:** When updating via Sparkle, Finder usually gets into a strange state and you are not able quit apps in the Dock. They stay as zombies there and you cannot even Force Quit them. Please restart the Finder again and the problem goes away. You can use the new restart option in the status menu item.

#### Fixed tab animation quirks

Opening and closing tab animations were jumpy. I've revisited the code and made sure they are going smooth again.

#### Fixed display quirks

Fixed some display quirks related to showing/hiding toolbar, statusbar and sidebar.

#### Fixed Visor mode

Visor mode users should be happy with this release. I've paid special attention to make this feature working again. The best part is that from now it correctly respects the Dock.

#### Fixed some crashes

Thank you all who sent me some crash reports. I really read them.

I've solved @DSStore, @RestoreFocus, @placeWindow and @AEOverride crashes in 0.7.1. As you can see, this should reduce crash rate by 90% or so.

<img class="blog-image-full-border" src="{{site.url}}/images/crash-distribution.png" title="The distribution of crash reports">