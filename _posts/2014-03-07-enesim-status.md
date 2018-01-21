---
layout: post
title: Enesim status
date: '2014-03-07T20:22:00.000+01:00'
author: turran
tags:
- enesim
modified_time: '2014-03-07T20:25:57.431+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-9077101858566645596
blogger_orig_url: http://www.turran.org/2014/03/enesim-status.html
---

It has been a year and a half from the last post, but none of the developments have stopped during this time. I'll try to do several posts in the following days explaining the different improvements on the whole stack of libraries.  
  
In Enesim, I've been porting all the renderer algorithms to the OpenGL backend and thus, all the libraries that depend on Enesim for drawing can use OpenGL out of the box without any specific modification but passing an Enesim\_Surface created by the OpenGL's Enesim\_Pool.  
  
Another improvement is that finally the NVIDIA's path extension can be used (when available) for the path renderer, besides Enesim own software and OpenGL implementations.  
  
On the current stack of libraries that I'm developing, having OpenGL support means that having SVG graphics/scenes using OpenGL for drawing is possible. In the same way, drawing Eon's widgets can be done using OpenGL without any special effort.
