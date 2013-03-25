---
layout: post
title: "Generate a valid Google Premier signature in PHP"
date: 2011/12/12 02:23:00 -0800
comments: true
external-url:
categories: [PHP, programming]
---


Google Premier requires for you to generate a signature over the URL you're 
going to ask for, then send that signature alongside the request. Here is how 
to do it, as there is no PHP example in the [Google Premier URL Signature documentation][1] 

In this code snippet we assume:

* ```$request_url``` has the url that will be using the Google Premier service (for example, Static Maps API). It also already has the client param, sensor param, etc.
* ```$signature_key``` has the key provided to you by Google
* You are running this snippet from an authorized domain
* Props to [ZZ Coder at StackOverflow][2]

  
{% codeblock Generate a valid Google Premier signature lang:phpinline %} 
$url_parts = parse_url($request_url); $signable_part = $url_parts['path'].'?'.$url_parts['query']; 
$decoded_key = base64_decode(strtr($signature_key, '-_', '+/'); 
$url_signature = hash_hmac('sha1', $signable_part, $decoded_key), true); 
$base64signature = strtr(base64_encode($url_signature), '+/', '-_'); 
$signature_param = '&signature='.urlencode($base64signature); 
{% endcodeblock %} 
	

'Strange' things in this snippet:

* Why the strtr()? Because Google uses URL-Safe base64
* Why the true param at the end of hash_hmac? Because we need it the signature to be returned in binary before base64encondig it.

Then you just have to append ```$signature_param``` to your original request (which 
we've assumed is in ```$request_url```) to have a correctly signed Google Premier 
request.



[1]: http://code.google.com/intl/es-ES/apis/maps/documentation/webservices/#URLSigning
[2]: http://stackoverflow.com/questions/3125410/trying-to-digitally-sign-via-hmac-sha1-with-php