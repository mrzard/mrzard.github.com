---
layout: post
title: "Choosing a method to store passwords safely."
date: 2010/12/13 04:30:00 -0800
comments: true
external-url:
categories: [programming, security]
---


As seen in the Gawker/Gizmodo HUGE problem with having their passwords compromised, 
I found a short and excellent post about why using speed-oriented hash functions 
is a bad idea for password encryption.

In a nutshell, MD5, SHA1 and the like are designed to work fast with large 
amounts of data, so they are most useful when calculating data integrity and 
the like, but being fast, they are also easy to attack by brute force.

On the other hand [Bcrypt][1] is 'slow' when compared with other hashing algorithms, 
which makes it strong against brute force attacks. You can find the original 
post here: [http://codahale.com/how-to-safely-store-a-password/][2]

I do not necessarily agree with the 'uselessness' of salting passwords, as 
that makes it harder to find a general pattern to attack ALL of the accounts 
protected by a single password in the system, but I see the point of it not 
being able to prevent or slow brute force attacks.

 



[1]: http://bcrypt.sourceforge.net/
[2]: http://codahale.com/how-to-safely-store-a-password/