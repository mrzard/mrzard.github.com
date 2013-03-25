---
layout: post
title: "Drag and drop interaction made easy with jQuery (and jQuery UI)"
date: 2011/04/12 01:18:00 -0700
comments: true
external-url:
categories: [jQuery, JavaScript]
---


Last week at work I had to make a drag-and-drop configurable homepage, where 
individual news items had to had the ability to be moved and arranged in a 
grid which represented the available placeholders on the homepage.

My work was made MUCH easier by the [draggable][1] and [droppable][2] plugins 
in jQuery UI. I just had to add a class which I binded the draggable plugin 
to to the news items and then add another class to the placeholders which I 
binded to the droppable plugin.

In case it's of help for somebody, here's a quick 'skeleton' on top of which 
you can code the drag&drop interactions you want.

  

	var draggable_options = { helper: 'clone', /* makes the item 'move' a copy 
	of itself rather than 'leave' the original area */ revert: 'invalid', /* makes 
	the item return to its original position if not dropped in a 'droppable' area 
	*/ cursor: 'move' // changes the cursor appearance on hover }; //we give the 
	items the draggable plugin with the options $(".draggable").draggable(draggable_options); 
	$(".droppable").droppable({ drop: function(event, ui) { /* detect where we 
	dropped the draggable element, in my case, the key part was the element's id 
	*/ var dropped_in = $(this).attr('id'); /* here i put '...' in the droppable 
	container's body to inform the user 'something' is happening */ var context 
	= $(this); context.html('...'); var dragged = $(ui.draggable); /* ui.draggable 
	is a reference to the dropped element now you can use all jQuery functions 
	like dragged.attr('id') to get its id, or dragged.html('whatever') to change 
	its innerHTML, etc... */ /* Here comes interaction, the removal of '...' and 
	display of the action results */ } });



[1]: http://jqueryui.com/demos/draggable/
[2]: http://jqueryui.com/demos/droppable/