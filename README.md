jQuery Coverflow
================
Version v1.0.2

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

Coverflow uses the concepts of "selected", "inner" and "outer" covers. There is
exactly one selected cover; the one in the middle that is visible as the
current (or "selected") cover. The inner cover are the ones closest to the
selected cover on either side. Outer covers are the ones at the very edges of
the visible field. There may be covers beyond the outer covers, but they will
not be visible.

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

>	The speed of animation. Use one of the standard constants "slow", "normal",
	"fast" or an integer for time in milliseconds.

-	**easing** (string, default: `undefined`)

>	Define an easing method for scrolling. If none is specified, "swing" easing
	is used by default.

-	**index** (string, integer: `0`)

>	The initial selected index.

-	**innerAngle** (float, integer: `-75`)

>	An angle, in degrees, of the inner covers. Negative values indicate the
	covers are turned inwards (towards the center). Positive values indicate
	the covers will be turned outwards.

-	**innerCss** (object, default: `undefined`)

>	A plain object containing CSS properties of the inner covers. Leave
	undefined if you don't need any CSS changes. You can specify all (and only)
	the CSS properties supported by jQuery/jQueryUI.

-	**innerOffset** (float, default: `100/3`)

>	Todo

-	**innerScale** (float, integer: `0.75`)

>	Todo

-	**outerAngle** (float, integer: `-30`)

>	An angle, in degrees, of the outer covers. Negative values indicate the
	covers are turned inwards (towards the center). Positive values indicate
	the covers will be turned outwards.

-	**outerCss** (object, default: `undefined`)

>	A plain object containing CSS properties of the outer covers. Leave
	undefined if you don't need any CSS changes. You can specify all (and only)
	the CSS properties supported by jQuery/jQueryUI.

-	**outerScale** (float, integer: `0.25`)

>	Todo

-	**selectedCss** (object, default: `undefined`)

>	A plain object containing CSS properties of the selected cover. Leave
	undefined if you don't need any CSS changes. You can specify all (and only)
	the CSS properties supported by jQuery/jQueryUI.

-	**visible** (string/float, default: `"density"`)

>	Todo

-	**width** (integer, default: `undefined`)

>	Todo

### Methods

-	**cover**

>	Get the currently selected cover as a jQuery object.

-	**index**

>	Get or set the current index. If no value is provided, the current index is
	returned. Otherwise, the index will be set to the provided value.

-	**refresh**

>	Redraw the covers. You shouldn't ever need to do this unless you are adding
	or removing covers or changing the covers yourself.

### Events

-	**change**

>	Triggered whenever the current cover index changes.
	function(cover, index)

-	**confirm**

>	Triggered when the user clicks on the current cover.
	function(cover, index)

-	**select**

>	Triggered whenever a cover is selected. This includes initially.
	function(cover, index)
