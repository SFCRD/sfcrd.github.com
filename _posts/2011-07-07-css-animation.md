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

## Demo

<style type="text/css">
	img {
		background: #FFF;
		margin: 0;
		padding: 0;
		border: 15px solid #FFF;
	}
</style>
<style type="text/css">
/* line 195, ../sass/screen.scss */
#banner {
  width: 300px;
  height: 250px;
  background: black;
  overflow: hidden;
	position: relative;
}
/* line 200, ../sass/screen.scss */
#banner > div {
  position: absolute;
  background-repeat: no-repeat !important;
}
/* line 204, ../sass/screen.scss */
#banner .logo1 {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 17px;
  margin-top: 59px;
  width: 59px;
  height: 140px;
  background: url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/sprite.png") left top;
}
/* line 211, ../sass/screen.scss */
#banner .red_line {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 94px;
  width: 6px;
  height: 250px;
  background: #ec2427;
	top: 0;
}
/* line 217, ../sass/screen.scss */
#banner .blue_line {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 100px;
  width: 7px;
  height: 250px;
  background: #1dabed;
	top: 0;
}
/* line 223, ../sass/screen.scss */
#banner .guy1 {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 107px;
  width: 193px;
  height: 250px;
  overflow: hidden;
  background: url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guy.jpg") left -380px;
  -webkit-transition: all 3s ease-in-out 0s;
  -moz-transition: all 3s ease-in-out 0s;
  -o-transition: all 3s ease-in-out 0s;
  -ms-transition: all 3s ease-in-out 0s;
  transition: all 3s ease-in-out 0s;
}
/* line 231, ../sass/screen.scss */
#banner .guy2 {
	position: absolute;
  background-repeat: no-repeat !important;
  width: 300px;
  height: 250px;
  background: black url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guy.jpg") left -630px;
  opacity: 0;
  -webkit-transition: all 0.8s ease 3.5s;
  -moz-transition: all 0.8s ease 3.5s;
  -o-transition: all 0.8s ease 3.5s;
  -ms-transition: all 0.8s ease 3.5s;
  transition: all 0.8s ease 3.5s;
}
/* line 238, ../sass/screen.scss */
#banner .title {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 151px;
  margin-top: 20px;
  width: 149px;
  height: 81px;
  background: url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/sprite.png") 150px bottom;
  -webkit-transition: all 0.8s ease-in-out 4s;
  -moz-transition: all 0.8s ease-in-out 4s;
  -o-transition: all 0.8s ease-in-out 4s;
  -ms-transition: all 0.8s ease-in-out 4s;
  transition: all 0.8s ease-in-out 4s;
}
/* line 246, ../sass/screen.scss */
#banner .text {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 153px;
  margin-top: 115px;
  width: 136px;
  height: 28px;
  background: url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/sprite.png") left -180px;
  opacity: 0;
  -webkit-transition: all 0.8s ease 5.5s;
  -moz-transition: all 0.8s ease 5.5s;
  -o-transition: all 0.8s ease 5.5s;
  -ms-transition: all 0.8s ease 5.5s;
  transition: all 0.8s ease 5.5s;
}
/* line 255, ../sass/screen.scss */
#banner .logo2 {
	position: absolute;
  background-repeat: no-repeat !important;
  margin-left: 185px;
  margin-top: 179px;
  width: 101px;
  height: 40px;
  background: url("http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/sprite.png") left -140px;
  opacity: 0;
  -webkit-transition: all 0.8s ease 6.2s;
  -moz-transition: all 0.8s ease 6.2s;
  -o-transition: all 0.8s ease 6.2s;
  -ms-transition: all 0.8s ease 6.2s;
  transition: all 0.8s ease 6.2s;
}
/* line 266, ../sass/screen.scss */
#banner.def .guy2 {
  opacity: 1;
}
/* line 269, ../sass/screen.scss */
#banner.def .title {
  background-position: left bottom;
}
/* line 272, ../sass/screen.scss */
#banner.def .text {
  opacity: 1;
}
/* line 275, ../sass/screen.scss */
#banner.def .logo2 {
  opacity: 1;
}


/* line 378, ../sass/screen.scss */
#banner.show .guy1 {
  background-position: left top;
}
/* line 381, ../sass/screen.scss */
#banner.show .guy2 {
  opacity: 1;
}
/* line 384, ../sass/screen.scss */
#banner.show .title {
  background-position: 0px bottom;
}
/* line 387, ../sass/screen.scss */
#banner.show .text {
  opacity: 1;
}
/* line 390, ../sass/screen.scss */
#banner.show .logo2 {
  opacity: 1;
}
</style>
Here is a example of a banner using Flash vs CSS animation.
Compare below banners using Flash and CSS3.

- [Flash](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/flash/targ_sw_boy_300x250_40_v05.html)
- [HTML](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/html/index.html)
- [Zip](http://ne-zu.com/work/crd/CSSAnimation/banner.zip)

### Preparation

To connect html access as less as possible, assemble each image kind.

**png-8: "sprite.png"**

![image](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/sprite.png)
![dimensions](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guide/sprite_size.png)

**jpg: "guy.jpg"**

![image](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guy.jpg)
![dimensions](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guide/guy_size.png)

### Make a box and add background

**HTML**

{% highlight html %}
<div id="banner"></div>
{% endhighlight %}

**CSS**

{% highlight css %}
#banner {
  width:300px;
  height:250px;
  background:black;
  /*make invisible outside of box*/
  overflow:hidden;
}
{% endhighlight %}

