---
layout: post
title: Eon builder
date: '2009-09-10T21:29:00.003+02:00'
author: turran
tags:
- efl
modified_time: '2009-09-10T21:53:03.622+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-7627063186559429611
blogger_orig_url: http://www.turran.org/2009/09/eon-builder.html
---

It has some time since my last post. During this months I've been fixing, adding features and fixing (yes, again) several libraries on the stack I've been developing. Lots of stuff have changed, Enesim's API is getting more stable, Eon and Ekeko have hit E's subversion, etc.  
  
Loading xml files for different scenes is great, but not too great if you want to test the usability of the system, so I've started an Eon builder. A way to create objects, define and assign paint objects, animate them, etc, etc. Here's a simple demo of what's going on there  
  
<object id="BLOG_video-c2fc50fa673b3d9" class="BLOG_video_class" contentid="c2fc50fa673b3d9" width="320" height="266"></object>
  
As you see, it is on a very basic stage, you can move objects, resize them, etc. There's no toolkit used (yet?) mainly because I haven't decided yet what's the best approach, something similar to edje? an external xml + put-your-preferred-scripting-language? something similar to CSS but more powerful? Need to solve this before starting with the toolkit ...
