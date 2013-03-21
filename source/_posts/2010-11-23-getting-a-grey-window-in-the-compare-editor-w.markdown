---
layout: post
title: "Getting a grey window in the compare editor with Eclipse Helios (w/PDT)"
date: 2010/11/23 02:58:00 -0800
comments: false
external-url:
categories:
---


This is a very annoying bug (it really surprises me it is not already patched 
in the main update site), that makes the compare editor not work.

The solution is pretty simple, though, just add [http://download.eclipse.org/tools/pdt/updates/2.2/milestones][1] 
as a software source and update PDT to get rid of the problem.

You can find detailed info at [StackOverflow][2] and [Eclipse Bugs][3]



[1]: http://download.eclipse.org/tools/pdt/updates/2.2/milestones
[2]: http://stackoverflow.com/questions/4230865/eclipse-problem-with-subclipse
[3]: https://bugs.eclipse.org/bugs/show_bug.cgi?id=326194