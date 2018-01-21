---
layout: post
title: Recent enesim changes
date: '2012-08-20T21:04:00.000+02:00'
author: turran
tags:
- enesim
modified_time: '2012-08-20T21:09:51.499+02:00'
thumbnail: http://3.bp.blogspot.com/-HO63g2xbZ3I/UDKIwnH4YtI/AAAAAAAABbU/G01qPQYCISs/s72-c/svg_animated_clock.png
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-8032287110483009911
blogger_orig_url: http://www.turran.org/2012/08/recent-enesim-changes.html
---

It's been a long time since I write here, but the changes on the enesim stack deserve a new post. In the past months a lot of new features have been added and lots of bugs have been fixed. Just a small update of the changes given that I'm about to leave for vacations ...  
  
[Enesim](http://code.google.com/p/enesim/wiki/GettingStarted#Enesim) is now more OpenGL friendly, it is possible to render complete SVG files with GL, still not as good as the software based backend, but is evolving nicely.  
  
Egueb and specially [Esvg](http://code.google.com/p/enesim/wiki/GettingStarted#Esvg) is now able to render animated SVG files, it is still missing input (to be able to interact with the SVG files) and scripting (Javascript) support. But those will come in a near future. As an example, I'm attaching an [animated clock](https://upload.wikimedia.org/wikipedia/commons/4/4d/Animated_analog_SVG_clock.svg) rendered (and animated) with Esvg. You'll see some differences between the original file and our own version, mostly the lack of filters and some text glitches.  
  

[![](http://3.bp.blogspot.com/-HO63g2xbZ3I/UDKIwnH4YtI/AAAAAAAABbU/G01qPQYCISs/s320/svg_animated_clock.png)](http://3.bp.blogspot.com/-HO63g2xbZ3I/UDKIwnH4YtI/AAAAAAAABbU/G01qPQYCISs/s1600/svg_animated_clock.png)

  
The past weeks I've been coding again the [Eon](http://code.google.com/p/enesim/wiki/GettingStarted#Eon) toolkit and left [Esvg](http://code.google.com/p/enesim/wiki/GettingStarted#Esvg) for a while. I wanted to make it compile again with the new API changes and be able to start doing applications. So I took the [Escen](http://code.google.com/p/enesim/wiki/GettingStarted#Escen) viewer again as an example and here is the result:  
  

[![](http://2.bp.blogspot.com/-fkstA7GoYHc/UDKJakIrMiI/AAAAAAAABbc/c1lb6m4meCk/s400/eon_escen_viewer.png)](http://2.bp.blogspot.com/-fkstA7GoYHc/UDKJakIrMiI/AAAAAAAABbc/c1lb6m4meCk/s1600/eon_escen_viewer.png)
