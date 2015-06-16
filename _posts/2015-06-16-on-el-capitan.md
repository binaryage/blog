---
layout: post
title: "On System Integrity Protection in El Capitan, OSX 10.11"
tags: [totalfinder, totalspaces]
author_name: Stephen Sykes
author_uri: http://about.me/sdsykes
---
<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/><img src="/shared/img/icons/totalspaces2-128.png" class="intro-icon"/>

** There is a significant risk that TotalFinder and TotalSpaces2 will not run on El Capitan. **

#### System Integrity Protection

##### The bad news

In the WWDC keynote last week Apple announced a feature called __System Integrity Protection__ for OSX 10.11. This feature protects the system software against modification both on disk, and in memory.

Both TotalFinder and TotalSpaces2 work by injecting code into running system apps (Finder.app in the case of TotalFinder, and Dock.app in the case of TotalSpaces2). If Apple follow through with this measure, it is __game over__ for these apps as consumer products. They simply won't be able to run on your computer.

For us, and our many users this would be a great disappointment. But Apple's goal is for greater system integrity, and that means blocking all modifications, whether from good and bad actors. We cannot blame them, but we wish there were some way of keeping our apps working, whether through new APIs or some additional verification, or whatever.

##### The good news

Firstly, the latest betas of both TotalFinder and TotalSpaces2 can be run on the first beta of OSX 10.11 El Capitan. They are not, at least for now, blocked.

Secondly, there will be a way to turn off System Integrity Protection. This possibility is aimed at developers. It involves booting your machine into recovery mode, and changing the setting there. Clearly it's designed to not be something you would normally do, and we could not reasonably ask customers to turn off security protections. But if the worst comes to pass, you will likely be able to run our apps using this method. We will try to support those of you who wish to do this.

#### The bottom line

While the situation is unclear at the moment, __there is a strong possibility that neither TotalFinder or TotalSpaces2 will work on a normally configured Mac running OSX 10.11 El Capitan__. We think it's fair to warn you now.
