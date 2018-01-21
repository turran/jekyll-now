---
layout: post
title: Linux Kernel, User space drivers and interoperability
date: '2008-02-13T10:12:00.000+01:00'
author: turran
tags: 
modified_time: '2008-11-20T10:13:33.142+01:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-7850729494475976012
blogger_orig_url: http://www.turran.org/2008/02/linux-kernel-user-space-drivers-and.html
---

On Linux version 2.6.23 (or .22, can't recall right now) the UIO (User space Input Output) API was included. It brought up several discussions, quoting Andrew Morton:

_"I'm a bit uncertain about the whole UIO idea, really. I have this vague feeling that we'd prefer to encourage people to move device drivers into GPL'ed kernel rather than encouraging them to do closed-source userspace implementations which will probably end up being slower, less reliable and unavailable on various architectures, distros, etc"_

Well, on the internet are several references about user space drivers, reliability of in-kernel drivers, etc ([here](http://lwn.net/Articles/66829/), [here](http://lwn.net/Articles/232575/) and [here](http://lwn.net/Articles/66829/)), so I won't go that way. But I'd like to express my excitement about this new API because it will open several alternatives specially on the interoperability of different Open Source Kernels (Linux, *BSD, etc) on the driver side. It's interesting that nobody has talked about this, having specific UIO implementations for each kernel and a common base code on the user space side (like a library) will in fact join efforts between all of us.
