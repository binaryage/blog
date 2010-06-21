---
layout: post
title: TotalFinder plays nice with TimeMachine
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.8.2 is another stability release. Just fixing bloody bugs.<br/>We need to get solid base for new exciting features, agreed?**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.8.2.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.8.2.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### TotalFinder and TimeMachine 

TotalFinder is now aware of TimeMachine. This is quite tricky. You know, when entering TimeMachine, the active Finder window is animated and floats into the center of the screen for TimeMachine's galaxy view. Finder uses heavy CoreAnimation machinery for this and it broke visually with TotalFinder. 

The worse thing is that Finder creates one extra "working window" to render stacked windows behind the main window (did you know those are clones?). This working window is disposed after returning from TimeMachine. Anyway, this windows juggling was so confusing for TotalFinder that it crashed usually immediately after returning from TimeMachine or when user tried to switch tabs. To make TotalFinder windows look nice in TimeMachine I needed to teach Finder windows how to switch from TotalFinder's tab style into original frame style and back. Right now it is used just for TimeMachine session, but it is a good foundation for future arbitrary switching Finder windows between classic and tab style.

Why? Some people want to be able to open classic Finder windows for some tasks while still having TotalFinder operating the rest of windows. We will see. I'm still considering it. But I don't want to make this too complicated.

#### Vaporized a monster memory leak

Honestly I didn't have much time to hunt for memory leaks. Crashes have higher priority right now. But there was one really huge <a href="http://getsatisfaction.com/binaryage/topics/memory_leak_upon_hiding">memory leak in the 0.8 release</a>. Thanks for reporting, Adam! 

Now I understand why have some people complained about TotalFinder slowing down their systems. I expect them to be Visor-feature users. Also I did a brief instrumentation using XCode's memory tools. After a short TotalFinder usage session all looked ok to me. Memory seemed to be returned to the system as expected. I haven't noticed any major memory leaks. Report to me if you see anything unusual. And don't forget: the Activity Monitor is your friend.

#### And more improvements

Drag &amp; Drop respects system settings for springing delay. Also TotalFinder goes mainstream and as you can imagine some people get shocked when exposed to a raw applescript. This renders them unable to click green "run" button and uninstall TotalFinder properly. And that is why we have a new uninstaller app which wraps this into a few straightforward clicks. No more sad faces.

**I hope this is a good release. Enjoy it and look forward for the next release 0.9 which should finally include some new features.**