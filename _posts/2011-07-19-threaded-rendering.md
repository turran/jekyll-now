---
layout: post
title: Threaded rendering
date: '2011-07-19T12:23:00.004+02:00'
author: turran
tags:
- enesim
modified_time: '2011-07-19T12:33:35.259+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-7225475766812394162
blogger_orig_url: http://www.turran.org/2011/07/threaded-rendering.html
---

The enesim stack has been actively developed on the past months, we have lots of new features and new design concepts but this post is about threaded rendering. Recently a threaded rendering path has been committed into enesim given outstanding results, for examlple running the benchmark application with the circle.escen example we have:  
  
Without threaded rendering  

  
./benchmark -f ../../examples/circle01.escen -d -t 10000  
../../examples/circle01.escen            \[15.375 sec\]  

  
  
And with threaded rendering  

  
./benchmark -f ../../examples/circle01.escen -d -t 10000  
../../examples/circle01.escen            \[4.948 sec\]  

  
  
This test was done on a quad core CPU and the gain is around 3x, of course the gain depends on the actual renderer to draw, the more complex the better.
