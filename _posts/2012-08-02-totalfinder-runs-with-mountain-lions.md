---
layout: post
title: "TotalFinder runs with Mountain Lions"
tags: [totalspaces]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/icons/totalfinder-128.png" class="intro-icon"/>

** Good news! [TotalFinder 1.4](http://totalfinder.binaryage.com/changes#1.4) works fine under new OS X 10.8 - Mountain Lion.<br>And it got even better. **

#### The upgrade is free of charge for all existing customers

Although I put long hours into maintaining the software and communication with people, I didn't really bring any major new features since the Lion upgrade. I think it's fair to keep it as a free update. Save your budget or buy some [other cool productivity software](http://binarybakery.com/index.php).

#### TotalFinder got faster!

It happened last weekend when I decided to rewrite the old and dusty internals of how TotalFinder manages Finder windows. It was needed to solve some outstanding Mountain Lion issues and as a side-effect it made all things much cleaner and faster. I'm pretty happy about it.

#### Snow Leopard is history. Get over it.

Sad, but I need to move on. As you can imagine TotalFinder is a hack on top of live Finder.app. I patch Finder internals and sometimes even fake AppKit logic. This is not your average Mac app. This is a brain surgery! Both Finder and AppKit are moving targets. They change between OS updates. It is really time consuming for me to test TotalFinder on different OS versions/setups/configurations and resolve bugs with multiple hacks.

I need more time for development. I decided to support just one OS version back. People running older OSes will have to stick with the latest compatible historical version. Currently I support Lion and Mountain Lion. The last Snow Leopard compatible version is [TotalFinder 1.3.4](http://totalfinder.binaryage.com/changes#1.3.4). Read more in [this article](http://totalfinder.binaryage.com/snow-leopard).

Hard feelings? [Blame me here](https://getsatisfaction.com/binaryage/topics/snow_leopard_not_supported_1_3_6).

#### TotalFinder has a bright future

I'm still here and dedicated to TotalFinder development. Right now I have whole TotalFinder source code loaded back in my head. So I hope I will be able to implement some hard but [highly requested features on the list](https://getsatisfaction.com/binaryage/ideas/popular). 

Also I have finally broken TotalFinder into separate plugins, eg. Tabs, Visor, CutAndPaste... It is now easier to maintain them and to develop new individual Finder tweaks separately. Reminds SIMBL? Yes! If you are a SIMBL hacker and want to join me hacking on TotalFinder, please drop me an email. Will pay in bitcoins :-)