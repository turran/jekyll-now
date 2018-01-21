---
layout: post
title: Initial Benchmark of the xf86-video-glamo on GTA02
date: '2009-03-01T16:58:00.000+01:00'
author: turran
tags:
- openmoko
- efl
modified_time: '2009-03-01T19:46:00.762+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-1961891870367973356
blogger_orig_url: http://www.turran.org/2009/03/initial-benchmark-of-xf86-video-glamo.html
---

After my tremendous problems building my build environment I have finally succeed :)  
So I had the chance to give xorg-video-glamo a try and see how well it behaves. To do the benchmark I used expedite and the results are:  
  
```
2.76 , Image Blend Unscaled  
12.69 , Image Blend Solid Unscaled  
1.56 , Image Blend Nearest Scaled  
8.77 , Image Blend Nearest Solid Scaled  
0.45 , Image Blend Smooth Scaled  
5.93 , Image Blend Smooth Solid Scaled  
5.02 , Image Blend Nearest Same Scaled  
22.05 , Image Blend Nearest Solid Same Scaled  
1.27 , Image Blend Smooth Same Scaled  
11.84 , Image Blend Smooth Solid Same Scaled  
0.51 , Image Blend Border  
6.67 , Image Blend Solid Border  
0.44 , Image Blend Border Recolor  
4.29 , Image Quality Scale  
7.22 , Image Data ARGB  
4.89 , Image Data ARGB Alpha  
6.54 , Image Data YCbCr 601 Pointer List  
6.04 , Image Data YCbCr 601 Pointer List Wide Stride  
6.67 , Image Crossfade  
9.28 , Text Basic  
1.05 , Text Styles  
0.79 , Text Styles Different Strings  
5.64 , Text Change  
5.67 , Textblock Basic  
4.67 , Textblock Intl  
1.81 , Rect Blend  
9.57 , Rect Solid  
69.84 , Rect Blend Few  
84.22 , Rect Solid Few  
41.09 , Image Blend Occlude 1 Few  
24.00 , Image Blend Occlude 2 Few  
17.50 , Image Blend Occlude 3 Few  
43.26 , Image Blend Occlude 1  
14.59 , Image Blend Occlude 2  
4.87 , Image Blend Occlude 3  
27.31 , Image Blend Occlude 1 Many  
6.81 , Image Blend Occlude 2 Many  
2.21 , Image Blend Occlude 3 Many  
3.79 , Image Blend Occlude 1 Very Many  
0.66 , Image Blend Occlude 2 Very Many  
0.36 , Image Blend Occlude 3 Very Many  
3.51 , Polygon Blend  
11.86 , EVAS SPEED  
```

The benchmark took around half an hour to end and from the final EVAS SPEED value, it is really, really slow.  
  
Note that right now the driver is just a wrapper on top of the fbdev, so no acceleration is coded yet, only software based rendering and giving that the CPU isn't that fast either, there's no surprise on the benchmark.  
  
The Xrender acceleration is one of the possibilities to improve the performance and the good news is that Evas already provides a Xrender based engine. So let's get the hands dirty and start hacking the driver! :)
