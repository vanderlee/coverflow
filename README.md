jQuery Coverflow
================
Version 1.2.0

Copyright &copy; 2013-2015 Martijn van der Lee (http://martijn.vanderlee.com).
MIT Open Source license applies.

Yet another jQuery Coverflow widget.

Features
--------
*	Separate CSS
*	Keyboard interaction using the cursor keys, Home, End, Page Up and Page Down.
*	Click on a picture to move it to focus.
*	Uses CSS3 transformations if supported by browser, otherwise gracefully degrades.
*	Events for changing the focus, selecting and confirming (clicking on the picture in focus).
*	Animation easing and duration.
*	Separate CSS styles for the selected, innermost and outermost styles, all smoothly transitioning.
*	Support for your own transitioning code, should you want to use weird CSS tricks such as CSS3 filters.
*	Builtin mousewheel support.
*	Optional support for complex CSS transitions using interpolate plugin.
	Included with Coverflow.
	Available separately from https://github.com/vanderlee/interpolate.
*	Optional support for reflections (need to enable manually).
	Use Christophe Beyls' Reflections.js plugin, available from http://www.digitalia.be/software/reflectionjs-for-jquery and included with Coverflow.
*	Optional support for touch swipe gestures.
	Use Matt Bryson's TouchSwipe plugin, available from https://github.com/mattbryson/TouchSwipe-Jquery-Plugin and included with Coverflow.

p.s. All the plugins optionally supported are MIT licensed, so as safe to use as the Coverflow plugin itself.

Download & Install
------------------
Install with bower using `bower install coverflow`.

jQuery v1.8.0 or higher required.
jQuery v1.7.x also works, but without the ability to click on covers to select.

jQueryUI v1.9.0 or higher required.

Current version: https://github.com/vanderlee/coverflow/archive/master.zip

Sourcecode on Github: https://github.com/vanderlee/coverflow

Quick start
-----------
Here's a short code fragment, demonstrating how to use coverflow at it's most
basic level.

There are many more options to tailor it to your needs.

	<div class="coverflow">
		<div class="cover">A</div>
		<div class="cover">B</div>
		...
		<div class="cover">Y</div>
		<div class="cover">Z</div>
	</div>

	<script>
		$(function() {
			$('.coverflow').coverflow();
		});
	</script>

Documentation
=============
`.coverflow(options)`
---------------------
Create one or more coverflows or access an existing coverflow.

Coverflow uses the concepts of "selected", "inner" and "outer" covers. There is
exactly one selected cover; the one in the middle that is visible as the
current (or "selected") cover. The inner cover are the ones closest to the
selected cover on either side. Outer covers are the ones at the very edges of
the visible field. There may be covers beyond the outer covers, but they will
not be visible.

Options
-------
### **density** (function, default: `1`)
@todo

### **duration** (integer/string, default: `"normal"`)
The speed of animation. Use one of the standard constants "slow", "normal",
"fast" or an integer for time in milliseconds.

### **easing** (string, default: `undefined`)
Define an easing method for scrolling. If none is specified, "swing" easing
is used by default.

### **enableKeyboard** (boolean, default: `true`)
Set to false to disable keyboard interaction. Can be enabled/disabled using the
`option` and `options` method.

### **enableClick** (boolean, default: `true`)
Set to false to disable mouse button (and touch tap) interaction. Can be
enabled/disabled using the `option` and `options` method.

### **enableWheel** (boolean, default: `true`)
Set to false to disable mouse wheel interaction. Can be enabled/disabled using 
the `option` and `options` method.

### **index** (string, integer: `0`)
The initial selected index.

### **innerAngle** (float, integer: `-75`)
An angle, in degrees, of the inner covers. Negative values indicate the
covers are turned inwards (towards the center). Positive values indicate
the covers will be turned outwards.

### **innerCss** (object, default: `undefined`)
A plain object containing CSS properties of the inner covers. Leave
undefined if you don't need any CSS changes. You can specify all (and only)
the CSS properties supported by jQuery/jQueryUI.

### **innerOffset** (float, default: `100/3`)
@todo

### **innerScale** (float, integer: `0.75`)
@todo

### **outerAngle** (float, integer: `-30`)
An angle, in degrees, of the outer covers. Negative values indicate the
covers are turned inwards (towards the center). Positive values indicate
the covers will be turned outwards.

### **outerCss** (object, default: `undefined`)
A plain object containing CSS properties of the outer covers. Leave
undefined if you don't need any CSS changes. You can specify all (and only)
the CSS properties supported by jQuery/jQueryUI.

### **outerScale** (float, integer: `0.25`)
@todo

### **selectedCss** (object, default: `undefined`)
A plain object containing CSS properties of the selected cover. Leave
undefined if you don't need any CSS changes. You can specify all (and only)
the CSS properties supported by jQuery/jQueryUI.

### **visible** (string/float, default: `"density"`)
@todo

### **width** (integer, default: `undefined`)
@todo

Methods
-------
### **cover**
Get the currently selected cover as a jQuery object.

### **index**
Get or set the current index. If no value is provided, the current index is
returned. Otherwise, the index will be set to the provided value.

### **refresh**
Redraw the covers. You shouldn't ever need to do this unless you are adding
or removing covers or changing the covers yourself.

Events
------
### **change**
Triggered whenever the current cover index changes. This includes initially and
for each cover passed by when skipping past multiple covers. Change triggers as
soon as the cover is on front; this may be before or after it's animation is
completed (but only once!).

Callback: `function(event, cover, index)`

### **confirm**
Triggered when the user clicks on the current cover.

Callback: `function(event, cover, index)`

`event.originalEvent.target` contains the DOM element that was clicked to
trigger the confirm event.

### **select**
Triggered whenever a cover is selected. This includes initially. In contrast to
the `change` event, `select` only triggers once after the requested cover
position has been reached.

Callback: `function(event, cover, index)`

### **animateStep**
Triggered for every animation frame. Use this event to customize how the
animation looks if the default options provide insufficient control.

Callback: `function(event, cover, offset, isVisible, isMiddle, sin, cos)`

### **animateComplete**
Triggered after the animation has stopped. A final `animateStep` will
be triggered after animation as well, so you don't need to use the
`animateComplete` event for normal animation frames.

Callback: `function(event, cover, offset, isVisible, isMiddle, sin, cos)`