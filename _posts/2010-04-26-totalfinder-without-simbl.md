---
layout: post
title: TotalFinder now works without SIMBL
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/base/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.8.3 does not rely on SIMBL anymore. It plugs into Finder.app on its own.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.8.3.dmg"><img src="{{site.url}}/base/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.8.3.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### TotalFinder loves SIMBL, but SIMBL scares people on the streets

[SIMBL](http://www.culater.net/software/SIMBL/SIMBL.php) is a great and well maintained software. All kudos to **Mike Solomon** who has been doing an awesome job on it for so many years.  TotalFinder probably would not be here today without SIMBL.

The current version of SIMBL has one fundamental problem related to TotalFinder. **It requires people to do something.** Running an installer is not much work, I know. But there is still a dependency. A user needs to install a separate program prior to TotalFinder. They have to keep it up-to-date. They will probably want to look at it and understand what it is. And let's be honest, the [SIMBL homepage](http://www.culater.net/software/SIMBL/SIMBL.php) is not very welcoming to non-programmers.

There are also some technical questions. Is it really worth it to replace SIMBL with my own homebrew solution?

<img class="clear blog-image" src="{{site.url}}/images/simbl-replacement-questioning.png" title="Good question, Shane. It is worth it to make my own SIMBL?">

Good question, Shane. Here are my reasons:

  - I want TotalFinder installation and uninstallation to be as seamless as possible. It should be ideally one-click experience. No brainer!
  - I don't want to depend on a component which may evolve. Testing compatibility and keeping up with Finder.app alone is quite enough work for me.
  - To sleep well at night I wanted to implement a [future compatibility check](http://github.com/darwin/simbl/commit/c95557a49b52aa6a26a5390e30e90364b17b38e1) for Finder
  - I don't really need SIMBL's Agent functionality. Actually it does no good with Finder's auto-restart and it has complicated my life in the past (I needed to [prevent a continuous crashing scenario](http://blog.binaryage.com/totalfinder-with-sparkle/), for example)

So I decided to roll my own solution. It does not need Agent and it is Snow Leopard only, so it turned out to be really easy (the [plugin injector](http://github.com/binaryage/totalfinder-osax/blob/master/TotalFinderInjector.m) has less than 100LOC). I was able to implement a future Finder version check like this:

<img class="clear blog-image-border" src="{{site.url}}/images/totalfinder-future-compatibility-check.png" title="TotalFinder warns you when running with an unknown Finder version (from the future)">

Ok, to wrap it up. TotalFinder.bundle is still a SIMBL plugin and you can run it with SIMBL if you want to play with `Info.plist`. But I'm using my own OSAX to do the Finder injection by default. Don't worry, I will open-source my solution in a few days [on GitHub](http://github.com/binaryage/totalfinder-osax). Of course I will be glad to get some feedback/code reviews on this. 

And as a side-effect I've learned how to rule the world with my own Scripting Additions. Wait for the next release .-)

#### A general project refactoring and Echelon rename

Echelon scares people too. So I decided to rename it simply to TotalFinder.kext. This way when you happen to look into `/System/Library/Extensions` you won't scare yourself to death by forgetting Echelon is simply something related to the peace-loving TotalFinder.

And by the way, if you are still scared please note that TotalFinder.kext is going to be also an open-source in a few days [on GitHub](http://github.com/binaryage/totalfinder-kext). You can then compile it on your own in case you want to be 100% sure about the kernel extensions on your system. I understand the geek inside of you, so in the future I will write a separate technical article about how it works :-)

This was also good excuse to refactor the whole XCode project into several smaller projects, solve dependencies, improve build scripts and clean things up. Unfortunately I cannot present any visible progress here, but I personally feel much better now. You know I hate [cruft](http://en.wikipedia.org/wiki/Cruft), especially in my own baby projects.

Oh, maybe I should have added that the installer's footprint is 3.4MB now, which is ~30% less than the previous 4.8MB. Yeah, faster downloads for you and cheaper S3 bills for me :-)

#### Want new windows always as tabs?

Folks using the OSX Spaces feature [were asking](http://getsatisfaction.com/binaryage/topics/desktop_folders_open_as_tabs_spaces_and_generic_problem) for better handling of new Finder windows. 

By default TotalFinder turns new popping Finder windows into tabs of the last active TotalFinder window. This caused problems in the case of having the TotalFinder window on a different space. Let's say the TotalFinder window is on space1, the user is working on space2 and for example clicks on the desktop to open a new folder. This would trigger a switch back to space1 because the newly created Finder window converts to a tab, and that activates TotalFinder window living on space1. I personally don't use spaces, but I understand that this is annoying.

From 0.8.3 onwards, you can go to TotalFinder/Tweaks preferences panel and check in "Don't adopt new Finder windows as tabs". This will enable you to open new Finder windows in separate TotalFinder windows. In the future I want to improve this behavior to also deal nicely with DMG files and other special types of Finder windows. This option might become the default in the future releases. Any ideas? [Tell me what do you think](http://getsatisfaction.com/binaryage/topics/desktop_folders_open_as_tabs_spaces_and_generic_problem).</a>.

**Good stuff is coming. Stay tuned as usual!**