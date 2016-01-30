jQuery Coverflow
================
Version 1.3.0

Copyright &copy; 2013-2016 Martijn van der Lee (http://martijn.vanderlee.com).
MIT Open Source license applies.

Yet another jQuery Coverflow widget.

Features
--------
*	Keyboard interaction using the cursor keys, Home, End, Page Up and Page Down.
*	Focusable
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
*	Extensive support for CSS styling of the states

p.s. All the plugins optionally supported are MIT licensed, so as safe to use as the Coverflow plugin itself.

Download & Install
------------------
Install with bower using `bower install coverflow`.

jQuery v1.8.0 or higher required.
jQuery v1.7.x also works, but without the ability to click on covers to select.

jQueryUI v1.9.0 or higher required.

Current version: https://github.com/vanderlee/coverflow/archive/master.zip

Sourcecode on Github: https://github.com/vanderlee/coverflow


jQueryUI custom build
---------------------
If you download a custom build of jQueryUI, you need these components:

*	Widget

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

### Focus
Coverflow is focussable. If you do not specify an explicit `tabIndex` attribute
for the Coverflow element, one will be assigned with value `-1`, meaning it
can be focussed using the mouse, but not by pressing the [tab] key.

You can optionally set the `autofocus` attribute on the element, and Coverflow
will detect it and focus itself on page load.

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

### **enableKeyboard** (boolean, default: `"both"`)
By default, Coverflow catches keyboard events both when hovering over it or
when it has focus.
Available options are `"focus"`, `"hover"`, `"both"` and `"focus"`. You can also
use boolean `true` or `false` to completely enable or disable keyboard.
Can be enabled/disabled using the `option` and `options` method.

If you use multiple coverflow components, you should use either `"focus"` or
`"hover"`, otherwise the keyboard will affect multiple Coverflows at once.

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

Extensions/dependencies
=======================
Coverflow is designed to take advantage of a number of separate Javascript
libraries to supply additional features. The download comes with these files
included. If you deploy your code, you may wish to use or exclude these files.

Interpolate
-----------
https://github.com/vanderlee/interpolate

Interpolate is a library for smoothly interpolating CSS by taking advantage of
the builtin jQuery and jQueryUI features. jQuery/jQueryUI offer support to
smoothly animate transitions between two states of a large number of CSS rules
but does not provide an interface to get a single "frame". Interpolate provides
that interface.

If you want to use Coverflow's `innerCss` and `outerCss` features, including
Interpolate will ensure the animations will be smooth.

TouchSwipe-Jquery-Plugin
------------------------
https://github.com/mattbryson/TouchSwipe-Jquery-Plugin

TouchSwipe provides support for touch device input, like swiping the coverflow
sideways. If you include this plug-in (or any plugin providing a compatible
`.swipe()` implementation), Coverflow will detect it and support swiping.

Relection.js
------------
http://www.digitalia.be/software/reflectionjs-for-jquery/

The Reflection.js jQuery plugin provides controlable image reflections
underneath the images. Though Coverflow neither detects nor interacts with this
script, Coverflow is designed to work smoothly with this plugin without any
additional code.
