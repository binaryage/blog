---
layout: post
title: Crash Reporting in binary age
tags: [totalfinder, crash reporting]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

**I decided to share some of my development stories. It looks like some folks enjoy this technical reading.**

#### Is it possible to build decent crash reporting system during Saturday?

<img class="blog-image-full-border" src="/images/crash-development.png" title="Commit logs as seen in GitX">
<div class="small" style="text-align:right">image taken from <a href="http://gitx.frim.nl/"><b>GitX - free OSX git client</b></a></div>

As you can see, the answer is YES, even if you wake up at 1pm.

The trick is to take existing tools and make them play together. I took Google's Breakpad, Apple's OSX crash reporting system, GitHub's gist, User's email client and Google's Gmail. Btw, if you don't have much imagination try [CookMate](http://www.cookmateapp.com), an iPhone app by Czech folks I've met recently.

#### Google already runs realtime crash reporting system, it's called Gmail

This is how my crash reporting system looks for me as a developer.
<img class="blog-image-full-border" src="/images/gmail-based-crash-reporting.png" title="The filtered crash reports in gmail">
The best part is I didn't have to learn anything new and I can use all Gmail goodness for managing my crash reports. 
The killer feature is that I can communicate the crash directly with the reporting user just by doing a reply.
I could imagine many "serious" crash reporting systems really suck at it.

#### User gets a pre-generated email

When TotalFinder crashes the user a gets custom dialog with explanations:
<img class="blog-image" src="/images/crash-dialog1.png" width="310" style="float:left" title="The crash reporting dialog - generating">
<img class="blog-image" src="/images/crash-dialog2.png" width="310" style="float:left" title="The crash reporting dialog - send report ...">
<br clear="all">

When clicking "Send Report ..." I upload the crash report anonymously to Gist and open pre-generated email with a link:

<img src="/images/crash-reporting-mail.png" class="blog-image-full" title="The crash report email template">

User can check the link if there is no confidential information. It's exactly the standard Apple's crash report you would find in their dialog:
<img src="/images/crash-reporting-gist.png" class="blog-image-full" title="The crash report uploaded to gist.github.com">

This is no rocket social engineering surgery. This is just a system I would like to use as a user. 
There is a pretty good chance the user is able and willing to send an email.
There is also explanatory text which looks like a message they are replying to with personal note that all crashes are being read by the author and not some black hole.
But what's more: It is completely transparent! They probably trust their email client more than some spinning TCP/IP wheel of some custom reporting dialog. 
All information is pure text so they can check it before sending. I didn't want to use attachments, but thanks to gist the mail is not bloated and scary.

I think Mozilla's guys should take note. I'm running on beta builds of Firefox and their crash reporter has sending checked on by default. So even if I don't want actively send the crash report and I don't notice it I click close and it starts spinning and sending something I cannot even inspect. I know they are good guys, but I was pissed off several times because they tricked me to send "something" while I was working on my secret web projects :-)

#### Ok, I'll tell you how I did it ...

