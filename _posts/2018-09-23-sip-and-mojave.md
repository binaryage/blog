---
layout: post
title: "Running TotalFinder and TotalSpaces2 on Mojave"
tags: [totalfinder, totalspaces]
author_name: Stephen Sykes
author_uri: mailto:stephen@binaryage.com
---
<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/><img src="/shared/img/icons/totalspaces2-128.png" class="intro-icon"/>

#### From Sierra and High Sierra to Mojave

In [this post from 2017](https://blog.binaryage.com/sip-and-installing-total-apps/) we talked about how we found a way to run our apps TotalFinder and TotalSpaces2 with System Integrity Protection (SIP) turned on. This was possible because the installation process would install our plugin components in trusted locations whilst SIP was turned off, allowing the user to turn SIP back on again after installation.

Unfortunately, with macOS 10.14 Mojave this is no longer the case - Apple have changed their verification code so that our plugin cannot possibly work with SIP turned on even if it is installed in the trusted locations that worked before.

**This means that in order to run our apps on macOS Mojave you have to keep SIP turned off.**

We know this is disappointing, and that some people will not want to do this.

**Your machine may be less secure when System Integrity Protection is not running. It is entirely your decision to modify or temporarily modify the settings.**

If you want more information about SIP, [see wikipedia](https://en.wikipedia.org/wiki/System_Integrity_Protection). Apple also provided [some information here](https://developer.apple.com/library/archive/documentation/Security/Conceptual/System_Integrity_Protection_Guide/Introduction/Introduction.html).

We provide updated instructions on how to install [TotalFinder here](https://totalfinder.binaryage.com/sip) and [TotalSpaces2 here](https://totalspaces.binaryage.com/installing-mojave).

#### Technical details

In Mojave Apple added additional signature checks for injected code. This means that our plugins won't load unless we can sign them with an Apple certificate, and as we aren't Apple we don't have that certificate. There isn't really any way around this, and we can only tell you how to get around the protection by disabling SIP.

In fact, TotalFinder and TotalSpaces2 can work with only the debug and file system protections turned off, and advanced users may want to use this command in the terminal in recovery mode:

    csrutil enable --without debug --without fs

The system will complain that this is an unsupported configuration though, and we cannot know if a future update will break it.

#### What next?

TotalFinder and TotalSpaces2 have had a good run, but it is certainly becoming more difficult to support these products. This is due to the additional protections Apple are adding, the changing technology (particularly increasing use of Swift which is harder to integrate with than Objective C), and more generally the lack of Apple provided APIs to do the kind of system modifications that our customers want.

We will keep supporting both products for the lifetime of macOS 10.14 Mojave, but there may well be a future release - perhaps 10.15 next year, perhaps later - that we cannot work with at all. But for now, if you wish to run TotalFinder or TotalSpaces2, we will do our best to make things work for you.
