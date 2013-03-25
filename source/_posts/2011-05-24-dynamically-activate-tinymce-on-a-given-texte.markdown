---
layout: post
title: "Dynamically activate tinyMCE on a given textarea."
date: 2011/05/24 02:05:00 -0700
comments: true
external-url:
categories: [tinyMCE, JavaScript]
---


If you are adding textareas dynamically and wish to enable tinyMCE on them, 
you just have to add this on the javascript function that adds said textarea. 

  

`tinyMCE.execCommand('mceAddControl',false, id_of_addedtextarea);`

Where 'id_of_addedtextarea' is what its name implies ;)

More detailed and better info here: [http://blog.dileno.com/archive/201102/adding-tinymce-editor-dynamically-and-get-its-value/][1] 



[1]: http://blog.dileno.com/archive/201102/adding-tinymce-editor-dynamically-and-get-its-value/