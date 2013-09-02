jQuery Coverflow
================
Version v1.0.0

Copyright &copy; 2013 Martijn van der Lee (http://martijn.vanderlee.com).
MIT Open Source license applies.

Yet another jQuery Coverflow widget.

Features
--------
-	Separate CSS
-	Keyboard interaction using the cursor keys, Home, End, Page Up and Page Down.
-	Click on a picture to move it to focus.
-	Uses CSS3 transformations if supported by browser, otherwise gracefully degrades.
-	Events for changing the focus, selecting and confirming (clicking on the picture in focus).
-	Animation easing and duration.
-	Separate CSS styles for the selected, innermost and outermost styles, all smoothly transitioning.
-	Support for your own transitioning code, should you want to use weird CSS tricks such as CSS3 filters.
-	Optional mousewheel support.
	Simply add Brandon Aaron's mousewheel plugin, available from https://github.com/brandonaaron/jquery-mousewheel and included with Coverflow.
-	Optional support for complex CSS transitions.
	Simply add my own interpolate plugin, included with Coverflow.
-	Optional support for reflections (need to enable manually).
	Simply add Christophe Beyls' Reflections.js plugin, available from http://www.digitalia.be/software/reflectionjs-for-jquery and included with Coverflow.
-	Optional support for touch swipe gestures.
	Simply add Matt Bryson's TouchSwipe plugin, available from https://github.com/mattbryson/TouchSwipe-Jquery-Plugin and included with Coverflow.

p.s. All the plugins optionally supported are MIT licensed, so as safe to use as the Coverflow plugin itself.

Download
--------
jQuery v1.7.0 or higher required.

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

Future
------
-	Cyclic scrolling (optional)
-	Cyclic display (optional)
-	Direct jQueryUI slider hookup
-	Support for transformie
-	Better automatic height calculation
-	Flat view if sufficient space (optional)
-	Non-linear swipe
-	Optional motion swipe
-	Lower jQuery/jQueryUI requirements

Documentation
=============
'.coverflow(options)'
-----------------------
Create one or more coverflows or access an existing coverflow.

### Options

-	**animateComplete** (function, default: `undefined`)

>	Todo
	function(cover, offset, isVisible, isMiddle, sine, cosine)
			
-	**animateStep** (function, default: `undefined`)

>	Todo
	function(cover, offset, isVisible, isMiddle, sine, cosine)

-	**density** (function, default: `1`)

>	Todo

-	**duration** (integer/string, default: `"normal"`)

>	Todo

-	**easing** (string, default: `undefined`)

>	Todo

-	**index** (string, integer: `0`)

>	Todo

-	**innerAngle** (float, integer: `-75`)

>	Todo

-	**innerCss** (object, default: `undefined`)

>	Todo

-	**innerOffset** (float, default: `100/3`)

>	Todo

-	**innerScale** (float, integer: `0.75`)

>	Todo

-	**outerAngle** (float, integer: `-30`)

>	Todo

-	**outerCss** (object, default: `undefined`)

>	Todo

-	**outerScale** (float, integer: `0.25`)

>	Todo

-	**selectedCss** (object, default: `undefined`)

>	Todo

-	**visible** (string/float, default: `"density"`)

>	Todo

-	**width** (integer, default: `undefined`)

>	Todo

### Methods

-	**cover**

>	Get the currently selected cover jQuery object.

-	**index**

>	Get the current index or set the index.

-	**refresh**

>	Redraw the covers. You shouldn't ever need to do this unless you are adding
	or removing covers or changing the covers yourself.

### Events

-	**change**

>	Todo.
	function(cover, index)

-	**confirm**

>	Todo
	function(cover, index)

-	**select**

>	Todo
	function(cover, index)