First I went to Google and started to search for some drop-in solution. I was very pleased with [Sparkle](http://sparkle.andymatuschak.org/) updating system (thanks Andy!) so I was in hope to find some decent crash reporting system.

Daniel Jalkut of Red Sweater Software wrote a great [Crash Reporter Roundup](http://www.red-sweater.com/blog/860/crash-reporter-roundup). After reading, it was obvious I'm not alone on this planet who looks for solution to that problem. More than that, some nice people were sharing their projects with the world. So nice afternoon. Thanks!

In the beginning I decided to flirt with Google's [Breakpad](http://code.google.com/p/google-breakpad). Looked like a young, shiny and well maintained project for big guys. And it's cross-platform! Which sounds great even if I don't need it at all. Anyway the great feature which finally sold me on it was an out-of-process crash reporter. Good stuff.

I started integration operation in TotalFinder and I ended up debugging a crash report dump routine which was going through stack frames of dying process and doing some woo-doo of reading some info out of it. It wasn't working at all and I realized I'm doing something really wrong. TotalFinder is a SIMBL plugin running in 64-bit Finder.app, Breakpad supports only 32-bit right now as one could read in Stefan Reitshamer's [article on this topic](http://www.reitshamer.com/?p=18). For a second I thought I could fix it for them, but then I realized I'm not the Messiah and I cannot do miracles with 64-bit opcodes. Sadness!

Ok, it's 13:50 and I'm getting back to the list of available crash reporting solutions. Some of them I excluded just by looking at their website. Some of them were promptly excluded just by looking at their source code. And rest of them I excluded by trying to integrate them. I have quite an uncommon situation here with 64-bit SIMBL so maybe they integrate well with classic apps. I don't remember the details, but my case was probably quite painful.

Well it's 17:14 and I'm doing rant commit about how all other solutions suck and going back to Breakpad. 36 seconds later I'm surprisingly merging my experimental branch with whole non-working breakpad into master. This is a suicidal operation I usually do when I want to finish the work no mater what. While it is on topic branch, it could be postponed. But when I merge it into master and break whole thing, it means I'm serious about it.

Ok it's still 17:14, the situation is serious and thats time for a hot shower. I got back with a fresh idea. I don't have time to roll my own solution. But I could use good parts from Breakpad and make something which could possibly work by the end of the day. I did a few things to Breakpad. I've commented out the whole machinery responsible for generating crash dumps and then I made their crash report dialog look nice with new "Send Report ..." button. Great! Now I had working out-of-process 64-bit crash reporting system which was not capable of generating crash reports. 

Let's call Apple for rescue. Apple's standard crash reporter knows how to generate good crash dumps even for 64-bit apps, the only problem is their standard crash reporting dialog popping up. One could google that the standard crash reporter is able to operate in so called "<a href="http://en.wikipedia.org/wiki/Crash_Reporter_(Mac_OS_X)">server mode</a>" which simply means it is generating crash report files on disk, but does not display crash dialog to the user. It sounds good but it has one problem. This setting is system-wide. My brain cannot understand why they did not introduce a system so this behavior could be configured individually per-app. They already have some routine which decides what to do with crashing app, this would be like three lines of code of reading plist and matching app identifier against it. Unfortunately there seems to be no other solution. Never-mind. This is exactly the situation when hacks are needed. 

I did some bold experiments and this is what I ended up doing. In Breakpad's crash handler of dying processes I simply switch crash reporter to server mode and let the app die with crash. The out-of-process crash sender gets spawned and first thing I do there is a reset of this setting back to original value. And it works well! Yes, there is a small time window in which other apps' crashes may be not reported to the user and yes hypothetically when my crash sender dies before it returns the value to the original it may make the user's system not open crash dialogs in the future. It is that big problem? I have a theory that people who care are just reading this article so they know about this behavior and other people just don't care. In the future I'll add a check into TotalFinder itself which returns the original value in case it finds it non-returned for some reason. This way the possibility of leaving the system in unwanted state would be minimal. You'll have a higher chance of your disk exploding than staying in the state of server mode crash reporting.

Ok, now I forced crash report file to be silently generated somewhere on the disk. The last step was just waiting for it to get generated and finding it. At this point I enable "Send Report ..." button. When user clicks it, I grab the file and upload it to [gist.github.com](http://gist.github.com). Again I'm so uncool for reinventing the wheel so I use Chris Wanstrath's [gist.rb uploader](http://github.com/defunkt/gist). Jaaaaay it's Ruby code! Much better than hanging myself trying to do a HTTP call using Cocoa.

And how does one open a mail client with a message? I tried to access the email APIs from Objective-C and it was like going back to the 80's. I kinda like the music, but those bearded men with strong glasses suck at making APIs. You may wonder but the easiest way is to generate mailto link and simulate click on it. Browsers already know how to open your system email client - whatever it is. And it will work in the future because nobody wants to break the web, right?

The web has won again. And that is the end of my story. 

#### No spam just meat

As you can see I'm getting 2 crash reports per hour on average. I didn't have time to analyze them in more detail. But it looks like most of them are related to patching filesystem APIs for a .DS_Store hack early after TotalFinder starts. I can imagine that during startup many threads are doing heavy filesystem work and I confuse them by doing some dirty job of redirecting filesystem calls. Will definitely look into this soon.

<div class="small">I'd like to thank all people who have been so kind and sent me their reports. This will definitely help me make TotalFinder better.</div>