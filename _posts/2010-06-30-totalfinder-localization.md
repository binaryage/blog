---
layout: post
title: TotalFinder opened for localization
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/base/img/icons/totalfinder-64.png" class="intro-icon"/>

**TotalFinder 0.9.5 is here. This release added localization support and a few fixes.**

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.5.dmg"><img src="{{site.url}}/base/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.5.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### Translate TotalFinder and get a free license

I'm pretty sure that you understand that translation must be an ongoing process. TotalFinder will be getting new features over time and of course I want to be free to tweak and possibly change anything. I don't want to spend my time swapping text files in emails and micro-managing translators. Instead I want to focus on TotalFinder improvements and features. That's why I'm looking for a good solution to this localization problem.

You know that already, the [guys behind the GitHub](http://github.com/github) are my rock stars. Quite frankly, if I were a young lady I would want to have babies with all of them.

Ehmm, all right, I'm a big believer in the [GitHub](http://github.com/binaryage) concept. The transparency it offers when looking at versioning and collaboration is breath-taking. I didn't even announce localization support here on the blog and some folks already 'got it' and [have forked my repo](http://github.com/binaryage/totalfinder-i18n/network/members). I understand that not everyone is familiar with git and other tools I'm forcing you into, but if you are a techie I guarantee you [learning git](http://progit.org) and GitHub is damn well invested time. Take it as a good opportunity to learn something new. Now you have a reason and my full support.

For your information, this is my experience when collecting localizations, easy as pie! :-)
<img class="clear blog-image-full-border" src="{{site.url}}/images/github-totalfinder-localization-fork-queue.png" title="GitHub fork queue">

Please look at this repo and read the instructions:
[http://github.com/binaryage/totalfinder-i18n](http://github.com/binaryage/totalfinder-i18n)

I will be improving those instructions over time by answering your actual questions. There is a [sample Czech translation](http://github.com/binaryage/totalfinder-i18n/tree/master/plugin/Resources/Czech.lproj). All I needed to provide was translations of
several [string files](http://github.com/binaryage/totalfinder-i18n/blob/master/plugin/Resources/Czech.lproj/Localizable.strings).

#### Headaches solved with switching exotic keyboard layouts

Some Asian guys got into big troubles when they updated to 0.9.3. Switching complex keyboard layouts might cause the whole Mac to hang for a few seconds. 

This wasn't quite my bug but some hidden problem in the ShortcutRecorder library. All has been solved now and the world is better [by one patch](http://code.google.com/p/shortcutrecorder/issues/detail?id=40).

#### My fight for pixel perfection

You might remember that I slaughtered the Google Chrome codebase and extracted the tabs implementation out of it. Some pixels got lost during this dirty process and some eagle-eyed UI designers are poking me to fix it (thanks Steve!).

Now I'm slowly learning how rendering the tabs really works and trying to tame Cocoa rendering on the pixel level. This version made pretty good progress on this. 

Other news is that Google is (probably!) planning [a slightly different tab look](http://blog.chromium.org/2010/06/fresh-coat-of-chrome.html) in an upcoming version. It looks gorgeous in my opinion. TotalFinder will definitely keep up and I want to know every pixel by name.

<img class="clear blog-image" src="{{site.url}}/images/new-chrome-tabs-mockup.png" title="Upcoming Chrome tabs?">

Also one of the most requested features is [Safari-style tabs](http://getsatisfaction.com/binaryage/topics/allow_safari_style_tabs_or_unique_a_style_chrome_tabs_me_not_like). I hear you! I will put these newly acquired skills towards this ultimate goal (sometime after the 1.0 release).