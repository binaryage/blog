---
layout: post
title: "The future of TotalFinder and TotalSpaces"
tags: [totalfinder, totalspaces]
author_name: Stephen
author_uri: mailto:stephen@binaryage.com
---
<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/><img src="/shared/img/icons/totalspaces2-128.png" class="intro-icon"/>

#### From Snow Leopard to Big Sur

An early version of TotalFinder was first released in November 2009 during the golden days of Snow Leopard. Although many still remember that operating system with fondness, the Finder implementation of the time was ripe for improvement. We think that TotalFinder was able to really make a difference in the usability of Finder, and we found there was a great deal of support for it.

In April 2012 we released TotalSpaces for OSX Lion, since the grid spaces functionality that we absolutely loved was removed by Apple after the Snow Leopard release. We were able to replace that functionality, and add some configurability and improvements of our own.

As time went by, we continued to develop these products and support them. Amazingly, TotalFinder has been available for over 11 years, and TotalSpaces for almost 9 years.

Over the years Apple has erected many obstacles, the most important of which was their "rootless" implementation, System Integrity Protection. This prevented modification of the system software, and had to be turned off for the installation or running of our products. Turning SIP off was uncomfortable to do (requiring two reboots), and uncomfortable for us to recommend.

Also notable was that Apple to some extent "Sherlocked" TotalFinder by implementing their own tabs implementation in Finder. We found that some people preferred the TotalFinder tabs, but this did reduce the relevance of TotalFinder to many people.

### What now?

At the end of [this post from 2018](https://blog.binaryage.com/sip-and-mojave/) we noted that TotalFinder and TotalSpaces2 have had a good run, but it is certainly becoming more difficult to support these products. This is due to the additional protections Apple are adding, the changing technology, and more generally the lack of Apple provided APIs to do the kind of system modifications that our customers want.

At that time we promised to support the products during the lifetime of Mojave. As it happened, we did better - we continued to make releases in 2019 and 2020, bringing support to Catalina and now to Big Sur.

However, the support in Big Sur is imperfect, and we are not able to support Apple Silicon macs at all.

So we have to admit that it's the end of the road for TotalFinder and TotalSpaces2. **We will not work on making TotalFinder or TotalSpaces2 work with the next version of MacOS, and they will not be ported to Apple Silicon macs.**

We will continue to provide limited support TotalFinder and TotalSpaces2 until the end of 2021. We will cease selling new licenses in the summer.

It is unlikely we will make these apps open source. Interested persons may want to look at [Yabai](https://github.com/koekeishiya/yabai) which uses some of the same APIs that TotalSpaces2 does (and I believe early on reversed some TotalSpaces2 code - we don't mind!). It also uses a similar code injection mechanism to TotalFinder and TotalSpaces. 

Also Aditya Vaidyam independently discovered some important APIs we use, [documented here](https://avaidyam.github.io).

Finally I'd like to mention and credit that the original reversing of the Core Graphics APIs was [done by Richard J Wareham](https://bitbucket.org/rjw57/desktopmanager/src/master/), and something may still be learned from this code.

### TotalSpaces3

It's not all bad news! For a while now we have been working on a new version of TotalSpaces, TotalSpaces3.
This version will work without modifying the system, and works with SIP enabled. It is a significant challenge to achieve an equivalent experience without the level of access that code injection provided us, but we believe it will be more than usable.

It is intended for Apple Silicon macs only (at this time), and is currently in private alpha testing. We don't have any release timetable set at the moment, but we will make announcements at the appropriate time.

### 11 years of BinaryAge

We like to think that we have achieved much during the lifetime of BinaryAge, including the release of various free utilities as well as our paid apps, we have found ways around all kinds of MacOS technical roadblocks, and we hope we have helped with the productivity of our users.

BinaryAge is not going anywhere. TotalSpaces3 is coming, and we may continue release new products and utilities in the future.

Although these days BinaryAge is a side project for Antonin and I, we hope we can continue to provide good products and service for our customers - and who knows what the future will bring.

Wishing you a safe and prosperous 2021.

Stephen (and Antonin)
