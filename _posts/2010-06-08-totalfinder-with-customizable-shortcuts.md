---
layout: post
title: TotalFinder with customizable shortcuts
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.9.3 is out with a few more features. This release has customizable shortcuts.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.3.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.3.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### Customizable Shortcuts

People with AZERTY keyboards had problem with my choice of keyboard shortcuts in 0.9.1. I decided to solve the problem once for all. You can now define your own shortcuts in case the default one conflicts with your custom keyboard layout.

<img class="clear blog-image" width="300" src="{{site.url}}/images/totalfinder-customizable-keyboard-shortcuts.png" title="TotalFinder provides distinct features which may be enabled at once">

#### Fixed installer and Asepsis initialization bugs

The installer often failed for people who decided to not install TotalFinder.kext. Maybe you didn't notice, but you can click the "Customize" button during the installation. 

This is also related to problems caused when the `/usr/local/.dscache` folder wasn't present during TotalFinder startup. In this case some initialization steps were not properly executed and TotalFinder might behave unpredictably.

#### I've got a little productivity crisis

First, I decided to switch from TextMate to XCode for Objective-C development. This was quite a productivity backslide, but I believe it is a good time investment for the future. I still do love TextMate for web development, ruby and ad-hoc text file editing, but XCode is way superior with its Objective-C integration.

Second, Google I/O talks, WWDC presentations, tech-podcasts and all the new technical stuff coming out these days. Sometimes I wish a day had 48 hours because I feel I cannot consume all of this :-)

Third, with nice weather there is much more "real life"(tm) activity out there. Friends are doing meetups, celebrations or just hanging out in pubs. I had to make several hard decisions about whether to go out or stay and code something on TotalFinder. There is still some boring work ahead like writing documentation, preparing localization support, implementing the licensing subsystem and setting up a web store. I would rather spend that time working on new features, but this has to be done. At least for me to stay motivated on the project.

Don't worry. I will keep you posted.