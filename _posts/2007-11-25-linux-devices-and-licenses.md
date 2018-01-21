---
layout: post
title: Linux, Devices and Licenses
date: '2007-11-25T10:14:00.000+01:00'
author: turran
tags: 
modified_time: '2008-11-20T10:17:48.389+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-8626643032233609237
blogger_orig_url: http://www.turran.org/2007/11/linux-devices-and-licenses.html
---

Nowadays there are lots of devices that include Linux and other free libraries or applications on it. With the GPL license you are supposed to liberate the source code in case you have modified it, which is really great but suffers in a key point, **merging**.

I've been working with several embedded devices for almost two years now and currently I'm looking for a multimedia development platform as a base for my master paper. In every development I've used GNU/Linux as the operating system and most of the times the manufacturer ships a SDK with it. In case you have a Linux based device and the company releases the source of the modified code you are a lucky guy because you can download that source and compile/modify it yourself, but what happens next? the truth is: **nothing**.

Nothing will happen, because that code will never go to mainstream, most of the times the modified code just don't follow the coding standard, in other cases the code just do what it needs not using the supposed API's or standard interfaces and in other cases because there won't be anyone to maintain it, because there's no **documentation**.

This situation really sucks, so at the end it's not about licensing some code its the lack of companies releasing the documentation. With the license you force to release (GPL) or not release (BSD) the source code but it just won't matter in the long term and in the integration.

On multimedia embedded devices it is really common (TI, Freescale, etc) to find the documentation for everything but the multimedia functionality, this devices can be ported to Linux (most of them are) but are really usefulness for the use cases they were designed: multimedia!. This gets worst when the device has companion devices like DSPs or FPGAs, the development environment for Linux is really a shame.

I hope some day this will change, If someone has some information on a company with a more open mind please let me know. =)
