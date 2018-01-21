---
layout: post
title: Openembedded, OpenWrt, Gentoo Portage
date: '2009-02-12T11:11:00.000+01:00'
author: turran
tags:
- openmoko
modified_time: '2009-02-12T12:00:14.195+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-3166185145342541950
blogger_orig_url: http://www.turran.org/2009/02/openembedded-openwrt-gentoo-portage.html
---

The past month i've been trying to setup my build environment to what I am used to have. After working for some years on embedded devices, my usual environment has always have a rootfs on my local box where I copy my developments and then the target device just mounts it's rootfs via NFS. This setup is widely used as it reduces the risk of converting your device into a brick. No need for burning the image or installing packages via some kind of specific intaller, no need for NAND/NOR writing.  
  
Openmoko uses Openembedded and from its name i thought that it will let me have this setup fairly easy. The truth is that my experience with it was null, but looking on the documentation it remind me a lot to what Gentoo/Portage is.  
  
Sadly, my impressions so far are very dissapointing. My goal was something very easy, just give me a rootfs and i'll manage the development, i didnt want to learn another pacakge system, just have a base system and deploy somehow development into it.  
  
My first problem with OE was how to create a base system. So first i followed the OE tutorial, and after setting up my `local.conf` I bitbaked nano. On the beginning it gave me some errors with qemu, basically some include errors:  
  
`  
qemu-native-0.9.1-r7/qemu-0.9.1/linux-user/syscall.c:79:26: warning: linux/dirent.h: No such file or directory  
`  
  
A simple patch fixed it  
  
```
--- linux-user/syscall.c 2009-02-04 22:27:40.000000000 +0100  
+++ linux-user/syscall.new 2009-02-04 22:37:42.000000000 +0100  
@@ -76,7 +76,7 @@  
#include  
#include  
#include  
-#include  
+#include  
#include  
  
#include "qemu.h"  
```
  
I put it on  
  
`packages/qemu/qemu-0.9.1`  
  
and the compilation continued. Then I bitbake xorg-xserver, around 5K package, no problem i'll wait. My first problem arised: Ok, now i have some packages, what now? I still want my rootfs! So I guessed I needed an image, there were around 80 image names, how to know what are those for? what do they will bitbake? On portage i would just do an  
  
`emerge -p <image>`  
  
and it will give me the list of packages the portage system will install and wont list me the already installed, or  
  
`emerge -s <image>`  
  
will give me the description. For me those image names were just cryptic names with no meaning at all. So i give bitbake a chance and run  
  
`bitbake openmoko-base-image`  
  
Now i have to compile and install 5000 packages more. No way thanks.  
  
I thought OE will be an incremental pacakge system, where i have a simple base system, with all the needed directories, device nodes created and just add packages to it. But looks like it isnt. The problem was even worst when i realized that in order to install a pacakge i will need to run a command in the target device ... WTF? im a developer not a user.  
  
Now I know there are ways to create a rootfs on the local box like [Werner's solution](http://svn.openmoko.org/developers/werner/myroot/).  
  
So yesterday i gave OpenWRT a chance, following [this steps](http://wiki.openmoko.org/wiki/OpenWRT). I have to say that it was fairly easy, just two commands and is done. One thing i really appreciated was that the menuconfig allowed me select what output form i want my rootfs to be: jffs2, ext2, and tgz, beside others. Now i have my rootfs and im ready to mount it from my phone via NFS.  
  
Look that im new with OE, for sure that some experts out there handle it correctly and might have a great solution for my case, from a newcomer point of view i was amazed that simple things like search a package, create a rootfs in tgz or list the dependant packages were not easy enough. I just want to develop :)
