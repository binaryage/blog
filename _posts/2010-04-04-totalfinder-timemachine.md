---
layout: post
title: TotalFinder plays nice with TimeMachine
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.8.2 is another stability release. Just fixing bloody bugs.<br/>We need to get solid base for new exciting features, agreed?**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.8.2.dmg"><img src="/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.8.2.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### TotalFinder and TimeMachine 

TotalFinder is now aware of TimeMachine. This was quite tricky. You know, when entering TimeMachine, the active Finder window is animated and floats into the center of the screen for TimeMachine's galaxy view. Finder uses heavy CoreAnimation machinery for this and it broke visually with TotalFinder. 

The worst thing is that Finder creates an extra "working window" to render the stacked windows behind the main window (did you know these are clones?). This working window is disposed of after returning from TimeMachine. Anyway, this window-juggling was so confusing for TotalFinder that it usually crashed immediately after returning from TimeMachine or when the user tried to switch tabs. To make TotalFinder windows play nice in TimeMachine, I needed to teach Finder windows how to switch from TotalFinder's tab-style into the original frame-style and back. Right now, it is used only for the TimeMachine session, but it is a good foundation for future arbitrary switching of Finder windows between the classic and tab styles.

Why? Some people want to be able to open classic Finder windows for some tasks while still having TotalFinder operate the rest of the windows. We will see. I'm still considering it. But I don't want to make this too complicated.

#### Vaporized a monster memory leak

Honestly I don't have much time to hunt for memory leaks. Crashes have higher priority right now. But there was one really huge <a href="http://getsatisfaction.com/binaryage/topics/memory_leak_upon_hiding">memory leak in the 0.8 release</a>. Thanks for reporting it, Adam! 

Now I understand why have some people complained about TotalFinder slowing down their systems. I expect them to be Visor-feature users. Also, I did a brief investigation using XCode's memory tools. After a short TotalFinder session everything looked ok to me. Memory seemed to be returned to the system as expected. I haven't noticed any major memory leaks. Report to me if you see anything unusual. And don't forget: the Activity Monitor is your friend.

#### And more improvements

Drag &amp; Drop respects system settings for springing delay. Also, TotalFinder goes mainstream, and as you can imagine some people get shocked when they're exposed to a raw applescript. This renders them unable to click the green "run" button to uninstall TotalFinder properly. And that is why we have a new uninstaller app which wraps this into a few straightforward clicks. No more sad faces.

**I hope this is a good release. Enjoy it and look forward for the next release 0.9 which should finally include some new features.**