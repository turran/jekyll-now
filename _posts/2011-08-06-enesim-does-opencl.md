---
layout: post
title: Enesim does OpenCL
date: '2011-08-06T00:14:00.004+02:00'
author: turran
tags:
- enesim
modified_time: '2011-08-06T00:23:10.729+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-7049522101405114470
blogger_orig_url: http://www.turran.org/2011/08/enesim-does-opencl.html
---

This was something I had in mind for a long time, not neccessary OpenCL but an usable way to make a "backend" system for renderers and surfaces/buffers. That moment has arrived. Right now the enesim code has a well defined backend system and an incipient OpenCL support. Given the nature of a renderer each one should provide each own OpenCL algorithm but at least Enesim provides a good abstraction to define such algorithms and interact with them.  
  
The pool subsytem has been refactored in a way that a pool should create surfaces or buffers and define its backend type. Given that, once a renderer element wants to draw into a surface, we can call the correct functions based on the backend and the associated data of a surface.  
  
Still there are things to do on Enesim and specifically on other subsystems of the library (like being able to make converters use also the backend system, like having a YUV422 -> ARGB converter on OpenCL or stuff like that), but is a very good step on the road of the 1.0 release. The only implementation of an OpenCL renderer is done on the "background" renderer given its simpleness, but is a good start to understand how OpenCL works and what common arguments are needed for every renderer.  
  
Later, with this approach, we can easily add an OpenGL shader approach for renderers and a texture based software pool :)
