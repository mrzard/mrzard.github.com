---
layout: post
title: "Setting Shipping Costs For A Whole Third Party Shopping Cart With Paypal"
date: 2010/09/21 07:26:00 -0700
comments: true
external-url:
categories: PayPal
---


Today I found that paypal just ignores the 'shipping' parameter when dealing 
with a third party cart.

If you find yourself with this problem the [workaround posted on the X forums 
by PayPal themselves][1] is to calculate shipping costs on your side and send 
them using the 'handling_cart' parameter.

It's just dumb to have to use a parameter that is not referred to shipping 
to include the shipping, but until this is resolved, this workaround should 
do the trick. At least if worked for me!

**UPDATE: **Looks like it's not just a workaround, but the expected behaviour, it's just that the documentation is poorly written, leading the developer to think that 'shipping' will apply to a cart, when in fact it will not, everything is expected to be sent using the 'handling_cart' param**  
**



[1]: https://www.x.com/thread/39507