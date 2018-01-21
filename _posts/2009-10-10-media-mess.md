---
layout: post
title: The media mess
date: '2009-10-10T15:57:00.000+02:00'
author: turran
tags:
- neuros
- kernel
modified_time: '2009-10-11T19:49:46.013+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-812251723042347944
blogger_orig_url: http://www.turran.org/2009/10/media-mess.html
---

The past weeks I've coding again the Neuros OSD2 development board on my spare times, given the months that have passed since last time I touched that device I thought that the Linux community would have brought a better media framework. Sadly it hasn't changed much as many people think.  
  
Every non-media subsystem on Linux seems to work good and well stable but when you need to bring latest video and graphics technologies to user level you really have a problem. (I don't really want to think how it would be if your salary depends on such thing, well in fact I do know ...)  
  
Basically, on Linux you have the following subsystems:  

  
*   Framebuffer:  
    The framebuffer is an abstraction which allows you to mmap the video (displayed and off-screen) memory, change resolutions, get timings, etc. There's a console driver on top of it too, fbcon.  
    
  
*   V4L:  
    The Vide4Linux API is mostly used to handle video capture devices, even so, it has API for things like Overlay, VBI, Radio, Output devices, etc. There's an intersection between this API and the framebuffer on the Video Output Overlay interface. Also, the Video Output interface can be seen as framebuffer device but with some differences, like the pixel format (mostly YUV and some RGBs formats) or the output standard (mostly TV standards).  
    
  
*   DRM:  
    This subsystem is in charge of handling the memory needed by the DRI drivers, manage the policies about who can be the owner of a device, who can query them, add contexts, etc  
    
  

  
The main problem I have had so far on the embedded devices I've work with is that several HW components match on different of the above API's but not completely on only one. For example, i might have a several graphics planes with several supported formats (YUV, RGB, etc), with color-keying, alpha blending, plane positioning or even 3D on one plane, but with several constraints that I should take care off, i.e one driver can't be the owner of a device, but it should be shared among several, with different interfaces, and in some of the cases such interfaces aren't enough to interact with one device.  
  
Recently there has been several RFCs on the Video4Linux media list to add new features, like a common contiguous memory allocator (similar to what DRM does), timings support for the output devices (like what the FB already has) or a central "Media" device which should control all the combinations or at least describe the topology of complex video pipelines. Kind of redundant isnt it?  
  
On the DRM side there are new things too, the new DRM KMS which has been added to Intel DRM drivers, that basically allows you to set the graphics mode in-kernel. No more X setting it up for you, this in theory allows you faster user switching, better graphical boot and (among others) be able to display a message whenever the kernel panics (BSoD). What will happen with the FB then? deprecate it? but what about the non 3D chips? are they going to use DRM as well? or keep the FB API?  
  
The result is that several APIs are trying to do what others are already doing, the idea of an API merging isn't heard on any ML. Someone must lead this different subsystem's community and join efforts to bring a good media framework into kernel. So sadly, even if the HW is evolving very fast on the media side, Linux doesn't give a good framework to support such stuff.
