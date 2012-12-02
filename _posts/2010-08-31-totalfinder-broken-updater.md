---
layout: post
title: Aargh, broken auto-updater
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

** New TotalFinder 0.9.9 is out. Nothing exciting here.<br>Just embarrassment that I managed to break auto-updater. **

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.9.dmg"><img src="/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.9.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### Hey you! Don't click that button!

I didn't notice it, but I broke the Sparkle updater in previous releases.<br>The `relaunch` script is missing in 0.9.7 and 0.9.8. 

<img class="clear blog-image-border" src="/images/dont-click-that-button.png" title="Don't click that button!">

Instead of clicking 'Install Update', please directly download <a href="http://downloads.binaryage.com/TotalFinder-0.9.9.dmg"><strong>TotalFinder 0.9.9</strong></a> and install it manually from the DMG archive.

To prevent something like this in the future I have created small script which is able to extract DMG plus all pkg files inside and tell me the difference between releases. This enables me to do a final check of what is going to be included in the new releases. The build process is too complicated to trust (XCode4 is alpha).

<img class="clear blog-image-full-border" src="/images/totalfinder-dmg-diff.png" title="Diffing DMG between releases (the diff app is p4merge for Mac)">

This way I can spot unwanted file inclusions/exclusions or unexpected file size changes in future releases.

#### Please switch to BETA updates channel

I want to prevent future broken releases, so I have introduced two channels for updates. The idea is similar to Chromium update channels. You may stick with:

  * **Stable Channel** - contains infrequent well-tested major versions (1.x line)
  * **Beta Channel** - contains frequent minor versions (1.x.y line)

<img class="clear blog-image" width="300" src="/images/pick-beta-channel.png" title="You may switch between stable and beta channel">
  
I expect you, readers of this blog, to switch to the BETA channel and stay on the cutting-edge TotalFinder version to help me catch any possible problems before launching to a wider audience. Also this enables me to be much more agile in releasing new versions. Thanks! 

#### Compatibility with future Finder

Since I'm a fresh member of a Mac Developer Program I was able to prepare and test TotalFinder with the future Finder version (10.6.6). All looks fine. Don't be afraid of updating OSX when the time comes.