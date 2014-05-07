---
layout: post
title: "Surfing the waves of Mavericks"
tags: [TotalFinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/binaryage-badge-128.png" class="intro-icon"/>

** Mavericks GM is out and public version will be released later this month. Now is the time to give you an update on our progress. **

Apple did a great job on this release and we as users are quite happy with the new system. You guys should update soon.

#### TotalFinder 1.5 is ready for Mavericks

Apple implemented tabs in Finder under Mavericks. That was an important [TotalFinder](http://totalfinder.binaryage.com) feature, but we believe TotalFinder still makes good sense because of other popular features including [dual mode](http://totalfinder.binaryage.com/dual-mode) and [folders on top](http://totalfinder.binaryage.com/folders-on-top). Over last months we've worked hard to port all the existing TotalFinder features to Mavericks at least for current users. And we are happy to say that all Mountain Lion features are available under Mavericks including Chrome-style tabs.

You can download TotalFinder 1.5 here:
[http://totalfinder.binaryage.com/changes#v1.5](http://totalfinder.binaryage.com/changes#v1.5)

#### TotalSpaces2 will be a paid upgrade

[TotalSpaces2](http://totalspaces.binaryage.com) is in beta testing at the moment, and we hope to have it polished and ready by the time Mavericks is released. It has been an awful lot of work to do the port to Mavericks, so it will be a paid upgrade. But we feel it's fair that the upgrade will be free for anyone who purchased TotalSpaces after OSX Mavericks was announced.

We will post more about the release of TotalSpaces2 soon.

#### TotalTerminal fork goes closed-source

[TotalTerminal](http://totalterminal.binaryage.com) works under Mavericks, but needs some polish. We decided to cleanup the codebase and share some library code and tools with TotalFinder. This forced us to make the next release closed-source. Personally I'm sorry for that, but there are some Xtra-copy-cats out there and we don't want to share our secret sauce, and maintaining two codebases eats too much time.

TotalTerminal 1.4 will be released next week.

#### Asepsis breaks under Mavericks

Upgrading to Mavericks breaks [Asepsis](http://asepsis.binaryage.com). Unfortunately directly installing Asepsis 1.3 under Mavericks [prevents the system from booting](http://asepsis.binaryage.com/#panic-mode-). I was looking for a fix and current implementation is no longer possible. All loaded dynamic libraries need proper signatures from Apple under Mavericks. This is good for security, but renders hacks like Asepsis to be (almost) impossible.

Maybe you remember, Asepsis started as a feature of TotalFinder. I'm thinking about going back to that implementation which should still be possible under Mavericks. But this will require Asepsis users to install TotalFinder.
