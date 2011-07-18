---
layout: post
title: "CSS Animation"
excerpt: "An introduction to rich animation in pure CSS3."

---

<style type="text/css">
.example {
	padding: 10px;
	background: #FF6B6B;
	color: #FFF;
	display: inline-block;
}
</style>

# CSS Animation

An introduction to rich animation in pure CSS3.

## What's CSS Animation?

CSS animation is used to make sequences between one property value element to the next; 
it's like tweening in flash, but runs seamlessly into a native browser via CCS.

![flash timeline](http://ne-zu.com/work/crd/CSSAnimation/assets/sec1_flash.png "Flash Timeline")

## Transition

The simplest kind of animation is called a **transition**.

Transitions are specified using the following properties:

- **transition-property** - What property should animate, e.g., opacity.
- **transition-duration** - How long the transition should last.
- **transition-timing-function** - The timing function for the transition (e.g., linear vs. ease-in vs. a custom cubic bezier function).
- **transition-delay** - Defines when the transition starts.
- **transition** - A shorthand for all properties. The order should be: property, duration, timing_function, delay [, ...]

{% highlight css %}
element {
  -webkit-transition: opacity 1s linear 2s;
}
element {
  -webkit-transition-property: opacity;
  -webkit-transition-duration: 1s;
  -webkittransition-timing-function: linear;
  -webkit-transition-delay: 2s;
}
element:hover {
  opacity: 0;
}
{% endhighlight %}

<style type="text/css">
#example-one {
  -webkit-transition: opacity 1s linear 2s;
  -moz-transition: opacity 1s linear 2s;
  -o-transition: opacity 1s linear 2s;
  -ms-transition: opacity 1s linear 2s;
  transition: opacity 1s linear 2s;
}
#example-one:hover {
	opacity: 0;
}
</style>
<div id="example-one" class="example">
	This div will fade out for 2 seconds when hovered over.
</div>

## Vendor Prefixes

There is a lot of duplication due to vendor prefixes for each browser.

[SASS](http://sass-lang.com/) allows you to define mixins to avoid repetitive code.

(It'll be only -webkit prefixes in the code samples from now on.)

{% highlight css %}
element {
  -webkit-transition: all 1s ease-in-out;
  -moz-transition: all 1s ease-in-out;
  -o-transition: all 1s ease-in-out;
  -ms-transition: all 1s ease-in-out;
  transition: all 1s ease-in-out;
}
{% endhighlight %}