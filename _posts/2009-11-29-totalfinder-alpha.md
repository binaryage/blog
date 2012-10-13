---
layout: post
title: TotalFinder - alpha call for testing!
tags: [totalfinder, testing]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="{{site.url}}/shared/img/icons/totalfinder-64.png" class="intro-icon"/>

**[TotalFinder](http://totalfinder.binaryage.com) is my attempt to make Finder.app better for programmers and Mac power users. I want it better for myself!**

#### The Story

I use Finder as my primary file manager and I have many small ideas how could I make it better. But my ultimate goal is quite ambitious. The goal is to extend Finder to support dual-panel mode like Total Commander. People around me are leaving Windows for Macs and asking for a Total Commander replacement. Need to hurry! :-)

Do you know <a href="http://visor.binaryage.com">Visor</a>? TotalFinder is also implemented as a [SIMBL](http://en.wikipedia.org/wiki/SIMBL) plugin which extends Finder.app functionality. TotalFinder works in Snow Leopard only. The reason is that Finder.app has been rewritten into Cocoa in Snow Leopard which finally made this hacking possible.

#### TotalFinder 0.2 ALPHA

<div class="blog-download">
    <a class="download-link" href="http://downloads.binaryage.com/TotalFinder-0.2.1.dmg"><img src="{{site.url}}/shared/img/small-download-button.png"/><div>http://downloads.binaryage.com/TotalFinder-0.2.1.dmg</div></a>
    <div class="download-note">The full changelog: <a href="http://totalfinder.binaryage.com/changelog.html">http://totalfinder.binaryage.com/changelog.html</a></div>
</div>

It was tested on my MacBook Pro 17" with 10.6.2 OSX running 32-bit kernel.

Before you install it, open terminal and prepare this command:

`rm -rf "/Library/Application Support/SIMBL/Plugins/TotalFinder.bundle"`

There is a chance that during startup TotalFinder crashes and brings down whole Finder.app. The problem is that there is a process continuously starting Finder.app if it is not running somewhere in OSX. So it ends as an infinite loop of Finder.app starts and crashes until you remove TotalFinder SIMBL.

You were warned! Stay sharp!

Note: The bug should be fixed in 0.2.1

#### Features

OK, let's see some screenshots:

<img src="{{site.url}}/images/tf02-features.png" style="float:left; width: 49%" title="Preferences panel with Visor feature">
<img src="{{site.url}}/images/tf02-dsstore.png" style="float:left; width: 49%" title="Preferences panel with .DS_Store redirection options">
<img src="{{site.url}}/images/tf02-tweaks.png" style="float:left; width: 49%" title="Preferences panel with various tweaks">
<img src="{{site.url}}/images/tf02-purchase.png" style="float:left; width: 49%" title="Preferences panel with info/purchase screen">

<div class="clear"> </div>

As you can grasp from the images this version implements two main features:

* Visor-like system-wide Finder window available via a hot-key
* Prevention of littering .DS_Store files all over the place

And you can also see that I'm planning to start selling this at some point in the future when the thing gets more stable.

#### How does .DS_Store redirection work?

I'm pretty excited about solving the problem which has been bugging me for more than two years since the day I switched to Macintosh. Every single day! 

Look, I use Finder.app with enabled hidden files and I'm also pretty heavy Terminal.app user. The .DS_Store litter makes me cry! If you ever happened to google for a solution, you could find just some simple scripts for deleting .DS_Store files (futile!). Or maybe there is some commercial app which is capable of watching filesystem and deleting them after creation. But this is not good enough for me! I'm using folder colors in Finder ;)

Here is what I did in TotalFinder:

* I've redirected low-level filesystem calls which Finder.app does: 
  * Anytime Finder.app is asking to open `/some/folder/.DS_Store` file, I open it as `/usr/local/.dscache/some/folder/_DS_Store`
  * This way Finder thinks files are at original places but they are being physically created in prefix folder, effectively sandboxing them
  * The only exception is the prefix folder itself, when you go and see it in the Finder, no redirection is applied
* I've implemented kernel extension Echelon, which monitors folder renames (and deletes) and sends them to TotalFinder
  * You see why. This is important to keep DS_Store folder structure in prefix directory mirroring actual structure on the disk

Yeah, kernel extension sounds scary. But I didn't find a better solution in user-space. FSEvents are not precise enough (it just reports "something was changed"). BSD kqueues must be registered on per-file basis, so it is not usable in this scenario. At the end of the day that kernel extension turned out to be a really light-weight solution. I use KAUTH API to monitor kernel filesystem events. I do it only if TotalFinder is connected and only for renames and deletes. Testing is a simple C-string comparison and sending notification via socket.

I've been using TotalFinder with this redirection enabled for a while and it works pretty well. I've noticed only two drawbacks so far:

* .DS_Store file is created on Desktop during OSX restart, Finder crash or TotalFinder reinstallation
  The reason is that SIMBL plugin gets injected too late and Finder manages to write this .DS_Store file
* .DS_Store file is created when you modify Spotlight comment on a file
  This is caused by mdworker process and has no direct relation to Finder.app process. 
  It seems like Apple engineers scattered DS_Store functionality into more applications.
  I'm still investigating this. Temporary workaround is not using these Spotlight comments. Which is my case anyway.
  
I hope this is enough info for you to get started playing with TotalFinder. Your <a href="http://getsatisfaction.com/binaryage/products/binaryage_totalfinder">feedback</a> is appreciated! 

I've fixed tons of <a href="http://visor.binaryage.com">Visor</a> bugs and made it possible under Snow Leopard. Now it is your turn to help me roll this out :-) Thanks!