---
layout: post
title: "Generate CSRF token programatically in Symfony 2"
date: 2012/08/08 07:28:29 -0700
comments: true
external-url:
categories: [Symfony2, PHP, programming]
---


If you find yourself in the need of generating a CSRF token for a 'built' Request 
or something in that fashion, you can do it rather easily:

  

	$csrfProvider = $this->container->get('form.csrf_provider'); $csrfToken = $csrfProvider->generateCsrfToken('unknown'); 
	

_'unknown'_ is the default 'intention' of CSRF tokens in Symfony2, change 'unknown' 
for the correct intention if you are using that option.

 



