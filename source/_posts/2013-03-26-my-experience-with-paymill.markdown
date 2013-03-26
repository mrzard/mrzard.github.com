---
layout: post
title: "My experience with Paymill"
date: 2013/03/26 12:30:00 +0100
comments: true
external-url:
categories: [paymill, PHP, payment]
---

I have been using [Paymill][1] at work for some time now, and this is what I think of it thus far:

PROS:

- Easy to implement. As in dumb-proof easy.
- Commission (2.95% + 0.28€) is reasonable against time of implementation.
- No other fees. No setup fee, no base usage fee, nothing, only their commission.
- They only charge for successful transactions.
* Pays every 7 days, directly to your bank account.
* Removes lots of man-hours in payment-gateway related stuff.
* Removes the need to be PCI-compliant.
* They have [libraries][2] for lots of languages and software packages.

CONS:

* Test mode and live mode do _not_ behave the same in some instances.
 * Have not checked recently, but at a point the test mode worked with a deprecated parameter that resulted in an error if used in live mode.
 * As of now, the amount sent to the bridge and the backend do NOT have to match in test mode for a successful transaction
* Error messages are not that clear, although they have improved in that area.
 * ```40000 RESPONSE_DATA: general problem with data``` or ```40100 RESPONSE_DATA_CARD: problem with creditcard data``` are not very telling. I got a 40100 for a client who did not have 3D-Secure enabled.
* Sometimes they take a long time to answer to support tickets.

BOTTOMLINE:

Paymill is a great tool and I recommend it if you need a payment gateway FAST and cannot / do not want to spend time going PCI-compliant. Only thing that worries me is the discrepancy in behaviour between test mode and live mode which makes it necessary to run some 'live' tests that would not be necessary otherwise. Anyway, once you have detected these little things you can work around them with your own tests and assertions.

[1]: https://www.paymill.com
[2]: https://github.com/Paymill