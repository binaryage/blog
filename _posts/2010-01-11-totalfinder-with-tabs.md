---
layout: post
title: TotalFinder with tabs!
tags: [totalfinder, releases]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/>

**I'm proud to announce a new version of [TotalFinder](http://totalfinder.binaryage.com) which introduces the tabs feature.**

<div class="blog-download">
  <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.6.dmg"><img src="/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.6.dmg</div></a>
  <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

<img class="blog-image no-shadow" src="/shared/img/totalfinder-mainshot.png" title="TotalFinder has Chromium tabs!">

The next expiration date is set to January 25, 2010 and it will be probably maintenance release to iron out all problems introduced in this ground breaking update.

#### Tabs gently ripped from Google Chrome project

I had an idea of bringing tabs experience into Finder back in November 2009. Obviously this is a hard task, but so exciting. I'm quite new to Cocoa and I've never implemented such a complex UI element in Cocoa before. But I'm not afraid to search the internet and get deep into problems I happen to be exploring.

Luckily enough, there is a great state-of-the-art open source tabs implementation in the <a href="http://code.google.com/p/chromium">Chromium project</a> available. I've studied briefly their codebase and it looked like a promising path to follow. I took their main browser window implementation and also components implementing tabs and extracted them from the main project. I've spent few days stripping dependencies and isolating functionality I needed. Dirty job but it paid off. After few evenings I've got working skeleton app with blank tabs.

I'd like to thank Google who made this all possible. I was really surprised how clean and well-documented the Chrome code is. People working on it earned my full respect. Kudos guys! By the way <a href="http://en.wikipedia.org/wiki/Blacktree_Software">Alcor</a>, the guy who invented Visor and QuickSilver, is also working on mac-specific features of Google Chrome. This browser thingy is in good hands.

#### Tabs transplantation with Finders as child windows

The next big task was to integrate tabs implementation with Finder. It wasn't clear to me how could I possibly do it. In the Chromium implementation every new tab has it's content area realized as a NSView. In the case of Chrome, tab contents are obviously web pages rendered by the webkit. In case of TotalFinder I wanted to render inner contents of original Finder windows.

Remember? I don't have source code of Finder, so I basically need to act as a middleman between OSX and Finder.app. Understanding both sides and at interesting points faking what OSX is telling to Finder and altering what Finder is doing to OSX. That's my playground. For example I'm operating on Cocoa level by talking to OSX on Finder's behalf.

I tried a technique of relocating NSViews from temporary Finder windows to tab contents. This brutal transplantation caused Finder to die quickly. I was trying hard to save the situation, but it is probably too brutal to relocate NSViews from main Finder window into hostile windows. Making this work would probably need to bypass big parts of Finder internals. Scary!

But I didn't give up. The main problem I was facing was how to re-use whole Finder windows as they are without disassembling them into smaller parts. I could overlay windows one on top of other and sync their positions, but I needed to solve window ordering problem. I simply needed to glue two or more windows together and fake them to act as one window for the user in all situations. I was looking for solutions and I've found quite hidden gem. The "child windows" feature of OSX windowing system. After few experiments I was seeing the light of hope again.

Child windows was a great bet and it solved the main pain point. The rest was just hacking around problematic behaviors. By the way you may try to do a window screenshot of the TotalFinder (CMD+SHIFT+4 and then hit SPACE). You will see clear split between tab content realized as a child window and frame window itself.

I'm pretty excited about this solution. It works better than I anticipated. In a nutshell it is pretty clean play with windowing system without breaking Finder consistencies.

#### What's next?

I'm pretty confident I can make dual-panel work using a similar technique. I have a semi-working prototype with relocating NSViews. In this case it was easier, because NSView transplantation takes place between two finder windows which is obviously not that destructive.

But with this new technique I have another path I can possibly follow and I believe child-window technique is generally a better way to go. Cross your fingers.

Please test v0.6 with your workflows and [share](http://getsatisfaction.com/binaryage) your experiences with me.