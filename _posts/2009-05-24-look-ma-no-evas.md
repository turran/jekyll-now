---
layout: post
title: Look Ma, no Evas!
date: '2009-05-24T16:36:00.011+02:00'
author: turran
tags:
- efl
modified_time: '2009-05-27T14:06:57.550+02:00'
thumbnail: http://3.bp.blogspot.com/_bp5z7TGyQ6k/Shls-S8KPmI/AAAAAAAAADU/627hq5uzL6g/s72-c/stack.png
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-8553425046068439419
blogger_orig_url: http://www.turran.org/2009/05/look-ma-no-evas.html
---

The past few months I've been away from main EFL development. With no particular reason than to build a different approach to the canvas library and to bring up this new concepts / features into mainline, similar to what happened with Eina.  
  
The stack I've been developing is as follows:  
  
[![](http://3.bp.blogspot.com/_bp5z7TGyQ6k/Shls-S8KPmI/AAAAAAAAADU/627hq5uzL6g/s400/stack.png)](http://3.bp.blogspot.com/_bp5z7TGyQ6k/Shls-S8KPmI/AAAAAAAAADU/627hq5uzL6g/s1600-h/stack.png)  
  

*   Enesim: The graphics library. You can find more information about it at the [wiki page](http://trac.enlightenment.org/e/wiki/Enesim)  
    
*   Emage: Is a library to load and save images in different formats. It supports synchronous and asynchronous operation and also user provided modules.  
    
*   Etch: The animation library. It basically interpolates two values using several algorithms, like: discrete, linear, sin, with bezier control points, etc.  
    
*   Ekeko: An OO property system. It has an abstract canvas and renderable types, UI events, generic properties, syncrhonous and asynchronous dispatching, among other features.  
    
*   Eon: This is where all the efforts join. Eon started as an improvment to Etk (still called etk2 on the repository), but then the initial idea diverge and now the code base is very different to what Etk is. Basically Eon has support for basic renderable shapes, like images or rectangles, support for subcanvases, transformations for images, etc.  
    

  
Here you can see a simple demo with some features I've done the past days: animated matrix transformations  
  
  
<object id="BLOG_video-995868701a49816b" class="BLOG_video_class" contentid="995868701a49816b" width="320" height="266"></object>
  
  
Update: To create the video I used this xml. Eon has a parser for XML based scene files.  
  
```
<etk w="100%" h="100%" id="canvas01">  
<rect x="0" y="0" w="100%" h="100%" color="white" id="rect01"/>  
<image x="40%" y="25%" w="50%" h="50%" file="tiger.png" id="image01">  
  <animMatrix name="matrix" type="0" dur="3s" from="0" to="0.7" calc="0" begin="click" repeat="-1" id="anim01"/>  
  <anim name="color" dur="5s" from="0xffff0000" to="0x66660000" calc="0" begin="click" repeat="-1" id="anim02"/>  
</image>  
<rect x="60%" y="10%" w="25%" h="25%" color="0xaa0000aa" id="rect02">  
  <anim name="y" dur="10s" from="10%" to="80%" calc="0" begin="click" repeat="3"/>  
  <anim name="color" dur="5s" from="blue" to="0xaaaaaaaa" calc="0" begin="click" repeat="-1"/>  
</rect>  
<rect x="10%" y="45%" w="25%" h="25%" color="red" id="rect02">  
  <anim id="myanim" name="x" dur="3s" from="10%" to="60%" calc="0" begin="click" repeat="1"/>  
  <anim id="anim04" name="color" dur="5s" from="red" to="0xaaaaaaaa" calc="0" begin="#myanim.stop" repeat="-1"/>  
</rect>  
</etk>  
```
