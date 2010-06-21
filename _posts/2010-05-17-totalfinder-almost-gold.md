---
layout: post
title: TotalFinder almost gold
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.9.1 is out with many improvements and some stability fixes.<br/>Maybe I should start calling it a beta?! What do you think? :-)**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.1.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.1.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### The major feature: "no major features"

I have still head full of crazy ideas about new exciting features for TotalFinder but I decided to stay calm and polish TotalFinder in its current state. 
Don't worry I'm also evaluating your ideas from <a href="http://getsatisfaction.com/binaryage">http://getsatisfaction.com/binaryage</a>.

The one thing is clear to me. TotalFinder must not turn into a bloat-ware. On the other side the TotalFinder is by definition a product for Mac tweakers who love to have options. I want to support separate orthogonal features which should be disabled by default and which may be enabled at will on separate preference panels. So everyone gets easy way how to use only subset of TotalFinder features. 

For example not that many people is interested in .DS_Store redirection while for some it is an essential feature. By the way I renamed this feature to "Asepsis" which is kind of cool name for real system surgeons ;-)

<img class="clear blog-image" width="300" src="{{site.url}}/images/new-preferences-panel.png" title="TotalFinder provides distinct features which may be enabled at once">

This is the new look of TotalFinder preferences. New mini tab buttons give room for new feature panels in the future :-)

#### Fixed several crash situations

The root of all evil was my extensive usage of performSelector:withObject:afterDelay: calls to make things smooth and sane. This was used for example when animating tabs. The problem is that target object with scheduled method call does not go away until the timer fires (performSelector calls retain on target). Cocoa system uses autorelease which does deallocation at some point in the future after the timer fired. The problem were weak references the target has to other objects. These objects may die in the meantime when the target is waiting for animation to finish.

As you can imagine this was the source of all sudden crashes when dealing with tabs. For example 100% repro case for one tabs related crash was:

- open window with two tabs
- with mouse click on close button of the second tab to initiate a tab closing animation
- use CMD+Q to close the whole browser window (you may be fast and close it with mouse or pressing CMD+W to close second tab quickly after first one)

I believe I've solved all these nasty issues by reviewing all performSelector calls and fixing object dependencies.

#### Visor window can be pinned and resized by dragging

I've replaced Visor close button with pin button. Visor Window may be also pinned by pressing `CMD+SHIFT+P` keyboard shortcut. You may also drag tabs bar to resize Visor vertically. Sweet!

<img class="clear blog-image-border" src="{{site.url}}/images/totalfinder-pinned-visor-window.png" title="Visor Window may be pinned by pressing CMD+SHIFT+P keyboard shortcut">

I've also improved free-form mode of Visor window and implemented seamless switching between these modes.

#### Narrow Tabs Bar for small screens

This is just a cherry. It was easy enough so I decided to make some folks with small screens happy. You have keyboard shortcut for this too `CMD+SHIFT+B`.

<img class="clear blog-image-border" src="{{site.url}}/images/totalfinder-narrow-tabs-bar.png" title="Narrow Tabs Bar">

#### Display hidden files without restarting Finder!

This one was really hard one. As I <a href="http://blog.binaryage.com/i-can-haz-folders-on-top">wrote before</a>, there is no simple way how to force Finder to display hidden files programatically. You may tweak AppleShowAllFiles key in Finder's plist, but it requires Finder restart to take effect.

So I've followed the hard path again. I've searched memory where Finder stores the bit which tells the file browser how to filter the files when rendering. As you would expect this memory offset differs for each hardware platform and Finder version. So I ended up with two table where I store known memory offsets for both i386 and x86_64 platforms.

As of 0.9.1 release. This feature works for Finder 10.6.3 and 10.6.4. The Apple is probably going to release Finder 10.6.5 soon, so I will release TotalFinder update for it shortly. If you encounter future compatibility warning you are going to lose this functionality for a while (Finder restart will work always of course).

<img class="clear blog-image-border" width="300" src="{{site.url}}/images/totalfinder-future-compatibility-check.png" title="TotalFinder warns you when running with unknown Finder version (from future)">

Note: Finder's minor version number is advanced by +1 in comparison to OS X system updates numbering.


#### What's next?

This is pretty much what you are going to get in 1.0 release. You should be already saving your 15 bucks as a reward for my hard work.

I plan the following features for 1.0:

* Pixel perfection (right now tab gradients visually mismatch the Finder windows)
* Localization support
* Registration (a funny box for pasting a license key)
* Small usability fixes

**I'm pretty excited how TotalFinder matures. Let me know what are yours must-haves for the 1.0 release.**