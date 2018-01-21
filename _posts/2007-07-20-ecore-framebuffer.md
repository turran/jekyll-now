---
layout: post
title: Ecore Framebuffer
date: '2007-07-20T23:05:00.000+02:00'
author: turran
tags:
- efl
modified_time: '2008-11-19T19:03:27.190+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-798922728293300921
blogger_orig_url: http://www.turran.org/2007/07/ecore-framebuffer.html
---

After changing Ecore_Fb to handle Linux Input Device as the main input driver available I decided to go further and implement several ideas I have in mind:  

*   Modules for input devices: Instead of having the input devices exclusive (linux_input or ps2/keyboard/tslib combo), ive made an abstraction to support input "modules" (for now they are just statically linked - its a similar approach to what evas had on the beginning with engines) For now we don't need real modules because the input modules is the only module type we have.
*   More Input Devices: A while ago i coded the linux\_input (event devices) support and place the input devices that were on ecore\_fb (tslib, keyboard, ps2) to support multiple devices (i.e two mice, three keyboards, whatever). I've re-enabled the replaced ones, following the module approach.
*   Support for keyboard layouts: In Ecore_Fb the keyboard layout was hard coded to english layout (ascii values only), with this code we can use different layouts (spanish, french, or your own), it was coded following the keymaps(5) idea. Ive also made a parser for keymaps (the files you have under /usr/share/keymaps/) which will export a c source file for now, i want to also export an eet file, but it wont be done until my eet patch gets in. btw, where's a good place to put this application? under /src/bin of ecore? on tests dir in cvs?
*   Support for not allocating a virtual terminal (in case there's no console attached to the fb) and some code to specify which fb device to use.

The only things that needs to be solved is to append the correct UTF-8 string into an Ecore_Fb event and that't it
