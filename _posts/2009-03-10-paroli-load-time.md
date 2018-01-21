---
layout: post
title: Paroli load time
date: '2009-03-10T10:36:00.003+01:00'
author: turran
tags:
- openmoko
- paroli
modified_time: '2009-03-10T11:56:15.013+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-5495143574510036825
blogger_orig_url: http://www.turran.org/2009/03/paroli-load-time.html
---

This days I wanted to profile the paroli application, there are some issues with the scrolling and loading time. So I first took the loading time issue and tried to solve it. Right now Enlightenment takes around 7 seconds to fully load and Paroli takes around 20 seconds. As E17 loads Paroli as a startup application before loading the modules, the time GTA02 takes to show up Paroli since the moment the X server has started is around 30 seconds.  
  
The current E17 config we have is a default one, we basically load every module for E17 even if it is not used for Paroli. After tweaking the configuration and making illume's module to be loaded in an async way, the loading of E17 now takes half of the time, only 3.5 seconds (The new config is already committed). Sadly Paroli itself still takes too much time.  
  
Note that all the numbers above are on a NFS system, but the relative slowness is the same for a flash filesystem.
