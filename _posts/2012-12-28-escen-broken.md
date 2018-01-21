---
layout: post
title: Escen broken
date: '2012-12-28T20:49:00.003+01:00'
author: turran
tags:
- enesim
modified_time: '2014-02-13T13:51:46.733+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-2668501820319918329
blogger_orig_url: http://www.turran.org/2012/12/escen-broken.html
---

In order to advance on the automatic bindings for Ender elements, Escen is broken and thus Eon. Sadly Escen needs a heavy refactor right now, but at least new features have reached Ender. Now, it is possible to define functions for structs so basically we can now map into Ender more C libraries. This was a requirement for Ender long time ago to basically support properties and functions for known-size native objects. This allows for example to match the following header:  
  
```
typedef struct _Enesim_Matrix  
{  
 double xx, xy, xz;  
 double yx, yy, yz;  
 double zx, zy, zz;  
} Enesim_Matrix;  
  
EAPI void enesim_matrix_translate(Enesim_Matrix *t, double tx, double ty);  
EAPI void enesim_matrix_scale(Enesim_Matrix *t, double sx, double sy);  
EAPI void enesim_matrix_rotate(Enesim_Matrix *t, double rad);
```
  
With the following Ender definition:

```
struct "Matrix" {  
 double "xx";  
 double "xy";  
 double "xz";  
 double "yx";  
 double "yy";  
 double "yz";  
 double "zx";  
 double "zy";  
 double "zz";  
 translate(double, double);  
 scale(double, double);  
 rotate(double);  
};
```
  
And then do something like this on ender:  

```
Ender_Element *e;  
e = ender_namespace_element_new(ns, "Matrix");  
ender_element_property_set(e, "xx", 150.0, "yy", 320.0, NULL);  
ender_element_function_call(e, "rotate", 180.0, NULL);
```
  
So now both structs and unions behave as an opaque pointer (objects). Another pending issue was to remove the Enesim dependency on Ender and Escen. That implies that the types _SURFACE_ and _MATRIX_ are no longer valid and things like this on escen files are not supported anymore:  
  
```
set { transformation = rotate(0.78, 64, 64), translate(-30, -30); };  
```
  
Later we will find a solution, maybe add scripting directly? Who knows ...
