---
layout: post
title: "Customize Form Prototype for Collections in Symfony2"
date: 2013/10/30 15:45:00 +0100
comments: true
external-url:
categories: [Symfony2, collections, forms, prototype]
---


When working with complex forms, sometimes you will be in need of
creating a collection field type to manage relations. When this is the
case, you may find yourself in the need of tweaking how the ‘add’ form
shows.

It’s pretty simple. In twig the protoype can be found under
form.collection.vars.prototype and can be used as a regular form (i.e.
if your form.collection member form has a ‘name’, it will also be
available in form.collection.vars.protoype.name).

With this information now you can create a twig that recieves an ‘item’,
which can be either a form.collection member or a prototype, and it will
be rendered the same.

Finally, wherever you hold the collection html, you will have to output
something like this:

{% codeblock %}
{% raw %}
	data-prototype="{% filter escape %}{% include 'prototype.twig' with { 'item': form.collection.vars.prototype } %}{% endfilter %}"
{% endraw %}
{% endcodeblock %}

And your `prototype.twig` should look like

{% codeblock %}
{% raw %}
	{{ form_row(item.field0) }}
	{{ form_row(item.field1) }}
	{{ form_row(item.field2) }}
{% endraw %}
{% endcodeblock %}

This way, you will have access to the prototype as if it were a regular
form, and you can apply all the customization you want (you can user
form_widget and the other functions, or access the vars directly, etc...)

Creating the helper twig is optional though, but handy because you have
to use the escape filter to the twig so you can put it in the correct
data-attribute.
