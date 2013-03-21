---
layout: post
title: "Failed to connect to socket /com/ubuntu/upstart ? Upstart Jobs Cannot be Run on chroot"
date: 2011/02/01 04:01:00 -0800
comments: false
external-url:
categories:
---


Thanks to [http://www.ashang.org/2010/10/unable-to-connect-to-upstart.html][1] 
I was finally able to upgrade my system while chrooted.

Being on chroot will cause some packages to fail when they are upgrading. Giving 
us an error message like this one:

start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused  
dpkg: error processing procps (--configure):

You can workaround this limitation by running these commands

$dpkg-divert --local --rename --add /sbin/initctl  
Adding 'local diversion of /sbin/initctl to /sbin/initctl.distrib'  
$ln -s /bin/true /sbin/initctl

Then you can run the upgrade, or do a dpkg --configure -a to upgrade the packages 
that were previously failing.



[1]: http://www.ashang.org/2010/10/unable-to-connect-to-upstart.html