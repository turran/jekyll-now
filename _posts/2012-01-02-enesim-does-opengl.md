---
layout: post
title: Enesim does OpenGL
date: '2012-01-02T21:16:00.001+01:00'
author: turran
tags:
- enesim
modified_time: '2012-01-02T21:16:33.211+01:00'
thumbnail: http://2.bp.blogspot.com/-Euzp4KEYqV0/TwIQDc3qxDI/AAAAAAAABP0/Qjx_OAMnlxU/s72-c/enesim_gl.jpg
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-4927464656256537662
blogger_orig_url: http://www.turran.org/2012/01/enesim-does-opengl.html
---

Finally I got some time to start implementing the OpenGL backend interface on the renderer side. On the surface side, it was already possible to create surfaces with a GL texture associated using the OpenGL Enesim's pool but we were missing renderers.  
  
Right now only simple renderers are implemented through fragment shaders. Mainly: stripes, checker and background. The approach is to always use shaders, being it geometric, fragment or vertex, I'm working on implementing geometric shaders for the different shapes but I don't have the hardware that supports it, so I suppose it will have to wait .... but good things will come in the future, like having a full GUI (Eon) done on OpenGL or rendering SVG files (ESVG) with full hardware acceleration  
  
Anyway, here is a screenshot, everyone loves screenshots! Here is a simple GLX window displaying a surface which was previously rendered with a stripes renderer which is  rotated.  
  

[![](http://2.bp.blogspot.com/-Euzp4KEYqV0/TwIQDc3qxDI/AAAAAAAABP0/Qjx_OAMnlxU/s320/enesim_gl.jpg)](http://2.bp.blogspot.com/-Euzp4KEYqV0/TwIQDc3qxDI/AAAAAAAABP0/Qjx_OAMnlxU/s1600/enesim_gl.jpg)