<div id="banner"></div>

### Add logos

**HTML**

{% highlight html %}
<div id="banner">
  <div class="logo1"></div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
/*define all of div under #banner*/
#banner > div {  
  /*make origin left top*/
  position:absolute;
  /*disable background repeat*/
  background-repeat:no-repeat !important;
}
.logo1 {
  margin-left:17px;
  margin-top:59px;
  width:59px;
  height:140px;
  background:url('sprite.png') left top;
}
{% endhighlight %}

<div id="banner">
  <div class="logo1"></div>
</div>

### Add red and blue lines

**HTML**

{% highlight html %}
<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
.red_line{
  margin-left:94px;
  width:6px;
  height:250px;
  background:#ec2427;
}
.blue_line{
  margin-left:100px;
  width:7px;
  height:250px;
  background:#1dabed;
}
{% endhighlight %}

<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
</div>

### Add image moving up (Set up the position to the bottom)

**HTML**

{% highlight html %}
<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
.guy1{
  margin-left:107px;
  width:193px;
  height:250px;
  overflow:hidden;
  background:url('guy.jpg') left -380px;
}
{% endhighlight %}

![image](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guide/guy1.png)

<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
</div>

### Add image for next scene

**HTML**

{% highlight html %}
<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
.guy2{
  width:300px;
  height:250px;
  background:black url('guy.jpg') left -630px;
}
{% endhighlight %}

<div id="banner" class="def">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
</div>

### Add another assets for next scene (title, text and logo)

{% highlight html %}
<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
  <div class="title"></div>
  <div class="text"></div>
  <div class="logo2"></div>
</div>
{% endhighlight %}

**CSS**

{% highlight css %}
.title{
  margin-left:151px;
  margin-top:20px;
  width:149px;
  height:81px;
  /*will be reviced this background at next step
    due to the initial position*/
  background:url('sprite.png') left bottom;
}
.text{
  margin-left:153px;
  margin-top:115px;
  width:136px;
  height:28px;
  background:url('sprite.png') left -180px;
}
.logo2{
  margin-left:185px;
  margin-top:179px;
  width:101px;
  height:40px;
  background:url('sprite.png') left -140px;
}
{% endhighlight %}

<div id="banner" class="def">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
  <div class="title"></div>
  <div class="text"></div>
  <div class="logo2"></div>
</div>

### Set up initial attributes of elements for last scene

**CSS**

{% highlight css %}
.guy2{
  opacity:0;
}
.title{
  /*revice this*/
  background:url('sprite.png') 150px bottom;
}
.text{
  opacity:0;
}
.logo2{
  opacity:0;
}
{% endhighlight %}

![image](http://ne-zu.com/work/crd/CSSAnimation/assets/banner/imgs/guide/last.png)

<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
  <div class="title"></div>
  <div class="text"></div>
  <div class="logo2"></div>
</div>

### Set up transition information

**CSS**

{% highlight css %}
.guy1{
  /*moves from bottom to top*/
  -webkit-transition:all 3s ease-in-out;
}
.guy2{
  /*fades in 3.5sec after 
    the first image finishes the animation*/
  -webkit-transition:all 0.8s ease 3.5s;
}
.title{
  /*slides from right to left 4s later*/
  -webkit-transition:all 0.8s ease-in-out 4s;
}
.text{
  /*fade in 5.5s later*/
  -webkit-transition:all 0.8s ease 5.5s;
}
.logo2{
  /*fade in 6.2s later*/
  -webkit-transition:all 0.8s ease 6.2s;
}
{% endhighlight %}

### Set up to start the entire animation

**CSS**

{% highlight css %}
#banner.show .guy1{
  background-position:left top;
}
#banner.show .guy2{
  opacity:1;
}
#banner.show .title{
  background-position:left bottom;
}
#banner.show .text{
  opacity:1;
}
#banner.show .logo2{
  opacity:1;
}
{% endhighlight %}

**Javascript**

{% highlight js %}
var elment = document.getElementById('banner');
elment.className = 'show';
{% endhighlight %}

<script type="text/javascript">
	function playAnimation( )
	{
		$( 'body' ).find( '#banner' ).last( ).toggleClass( 'show' );
	}
</script>

[Click here to call the javascript](javascript:playAnimation())

<div id="banner">
  <div class="logo1"></div>
  <div class="red_line"></div>
  <div class="blue_line"></div>
  <div class="guy1"></div>
  <div class="guy2"></div>
  <div class="title"></div>
  <div class="text"></div>
  <div class="logo2"></div>
</div>

## Reference

**Nike Jordan BCT Low**

(Please reload if an image doesn't show well during the animation.)

- [Flash](http://www.nike.com/jumpman23/BCT/)
- [HTML](http://ne-zu.com/work/crd/nike/index.html)
- [Zip](http://ne-zu.com/work/crd/nike/nike.zip)
 
**Lists of CSS Properties**

- [Webkit](http://css-infos.net/properties/webkit.php/)
- [Mozilla](https://developer.mozilla.org/en/css_reference/mozilla_extensions)
- [Opera](http://www.opera.com/docs/specs/presto29/)
- [IE](http://msdn.microsoft.com/en-us/library/ms531207%28v=vs.85%29.aspx)
