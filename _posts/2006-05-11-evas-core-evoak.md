---
layout: post
title: Evas Core, Evoak
date: '2006-05-11T09:50:00.000+02:00'
author: turran
tags:
- efl
modified_time: '2008-11-20T09:53:59.154+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-2670341979700988902
blogger_orig_url: http://www.turran.org/2006/05/evas-core-evoak.html
---

I have uploaded the changes I've done to Evas and Evoak. The Evas package is renamed to evas_core for easy interoperation between the current evas and my own. My changes are:  

*   Build Modules outside main tree
*   Rearrangement of the headers
*   Object Engine support

The Evoak's package is a rewrite of almost everything the old evoak had. Test the edje loader!. Feel free to leave any comments about them. Note that the cvs version I made my changes in is very old (a few months) so don't expect to find the latest cvs features, I didn't have the time to merge them.
