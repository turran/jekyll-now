---
layout: post
title: Etch hits E's svn
date: '2008-12-09T15:39:00.000+01:00'
author: turran
tags:
- efl
modified_time: '2008-12-10T15:06:21.775+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-8099687935415107236
blogger_orig_url: http://www.turran.org/2008/12/etch-hits-es-svn.html
---

Etch, a timeline based animation library, finally arrives to E's svn repository. Basically you define animations based on key frames and a data type (integer, float, argb colors, etc), set the interpolation between those key frames and your callbacks will be called at every frame based on the number of frames per second that you have set.  
```
Etch *e;  
e = etch_new();  
etch_timer_fps_set(e, 30);  
a = etch_animation_add(e, ETCH_UINT32, _animation_cb, NULL);  
k = etch_animation_keyframe_add(a);  
etch_animation_keyframe_type_set(k, ETCH_ANIMATION_COSIN);  
etch_animation_keyframe_value_set(k, 10);  
etch_animation_keyframe_time_set(k, 3, 3015);  
```
Note that this library is totally agnostic about the main loop handler, you just need to call `etch_timer_tick(e)` to update the internal system.  
  
The example below is an application that transforms an evas' image and moves it based on a couple of Etch's animations and Enesim's transformation functions.
