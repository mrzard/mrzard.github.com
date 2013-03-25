---
layout: post
title: "Easy VirtualBox setup between Host, Guest and other networks"
date: 2010/09/30 00:16:00 -0700
comments: true
external-url:
categories: [VirtualBox]
---


At work, we use [VirtualBox][1] as our development box. Yesterday due to the 
strike, I worked from home, and as I grew tired of changing network settings 
to make my VirtualBox installation accessible, I gathered some info and found 
a perfect solution.

First I created a Network adapter that used NAT. In most configurations that 
will make your Virtual Machine have access 'to the outside world' (provided 
your host machine has access).

Then I created another connection using the host-only adapter. This ensures 
you'll have host to guest and guest to host connection no matter where you 
are. For this connection, you'll have to assign an static IP with address mask 
255.255.255.0 and no default gateway on your host machine, then configure your 
adapter in the guest with an IP in the same range, also with no default gateway. 

With this you can access your guest machine using the IP in the range of the 
host-only adapter, while the guest machine will be able to access anything 
available to the host machine via the NAT connection.

Then if you need to have your guest machine available in other networks, you 
just have to enable another adapter and configure it for the network in question. 

With this configuration I now can plug my development machine (host and guest) 
at home or at the office and just work with no further configuring.



[1]: http://www.virtualbox.org/