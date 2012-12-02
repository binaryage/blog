---
layout: post
title: Localized TotalFinder keeps crashing after expiration
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**My mom always told me: "write automated tests, my boy"<br>But you know... I had always better things to do.**

#### After expiration TotalFinder wants to say something...

But my localization function crashes for some reason in Russian, Japanese and Chinese versions. And maybe in others too! <strike>I would guess translators haven't used localization string placeholders correctly or it's something on my side.</strike>

The reason was much simpler. I just used a plain C string instead of Objective-C NSString at one place when printing expiration info. This caused the crash in all versions regardless of localization state. This bug affects both 0.9.5 and 0.9.6. 

#### The rescue: Please upgrade to TotalFinder 0.9.9 manually

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.9.dmg"><img src="/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.9.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

I'm sorry for the inconvenience. The bug has been fixed from 0.9.7.