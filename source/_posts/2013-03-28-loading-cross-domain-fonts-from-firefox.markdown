---
layout: post
title: "Loading Cross-domain Fonts From Firefox"
date: 2013/03/28 15:45:00 +0100
comments: true
external-url:
categories: [HTTP, fonts, headers, webfonts, nginx, firefox]
---

When requiring a font from an external CSS file (assets domain, CDN,
etc), you may see that Firefox refuses to display the font. This is
because Firefox, by default, disables cross-domain fonts. To solve this
you have to add a header to the response with the font file. The header
is `Access-Control-Allow-Origin: *`

In a typical `nginx` setup, this is achieved with this snippet:

nginx add header
``` plain nginx add header
location ~* \.(eot|ttf|woff)$ {
	add_header Access-Control-Allow-Origin *;
}   
```

Once you have that in place, the fonts will be loaded correctly from
Firefox.
