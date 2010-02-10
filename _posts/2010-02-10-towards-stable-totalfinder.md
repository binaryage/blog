---
layout: post
title: Towards stable TotalFinder
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

TotalFinder 0.7.1 update is ready for download.

#### **[http://downloads.binaryage.com/TotalFinder-0.7.1.dmg](http://downloads.binaryage.com/TotalFinder-0.7.1.dmg)**

**Warning:** When updating via Sparkle, the Finder usually gets into strange state and you are not able quit apps in the Dock. They stay as zombies there and you cannot even Force Quit them. Please restart the Finder again and the problem goes away. You may use new restart option in the status menu item.

---

#### As usual, the changelog is here

[http://totalfinder.binaryage.com/changelog.html](http://totalfinder.binaryage.com/changelog.html)

#### Fixed tab animation quirks

Opening and closing tab animations were jumpy. I've revisited the code and made sure they are going smooth again.

#### Fixed display quirks

Fixed some display quirks related to showing/hiding toolbar, statusbar and sidebar.

#### Fixed Visor mode

Visor mode users should be happy with this release. I've paid special attention to make this feature working again. The best part is that from now it correctly respects the Dock.

#### Fixed some crashes

Thank you all who sent me some crash reports. I really read them.

I've solved @DSStore, @RestoreFocus, @placeWindow and @AEOverride crashes in 0.7.1. As you can see, this should reduce crash rate by 90% or so.

<a href="/images/crash-distribution.png"><img src="/images/crash-distribution.png" width="700"></a>