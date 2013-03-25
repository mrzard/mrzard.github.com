---
layout: post
title: "Cygwin + Rsync error 13 + Windows 7 problems"
date: 2010/09/07 14:30:00 -0700
comments: false
external-url:
categories: [GNU/Linux, Windows 7, cygwin, rsync]
---


If you find yourself getting rsync error 13 when using it on cygwin, check 
the permissions on your source folder. For some reason, out of the box all 
directories have 400 permissions, and if your destination folder needs anything 
higher than that, rsync will fail. Make sure you execute chmod -R 755 on the 
source directory - assuming it's in your cygwin box-.

Also, if chmod fails, make sure you ran cygwin as administrator on your Windows 
machine.

Worked like a charm for me!



