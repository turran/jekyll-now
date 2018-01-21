---
layout: post
title: Egüeb's EFL Integration
date: '2014-04-02T21:23:00.001+02:00'
author: turran
tags:
- egueb
- efl
modified_time: '2014-04-09T11:16:28.585+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-6245378330764281631
blogger_orig_url: http://www.turran.org/2014/04/eguebs-efl-integration.html
---

On [https://github.com/turran/efl-egueb](https://github.com/turran/efl-egueb) you'll find the Egüeb's EFL integration project.  
Basically this projects does all the links between the different EFL technologies: Ecore, Evas, Edje and Egüeb.  
  
Given that Egüeb is based on the "features" concept to support different features on the documents (drawing, animations, input events, etc) all of theme can be easily matched against EFL's abstraction. For example all the input events are handled automatically using the Ecore Event abstraction. For animated documents (documents that use the SMIL elements) an Ecore Timer is used. For drawing an Ecore Idler is used, etc.

### Window abstraction:

You can use any Egüeb document implementation along with the new Efl Egüeb Window type. With that you can easily create a window for drawing any Egüeb document. For example:  

```
Efl_Egueb_Window *w;  
Egueb_Dom_Node *doc = NULL;  
Enesim_Stream *s;  
  
efl_egueb_init();  
/* Load the file */  
  
s = enesim_stream_file_new("some.svg" "rb");  
/* Parse it */  
egueb_dom_parser_parse(s, &doc);  
enesim_stream_unref(s);  
  
/* Create the new window */  
w = efl_egueb_window_auto_new(doc, 0, 0, width, height);  
ecore_main_loop_begin();  
efl_egueb_window_free(w);  
efl_egueb_shutdown();  
```
  
Will show a window with the contents of the SVG file drawn and you can interact with it in a similar way to what Ecore Evas abstraction does.

### Smart Object:

Along with the window abstraction, there is also an Evas Smart object. With it you can embed a any Egüeb Document into an Evas scene. For example:

```
Evas_Object *o;  
Evas *evas;  
  
o = efl_egueb_smart_new(evas);  
efl_egueb_smart_file_set(o, "some.svg");  
evas_object_move(o, 0, 0);  
evas_object_resize(o, 320, 320);  
evas_object_show(o);  
```  

### Edje external object:

The last abstraction provided on Efl Egüeb is an Edje external object to easily include an Egüeb Document into an edje scene.  
For example:  
  
``` 
collections {  
  group { name: "main";  
    externals {  
      external: "egueb";  
     }  
  
     parts {  
       part { name: "anim_svg_example";  
         type: EXTERNAL;  
         source: "egueb";  
         description { state: "default" 0.0;  
           params {  
             string: "file" "some.svg";  
           }  
         }  
       }  
     }  
   }  
}
```
