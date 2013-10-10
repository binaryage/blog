---
layout: post
title: "Surfing the waves of Mavericks"
tags: [TotalFinder]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/binaryage-badge-64.png" class="intro-icon"/>

** Mavericks GM is out and public version will be released later this month. That is the time to give you an update on our progress. **

Apple did a great job on this release and we as users are quite happy with the new system. You guys should update soon.

#### TotalFinder 1.5 is Mavericks ready

Apple implemented tabs in Finder under Mavericks. That was the main TotalFinder feature, but we believe TotalFinder still makes good sense because of other features. Anyways over last 4 months we've worked hard to port existing TotalFinder features to Mavericks at least for current users. And we are happy to say that all Mountain Lion features are available under Mavericks as well including Chrome-style tabs.

You can download TotalFinder 1.5 here:
[http://totalfinder.binaryage.com/changes#v1.5](http://totalfinder.binaryage.com/changes#v1.5)

#### TotalSpaces 2 will be a paid upgrade

TODO: Stephen

#### TotalTerminal fork goes closed-source

TotalTerminal works under Mavericks, but needs some polish. We decided to cleanup the codebase and share some library code and tools with TotalFinder. This forced us to make the next release closed-source. Personally I'm sorry for that, but there are some Xtra-copy-cats out there and we don't want to share our secret sauce. We did this decision because maintainig two codebases eats too much time.

TotalTerminal 1.4 will be released next week.

#### Asepsis breaks under Mavericks

Upgrading to Mavericks breaks Asepsis. Unfortunately installing Asepsis 1.3 under Mavericks prevents the system from booting. I was looking for a fix and current implementation is no longer possible. All loaded dynamic libraries need proper signatures from Apple under Mavericks. This is good for security, but renders hacks like Asepsis to be (almost) impossible.

Maybe you remember, Asepsis started as a feature of TotalFinder. I'm thinking about going back to that implementation which should still be possible under Mavericks. But this will require Asepsis users to install TotalFinder.