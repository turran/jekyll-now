---
layout: post
title: Metadata Filesystem
date: '2010-08-03T12:23:00.005+02:00'
author: turran
tags:
- metadatafs
modified_time: '2010-08-03T14:13:19.279+02:00'
blogger_id: tag:blogger.com,1999:blog-4245000852706595379.post-7257217993524190912
blogger_orig_url: http://www.turran.org/2010/08/metadata-filesystem.html
---

It's been a while since my last post. But now it is time to announce something new I'm doing on my spare time (which is almost none this weeks/months). Basically it is a FUSE filesystem that generates a directory tree based on the mp3 (or ogg, flac, whatever) metadata fields.  
  
Basically once you have mounted your mp3 directory, you'll get something like this:  
/Album  
/Artist  
/Files  
/Title  
/Genre  
  
It allows you to browse your music collection with the common file operations (open(), readdir(), etc). For now it only has read access, i.e you can only browse, list and search, but there's a TODO item to allow write operations, that is, a way to write the metadata information based on the file operations you do on the files, like renaming the Album's name.  
  
You can find more information in [the google code project](http://code.google.com/p/metadatafs/)
