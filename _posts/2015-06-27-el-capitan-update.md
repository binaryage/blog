---
layout: post
title: "Update on System Integrity Protection in El Capitan, OSX 10.11"
tags: [totalfinder, totalspaces]
author_name: Stephen Sykes
author_uri: http://about.me/sdsykes
---
<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/><img src="/shared/img/icons/totalspaces2-128.png" class="intro-icon"/>

** TotalFinder and TotalSpaces2 will not run on El Capitan in its default configuration. **

In our [previous post](http://blog.binaryage.com/on-el-capitan/) we explained that the new security features of the forthcoming release of OSX may affect our apps.

#### The end of system modifications and tweaks

Both TotalFinder and TotalSpaces2 work by injecting code into processes that are part of OSX. They change the way those processes work, but they don't change the underlying system - they just add features whilst they are running. If you quit TotalFinder or TotalSpaces2, those processes restart and system returns to its original state.

However, in El Capitan OSX 10.11, this kind of modification will be disallowed by a new feature called "System Integrity Protection". It is also known as "Rootless". The feature prevents both modifications to your system files, and to system processes whilst they are running (even if you enter your password for administrator access).

So in a normally configured Mac, TotalFinder and TotalSpaces2 cannot run.

#### BinaryAge apps

In light of this, **it's clear that TotalFinder and TotalSpaces2 will cease to be consumer products**. But they will continue to work as normal on OSX 10.9 and 10.10, so users who do not upgrade to 10.11 can continue to use them.

**We are announcing a 50% discount on the price of both TotalFinder and TotalSpaces2 from today in recognition of the situation.**

We have not yet decided how we will proceed once OSX 10.11 is released.

#### The silver lining

You can actually turn System Integrity Protection off. To do so, you must reboot into recovery mode (it is not meant as an operation a regular user would do).

Understandably, we do not feel we can ask our users to do that (it must be your own decision) as it affects all the new protections.

We do feel that it would have been possible for Apple to allow developer signed code to be injected, or have a more fine grained permission system, but as things stand the feature is either on or off at a global level.

#### TotalFinder on El Capitan

With System Integrity Protection turned off, the latest build of TotalFinder works with some features missing in the current beta El Capitan. It will require some effort to re-write the missing features (for example colored labels, and folders on top). **We are not currently intending to do a full port for El Capitan.**

#### TotalSpaces2 on El Capitan

With System Integrity Protection turned off, the latest build of TotalSpaces2 works well on the current beta of El Capitan. **We intend to continue to support TotalSpaces2 if possible on El Capitan for those that wish to run it.**

#### Turning off System Integrity Protection

If you choose to change the System Integrity Protection setting, this feature is turned on or off by rebooting into recovery mode (hold CMD and R when rebooting), and then choosing Utilities -> Security Configuration and unchecking the Enforce System Integrity Protection checkbox.

<img class="clear blog-image" src="/images/recovery-mode.png" title="Recovery mode">
<img class="clear blog-image" src="/images/security-configuration.png" title="Security configuration">

#### Discussion

While we are disappointed, we aren't defeated - we will find other projects, and there may be more apps BinaryAge in the future.

For download links for the latest betas, and further discussion see the posts in our forum for [TotalFinder](http://discuss.binaryage.com/t/totalfinder-status-under-os-x-10-11-el-capitan/3858) and [TotalSpaces2](http://discuss.binaryage.com/t/totalspaces2-status-under-os-x-10-11-el-capitan/3828).

<strike>Finally, note that [TotalTerminal](http://totalterminal.binaryage.com) is not currently affected by System Integrity Protection.</strike>
