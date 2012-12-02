---
layout: post
title: TotalFinder almost gold
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.9.1 is out with many improvements and some stability fixes.<br/>Maybe I should start calling it a beta?! What do you think? :-)**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.1.dmg"><img src="/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.1.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### The major feature: "no major features"

I still have my head full of crazy ideas about exciting new features for TotalFinder but I decided to stay calm and polish TotalFinder in its current state. 
Don't worry, I'm also evaluating your ideas from <a href="http://getsatisfaction.com/binaryage">http://getsatisfaction.com/binaryage</a>.

One thing is clear to me. TotalFinder must not turn into bloat-ware. On the other side the TotalFinder is by definition a product for Mac tweakers who love to have options. I want to support separate orthogonal features which should be disabled by default and which may be enabled at will on separate preference panels. So everyone gets an easy way to use only a subset of TotalFinder features. 

For example some people are not that interested in .DS_Store redirection, while for others it is an essential feature. By the way, I renamed this feature "Asepsis" which is kind of a cool name for real system surgeons ;-)

<img class="clear blog-image" width="300" src="/images/new-preferences-panel.png" title="TotalFinder provides distinct features which may be enabled at once">

This is the new look of TotalFinder preferences. New mini tab buttons give more room for new feature panels in the future :-)

#### Fixed several crash situations

The root of all evil was my extensive usage of performSelector:withObject:afterDelay: calls to make things smooth and sane. For example, this was used when animating tabs. The problem is that the target object on which the scheduled method is called does not go away until the timer fires (performSelector calls [retain] on target object). Cocoa uses autorelease which does deallocation at some point after the timer has fired. The problem was that the target had weak references to other objects. These objects may die in the meantime while the target is waiting for the animation to finish.

As you can imagine this was the source of all sudden crashes when dealing with tabs. For example a 100% reproducible case for one tabs-related crash was:

- open window with two tabs
- click on close button of the second tab to initiate a tab closing animation
- use CMD+Q to close the whole browser window (if you're fast you can close it with mouse or pressing CMD+W to close second tab quickly after first one)

I believe I've solved all of these nasty issues by reviewing all performSelector calls and fixing object dependencies.

#### Visor window can be pinned and resized by dragging

I've replaced the Visor close button with pin button. The Visor window may be also pinned by pressing the keyboard shortcut `CMD+SHIFT+P`. You can also drag the tabs bar to resize Visor vertically. Sweet!

<img class="clear blog-image-border" src="/images/totalfinder-pinned-visor-window.png" title="The Visor window may be also pinned by pressing the keyboard shortcut `CMD+SHIFT+P`">

I've also improved the free-form mode of the Visor window and implemented seamless switching between these modes.

#### Narrow Tabs Bar for small screens

This is just the cherry on the top. It was easy enough so I decided to make some folks with small screens happy. You have a keyboard shortcut for this too: `CMD+SHIFT+B`.

<img class="clear blog-image-border" src="/images/totalfinder-narrow-tabs-bar.png" title="Narrow Tabs Bar">

#### Display hidden files without restarting Finder!

This was a really hard one. As I <a href="http://blog.binaryage.com/i-can-haz-folders-on-top">wrote before</a>, there is no simple way to programatically force Finder to display hidden files. You can tweak AppleShowAllFiles key in Finder's plist, but it requires Finder to restart to take effect.

So I've followed the hard path again. I've searched the memory where Finder stores the bit which tells the file browser how to filter files when rendering. As you would expect this memory offset differs for each hardware platform and Finder version. So I ended up with two tables where I store known memory offsets for both i386 and x86_64 platforms.

As of the 0.9.1 release, this feature works for Finder 10.6.3 and 10.6.4. Apple is probably going to release Finder 10.6.5 soon, so I will release a TotalFinder update for it shortly. If you encounter the future compatibility warning you will lose this functionality for a while (a Finder restart will always work, of course).

<img class="clear blog-image-border" width="300" src="/images/totalfinder-future-compatibility-check.png" title="TotalFinder warns you when running with unknown Finder version (from the future)">

Note: Finder's minor version number is advanced by +1 compared to the OS X system update numbering.


#### What's next?

This is pretty much what you are going to get in the 1.0 release. You should be already saving your 15 bucks as a reward for my hard work.

I'm planning the following features for 1.0:

* Pixel perfection (right now the tab gradients don't visually match the Finder windows)
* Localization support
* Registration (a funny box for pasting a license key)
* Small usability fixes

**I'm pretty excited about how TotalFinder is maturing. Let me know what your must-haves are for the 1.0 release.**