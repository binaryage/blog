---
layout: post
title: "SIP and installing BinaryAge apps"
tags: [totalfinder, totalspaces]
author_name: Stephen Sykes
author_uri: mailto:stephen@binaryage.com
---
<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/><img src="/shared/img/icons/totalspaces2-128.png" class="intro-icon"/>

#### From El Capitan to here

In 2015 we realised that System Integrity Protection would stop TotalFinder and TotalSpaces2 working on normally configured Macs. At the time, we felt that this would mean the end of those products as general consumer products.

However, it is clear that although we don't see the sales we used to have, there is still strong support for these products. There remains a market for tools that improve the workflow and usability of your system.

#### A chink of light

One request we often hear is to allow TotalFinder and TotalSpaces2 to be installed so that they can run with System Integrity Protection (SIP) turned on. And in fact we discobered that this is possibe - we have earlier advised anyone who asked to go through a complex process to install our plugin component in a special system location so that the apps could run on a normally configured Mac.

Having realised we could do this, we wanted to give this option to everyone. We have made it simpler, and in fact, from now on it will be the default method of installation.

#### TotalFinder and TotalSpaces2 with SIP turned on

The installtion process for our apps will be as follows:

1. Reboot into recovery mode (hold cmd-R during reboot).
2. Go to utilities->terminal, type csrutil disable, and reboot.
3. Install TotalSpaces2 and/or TotalFinder and run the app(s),
4. (Optional) Reboot into recovery mode (hold cmd-R during reboot).
5. (Optional) Go to utilities->terminal, type csrutil enable, and reboot.

So before installing our apps, turn SIP off, Then once the apps are installed you are free to turn SIP back on.

This new installtion method is supported from TotalFinder v1.x.x and TotalSpaces2 v2.5.4.

If you are upgrading from a previous version, everything will continue to work normally. But in order to turn SIP fully on, you must go through the above process.

#### Technical details

Both TotalFinder and TotalSpaces2 have a plugin component that lives in /Library/ScriptingAdditions. As a normal user you can allow writing that component there if you allow adminstrator access.

However, plugins in that location cannot be loaded by OSX/MacOS with System Integrity Protection fully turned on.

It turns out there is another location, /System/Library/ScriptingAdditions from where the system *will* load plugins even with SIP turned on. However, SIP must be turned off in order to be able to write the plugin there in the first place.

We are changing to using this system location as our primary pluign location. So, for installtion, turn SIP off, install and run the apps, then you may freely turn SIP back on.

#### Risks

Apple "own" the system locations in your file system, and it is entirely possible that they could remove our plugin components during a software update. If this happens, you would need to turn SIP off again in order for the plugin to be re-installed. We don't think this will happen, but you never know.

If we have to update our plugin component, this would also require SIP changes, but we are aiming to keep the component stable across many releases.

#### Final words

Both TotalFinder and TotalSpaces2 have a number of other improvements in this release, so it should be worth upgrading. We are pushing the new binaries out to our pre-release testers today, and to all users if everything seems fine. Let us know if you have any problems!

[Discuss]: http://discuss.binaryage.com/
[TotalFinder]: http://totalfinder.binaryage.com
[TotalSpaces]: http://totalspaces.binaryage.com
