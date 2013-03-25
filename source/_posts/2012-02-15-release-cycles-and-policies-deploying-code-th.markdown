---
layout: post
title: "Release cycles and policies, deploying code thoughts."
date: 2012/02/15 12:17:00 -0800
comments: false
external-url:
categories: [programming]
---


In my programming experience I have worked with different ways of handling 
releases. From the old easy FTP access to other cool stuff like [phing][1]. 

What I have learned is that it does not really matter which tools you use, 
and is pretty much contained in the next points.

0 - Prepare for the release. Write a 'script' of what code has been changed/added 
and what tests it must pass (unit, integration, user...). Iterate until all 
tests have passed. Then move the release to your staging server. Always have 
100% awareness of what is going into the release.

1 - Have a proper staging server(s). This allows for good testing, and reduces 
(hopefully eliminates) the necessity to double check stuff in the live server(s). 

3 - The release has to work. Test everything, then test it again. Then release. 
And go to 4.

4 - Shit happens. The relese does not always work. This is pretty common, specially 
with large codebases, multiple programmers and code merging (SVN I'm looking 
at you). Or discrepancies between your live servers and your testing servers. 
Or simply someone forgot to run a test.

5 - Your release system must work for you, not against you. It's fine to have 
a release date / system, but fear not of changing it to fit your needs. This 
leads us to the next point.

6 - Make it that the release system is quick and can be fired anytime. You 
never know when you're going to need an emergency fix. Make it easy to fix 
mistakes. Also make it painful to make them. You don't want developers feeling 
confident they can release a half cooked solution and fix it later. I must 
confess though that I prefer to release and fix than to never release.

7 - Use of tools like phing can help you a lot automating some boring stuff, 
but again make deploying a simple procedure that has no bottlenecks and allows 
you to eliminate any serious enough bug or mistake in a heartbeat.

8 - Do not fire your lean, quick release system for everything. That CSS fix 
can wait until the next release.



[1]: 