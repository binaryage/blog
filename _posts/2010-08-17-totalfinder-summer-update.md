---
layout: post
title: TotalFinder summer update
tags: [totalfinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

** Hey, TotalFinder 0.9.8 is out. Unfortunately nothing much new. Just fighting the fire. **

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.9.8.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.9.8.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

#### The crashing nightmares

0.9.5 and 0.9.6 were pretty bad releases. There was a bug introduced by new localization code. Both versions <a href="{{site.url}}/localized-totalfinder-keeps-crashing">started crashing</a> immediately after expiration. Unfortunately this rendered auto-update mechanism defunct.

One day old 0.9.7 is also bad. Some people experienced crashes when manipulating tabs or closing windows. I believe I nailed the problems in 0.9.8.

Thank you all who sent me crash reports. Unfortunately I wasn't able to respond to all of them.

#### Tabs match new Chrome look

I've updated the tabs rendering code from latest Chromium sources. Kudos to Google's guys.

<img class="clear blog-image-border" src="{{site.url}}/images/new-chrome-tabs.png" title="Updated tabs rendering to match latest Chrome">

#### TotalFinder still runs after expiration

I've added small reminder that this software will become a paid software soon. I'm pretty sure you know it already. But over the internets I saw some discussions of people who do not read or they expect to stick with an alpha forever. So I wanted to make it clear this way. You can dismiss that small gray sticker in the top-right corner by clicking on it. I quite like this solution. This may be my future way how to communicate important things to all TotalFinder users.

<img class="clear blog-image-full-border" src="{{site.url}}/images/totalfinder-alpha-reminder.png" title="Alpha Reminder">

That crashing lesson was terrible experience and I want to prevent something like this in the future. I decided to run the same code path after expiration. This way I don't need to test the expiration state intensively prior to every release. 

To force people to upgrade I've added a little annoyance. Every 10 tab switches a dialog pops up which reminds you that you should update to the latest version.

<img class="clear blog-image-full-border" src="{{site.url}}/images/totalfinder-expired.png" title="Expired version has annoying limitation">

#### Spent some time on mastering XCode4

I was so excited about XCode4 that I've converted TotalFinder projects and used it for development. This slowed me down quite a bit, because it is still buggy alpha software with many flaws. It has also completely new UI to learn. But I couldn't help myself. I need to live dangerously on the bleeding edge. I think you guys who are using TotalFinder since early versions you know exactly what I mean :-)