---
layout: post
title: TotalFinder with dual mode!
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

TotalFinder 0.7 is finally out! Grab it while it is hot.

#### **[http://downloads.binaryage.com/TotalFinder-0.7.dmg](http://downloads.binaryage.com/TotalFinder-0.7.dmg)**

---

#### Introducing dual-pane mode

You may activate dual panels by **double-clicking tab** or pressing **CMD+U**. It simply glues currently selected tab with the next one (or the previous one). Clicking again makes them separate again. Easy and unobtrusive!

<a target="_blank" href="/images/totalfinder-dual-pane-mode.png"><img src="/images/totalfinder-dual-pane-mode.png" width="700"></a>

As you can see I've decided to use the power of tabs to implement this feature. This way you may organize your dual-tabs with same ease as dealing with ordinary tabs. I'm already using it for few days and I'm really happy with this solution. We just need to agree on some keyboard shortcuts for copying/moving files between panels.

I've also decided not to spawn new finder tabs in case there is no suitable tab for dual mode. In this case it just does nothing. I'm open for your suggestions how this should work in the future. I personally think opening new tabs is quite a heavy-weight operation and should be done only explicitly.

#### My path was not that straight

This hacking is more like archeology than anything else. One thing is reverse-engineering the Finder and understanding how it works internally, but that is not enough. To build something reliable on top of it I usually need to try different approaches and pick symbiotic ones which may survive in the real world.

Maybe you remember my early screenshot of dual pane prototype back from October. I've used there the technique of [relocating NSViews from hidden Finder window](http://blog.binaryage.com/totalfinder-with-tabs) for right-side list view. The solution was very fragile and unstable. I've never managed to make it fully working. I would probably need to pull much more of my hair off to get it into good shape. I'm really glad I've followed the tabs-path instead.

<a target="_blank" href="/images/totalfinder-old-dual-approach.png"><img src="/images/totalfinder-old-dual-approach.png" width="700"></a>

#### Custom crash reporting

You will get chance to upload crash report as a gist and send me an email. Hope you will never have to see this dialog :-)

<a target="_blank" href="/images/new-crash-report-dialog.png"><img src="/images/new-crash-report-dialog.png" width="400"></a>

#### Locked dock? "killall Finder" for rescue 

Sometimes TotalFinder locks Finder and other apps. The symptom is that other apps are not able to quit (even Force Quit) and just stay in the Dock in zombie state. It happens usually shortly after re-installation. 

If this happens, please kill Finder and start from scratch by typing this in Terminal.app:

`killall Finder`

I have to catch this annoyance. I'll probably replace whole installer with custom script. This way I'll know exactly what installer does instead of relying on Apple's magic. Btw. right now it is not possible to downgrade TotalFinder directly. The installer just don't replace it in case of going to lower version number. You have to manually uninstall using Uninstall.scpt and then install older version.

#### What's next?

At this moment my roadmap looks like this:

  * Continue fixing quirks and improve stability
  * Add drag-and-drop tabs, cut and paste, and keyboard shortcuts for sidebar items for v0.8
  * Terminal.app co-operation for v0.9, open beta period?
  * Hacking NASA satellites? ;)

These features should be much easier compared to tabs and dual-pane mode. I'm optimistic. Stay tuned!