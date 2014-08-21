---
layout: post
title: "Fluhsing only desired entities with Doctrine"
date: 2013/10/10 15:45:00 +0100
comments: true
external-url:
categories: [Doctrine, EntityManager, flush]
---

Sometimes, you may be working with several entities at the same time. If
this entities are managed by Doctrine, you may find yourself in the
situation where you want to flush only some of them. If you want to do
so, you can pass an array of entities to the flush(), so it only affects
the entities you explicitly pass to the function.

This is very useful to avoid side-effects in some instances.