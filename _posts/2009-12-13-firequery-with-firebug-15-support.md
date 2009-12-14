---
layout: post
title: FireQuery 0.4 with Firebug 1.5 support
tags: [firequery, releases]
author_name: Antonin Hildebrand
author_uri: http://hildebrand.cz
---

<img src="/shared/img/firequery-icon.png" style="float: left; margin-right: 20px"> 

Did not much real work during weekend because of pre-christmas drinking with friends :-) But I've at least released a new version of [FireQuery](http://firequery.binaryage.com supports) which finally supports [Firebug 1.5](http://getfirebug.com) (in beta right now).


#### Firebug 1.5 support

Many thanks to [Steven Roussey](http://twitter.com/sroussey) who [implemented changes](http://github.com/darwin/firequery/commits/master) needed for new Firebug.

#### Alternative jQuery version

You may specify alternative jQuery version by typing `about:config` into browser URL:

<img src="/images/about-config-jquery-url.png" width="600">

Search for `extensions.firebug.firequery.jQueryURL` key and change it to fit your needs. For example you may specify one of Google-hosted [jQuery versions](http://code.google.com/apis/ajaxlibs/documentation/index.html#jquery).
