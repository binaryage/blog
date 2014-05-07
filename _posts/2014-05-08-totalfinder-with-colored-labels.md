---
layout: post
title: "TotalFinder 1.6 with Colored Labels"
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/>

** Great news! Over last few months I've done a great progress on TotalFinder. Today I'm happy to announce [TotalFinder 1.6](http://totalfinder.binaryage.com/changes#1.6) with [Colored Labels](http://totalfinder.binaryage.com/colored-labels). **

#### Colored Labels

We all remember color labels from Mountain Lion, right? In Mavericks the labels were replaced with tags represented by smaller colored dots. Under Mavericks you can now apply multiple tags to selected items. In effect it is not clear what color should win, so Apple decided not to paint row backgrounds colors at all.

TotalFinder 1.6 offers you an option to render full-row color background using color of the last tag applied to an item. If you keep this rule in mind, can use tags in a way which emulates color labels in older OS versions.

<img src="/images/full-clabels.png" class="blog-image"/>

The implementation is solid and I'm really happy about the final outcome. Read more in **[the documentation](http://totalfinder.binaryage.com/colored-labels)**.

#### More stability and fixes

I did a lot of work on TotalFinder code base. It is now more flexible. You know, it always has been a challenge to keep TotalFinder updated with system changes. I believe I will be able to react to Finder changes in new OS X more rapidly.

Notable improvements in version 1.6 are:

  * Finally fixed pretty bad <a href="http://discuss.binaryage.com/t/totalfinder-does-not-clear-selection-keyboard-shortcuts-dont-work/1611/5">Cut &amp; Paste glitch</a>
  * Resolved click-drag issue <a href="http://discuss.binaryage.com/t/mavericks-totalfinder-window-moves-position-on-screen-by-itself/1687">causing window jump</a>
  * DMGs now open as separate standard Finder windows - which should resolve confusion about missing sidebars
  
As always, here is the full changelog: [http://totalfinder.binaryage.com/changes](http://totalfinder.binaryage.com/changes)

#### It is the time to say Lion goodbye

At this point I'm also officially dropping support for OS X 10.7. The last supported Lion version is 1.5.38.