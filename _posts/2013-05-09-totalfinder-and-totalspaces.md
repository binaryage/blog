---
layout: post
title: "TotalFinder 1.4.9 and TotalSpaces 1.2.2"
tags: [thoughts]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/binaryage-badge-64.png" class="intro-icon"/>

**In the <a href="http://blog.binaryage.com/meet-brian-and-mike/">last post</a>, I introduced a couple new BinaryAge teammates and hinted that we'd have new TotalFinder and TotalSpaces releases.  <a href="http://totalfinder.binaryage.com">TotalFinder 1.4.9</a> has been in the wild for a month now and has been doing great.  <a href="http://totalspaces.binaryage.com">TotalSpaces 1.2.2</a> was released just last week and added a lot of new features!**

#### TotalFinder brings back colored sidebar

Besides making TotalFinder more stable, we added some new features that have been often requested by customers. A new preferences pane makes it easier for you to see what you can tweak, including new tweaks:

  * colored sidebar icons, based on a SIMBL plugin called <a href="http://cooviewerzoom.web.fc2.com/colorfulsidebar.html">ColorfulSidebar</a>.
  * the new ability to open new tabs with the previous Finder location.
  * a progress bar over the Dock icon when copying files.

We fixed several issues, too, including a few related to keyboard shortcuts and the escape key. Unfortunately, we're still working to fix integration with TimeMachine. For now, relaunch Finder so it loads without TotalFinder before you enter TimeMachine, then reopen TotalFinder when you're done.

I want to give special thanks to <a href="https://github.com/shpakovski">Vadim Shpakovski</a> for his <a href="https://github.com/shpakovski/MASShortcut">MASShortcut</a> framework for managing keyboard shortcuts.

#### TotalSpaces intro video

<object width="600" height="420" classid="clsid:02BF25D5-8C17-4B23-BC80-D3488ABDDC6B" codebase="http://www.apple.com/qtactivex/qtplugin.cab">
<param name="src" value="http://cdn.binaryage.com/totalspaces-intro.mov">
<param name="autoplay" value="false">
<embed src="http://cdn.binaryage.com/totalspaces-intro.mov" width="600" height="420" autoplay="false" pluginspage="http://www.apple.com/quicktime/download/">
</embed>
</object>

Stephen spent most of his time over the past few months on a number of improvements and brand-new features.

TotalSpaces 1.2.2 makes it much easier to navigate among your multiple spaces, especially since space names are now shown in the overview grid. And when you are using the grid, you can now zoom into a window by hovering over it and holding the Shift key, so you can very quickly see which window is which.

Switching in and out of the overview grid is smoother and, in Mountain Lion, enhanced with an animated zoom.

With this version, you have better control. Improvements include space transitions that always match the direction you commanded even when circulating, plus hotcorners in multi-screen setups work much better now, too.

And, for kicks, don't forget you have all of the Quartz transition types available -- sliding, cube, flip, or it can be instant for maximum speed.

Finally, TotalSpaces has been translated into a few new languages. If you'd like to help out by translating it into your own language, <a href="https://github.com/binaryage/totalspaces-i18n">see here</a>.