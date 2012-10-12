---
layout: post
title: TotalFinder with dual mode!
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/base/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.7 is finally out! Grab it while it's hot.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.7.dmg"><img src="{{site.url}}/base/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.7.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

---

#### Introducing dual-pane mode

You may activate dual panels by **double-clicking tab** or pressing **CMD+U**. It simply glues the currently selected tab with the next one (or the previous one). Clicking again makes them separate again. Easy and unobtrusive!

<img class="blog-image-full-border" src="{{site.url}}/images/totalfinder-dual-pane-mode.png" title="Dual mode applied to two left-most tabs">

As you can see I've decided to use the power of tabs to implement this feature. This way you may organize your dual-tabs with the same ease as dealing with ordinary tabs. I've already been using it for few days and I'm really happy with this solution. We just need to agree on some keyboard shortcuts for copying/moving files between panels.

I've also decided not to spawn new finder tabs in case there is no suitable tab for dual mode. In this case it just does nothing. I'm open to your suggestions how this should work in the future. I personally think opening new tabs is quite a heavy-weight operation and should only be done explicitly.

#### My path was not that straight

This hacking is more like archeology than anything else. One thing is reverse-engineering Finder and understanding how it works internally, but that is not enough. To build something reliable on top of it I usually need to try different approaches and pick symbiotic ones which may survive in the real world.

Maybe you remember my early screenshot of dual pane prototype back from October. I've used there the technique of [relocating NSViews from hidden Finder window](http://blog.binaryage.com/totalfinder-with-tabs) for right-side list view. The solution was very fragile and unstable. I've never managed to make it fully working. I would probably need to pull much more of my hair out to get it into good shape. I'm really glad I've followed the tabs-path instead.

<img class="blog-image-full" src="{{site.url}}/images/totalfinder-old-dual-approach.png" title="The original dual mode approach">

#### Custom crash reporting

You will get a chance to upload crash report as a gist and send me an email. Hope you will never have to see this dialog :-)

<img class="blog-image" src="{{site.url}}/images/new-crash-report-dialog.png" width="400" title="The crash reporting dialog">

#### Locked dock? "killall Finder" for rescue 

Sometimes TotalFinder locks Finder and other apps. The symptom is that other apps are not able to quit (even Force Quit) and just stay in the Dock in zombie state. It happens usually shortly after re-installation. 

If this happens, please kill Finder and start from scratch by typing this in Terminal.app:

`killall Finder`

I have to catch this annoyance. I'll probably replace the whole installer with custom script. This way I'll know exactly what installer does instead of relying on Apple's magic. Btw, right now it is not possible to downgrade TotalFinder directly. The installer just won't replace it in case of going to lower version number. You have to manually uninstall using Uninstall.scpt and then install older version.

#### What's next?

At this moment my roadmap looks like this:

* Continue fixing quirks and improve stability
* Add drag-and-drop tabs, cut and paste, and keyboard shortcuts for sidebar items for v0.8
* Terminal.app co-operation for v0.9, open beta period?
* Hacking NASA satellites? ;)

These features should be much easier compared to tabs and dual-pane mode. I'm optimistic. Stay tuned!