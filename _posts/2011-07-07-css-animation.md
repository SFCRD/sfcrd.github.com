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

## Transform

Using transform, boxes can be scaled, rotated, skewed and translated.

You can chain together operations to apply multiple transforms at once to an object (e.g., if you want to both scale and rotate a box).

The supported primitives are:

- **scale**, **scaleX**, **scaleY**
- **rotate**
- **translate**, **translateX**, **translateY**
- **skew**, **skewX**, **skewY**
- **matrix** - Specify a full affine transform matrix. This function takes six values. The last two values are the tx and ty, and they can be lengths or percentages.
- ****-webkit-transform-origin** - Specify the origin of the transform.

{% highlight css %}
element {
  -webkit-transform: translate(30px,0px);
}
element {
  -webkit-transition: all 1s ease-in-out;
  -webkit-transform: scaleX(2) rotate(10deg);
}
{% endhighlight %}

<style type="text/css">
#example-two:hover {
	-webkit-transform: translate(30px, 0px);
	-moz-transform: translate(30px, 0px);
	-o-transform: translate(30px, 0px);
	-ms-transform: translate(30px, 0px);
	transform: translate(30px, 0px);
}
</style>
<div id="example-two" class="example">
	-webkit-transform: translate(30px,0px)
</div>

<style type="text/css">
#example-three {
	-webkit-transition: all 1s ease-in-out 0s;
	-moz-transition: all 1s ease-in-out 0s;
	-o-transition: all 1s ease-in-out 0s;
	-ms-transition: all 1s ease-in-out 0s;
	transition: all 1s ease-in-out 0s;
}
#example-three:hover {
	-webkit-transform: scaleX(2) rotate(10deg);
  -moz-transform: scaleX(2) rotate(10deg);
  -o-transform: scaleX(2) rotate(10deg);
  -ms-transform: scaleX(2) rotate(10deg);
  transform: scaleX(2) rotate(10deg);
}
</style>
<div id="example-three" class="example">
	-webkit-transform: scaleX(2) rotate(10deg)
</div>

## 3D Transform

WebKit on MacOSX has support for CSS 3D transforms, which allow you to position elements on the page in three-dimensional space using CSS.

Now Chrome supports it too :D

Read about it more in detail here: [3D Transform](http://www.webkit.org/blog/386/3d-transforms/)

## -webkit-animation

WebKit supports explicit animations in CSS. As a counterpart to transitions, animations provide a way to declare repeating animated effects, with keyframes, completely in CSS.

Specifying animations is easy. You first describe the animation effect using the **@-webkit-keyframes** rule.

The animation engine will smoothly interpolate style between the keyframes.

-webkit-animation is specified using the following properties:

- **animation-name** - Specifies the name of an animation
- **animation-duration**
- **animation-timing-function**
- **animation-delay**
- **animation-iteration-count**
- **animation-fill-mode** - Specifies whether the effects of an animation are apparent before the animation starts and after it ends, e.g., forwards/backwards.
- **animation-direction** - Determines whether the animation should play in reverse on alternate iterations
- **animation-play-state** - Determines whether the animation is running or paused
- **animation** - A shorthand for all properties.The order should be: name, duration, timing_function, delay, iteration_count, direction [, ... ]

{% highlight css %}
@-webkit-keyframes pulse {
  0% {
    background-color: red;
    opacity: 1.0;
    -webkit-transform: scale(1.0) rotate(0deg);
  }
  50% {
    background-color: blue;
    opacity: 0.75;
    -webkit-transform: scale(1.1) rotate(-5deg);
  }
  100% {
    background-color: red;
    opacity: 1.0;
    -webkit-transform: scale(1.0) rotate(0deg);
  }
}
element {
  -webkit-animation-name: pulse;
  -webkit-animation-duration: 4s;
  -webkit-animation-timing-function: ease-in-out;
  -webkit-animation-iteration-count: infinite;
}
element {
  -webkit-animation: pulse 4s ease-in-out infinite;
}
{% endhighlight %}

<style type="text/css">
@-webkit-keyframes pulse {
  0% {
    background-color: red;
    opacity: 1.0;
    -webkit-transform: scale(1) rotate(0deg);
  }

  50% {
    background-color: blue;
    opacity: 0.75;
    -webkit-transform: scale(1.1) rotate(-5deg);
  }

  100% {
    background-color: red;
    opacity: 1.0;
    -webkit-transform: scale(1) rotate(0deg);
  }
}
#example-four {
	-webkit-animation: pulse 4s ease-in-out infinite;
	color: white;
	background: red;
}
</style>
<div id="example-four" class="example">
	This paragraph should pulse. Pulsing is the new blink. You heard it here first. (Only supports for webkit based browsers)
</div>