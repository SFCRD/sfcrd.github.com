---
layout: post
title: "New-School HTML"
excerpt: "Introduce new-school HTML to people and make it approachable."
authors:
  - Jon Cipriano
  - Jeremy Ruppel
  
---

# New-School HTML

Introduce new-school HTML to people and make it approachable.

## The Current State of the Web

- CSS and HTML were meant to describe **documents**, not **applications**.
- Platforms are fragmented (browsers & devices).
- Standards are evolving (HTML5 & CSS3).
- Movement towards plugin-less applications.
- **All of the above making our jobs difficult.**

## The Problem

- Browsers interpret HTML and CSS differently.
- CSS is static. CSS lacks basic scripting features.
- CSS syntax is repetitive and redundant.
- HTML is static. Complicated javascript or server-side scripting is required to make it dynamic.
- Including HTML as strings in javascript tangles your view with your logic.

## The Solution

- Sass - [http://sass-lang.com/](http://sass-lang.com/)
- Compass - [http://compass-style.org/](http://compass-style.org/)
- Mustache - [http://mustache.github.com/](http://mustache.github.com/)

## What is Sass?

- **S**yntactically **A**wesome **S**tyle **S**heets
- An extension of CSS3, adding nested rules, variables, mixins, selector inheritance, and more. 
- Can be used as a command-line tool or web-framework plugin.
- Gets "*compiled*" to well-formatted, standard CSS.

## Why use Sass?

- Removes repetitive definitions in CSS.

- Reusable "variables" and "includes/partials".

- Can minify your CSS output for you.

- It just makes sense.

## How to use Sass:

- Install it with `gem install sass`

- Create a Sass stylesheet:

{% highlight scss %}
/* style.scss */
#navbar {
  width: 80%;
  height: 23px;
}
{% endhighlight %}

- Run `sass --watch style.scss:style.css`.
  
Sass will watch your file for any changes and kick out a new compiled stylesheet whenever you save.

- That's it!

### SCSS Syntax

- SCSS is a *superset* of CSS3. Every CSS3 stylesheet is also a valid SCSS stylesheet.

- SCSS adds variables, nested styles, functions, math, inheritance, and mixins.

{% highlight scss %}
$blue: #0000F4;
$size: 14px;

@mixin underline {
  text-decoration: underline;
}

#main {
  background-color: $blue;
  p {
    font-size: $size + 2px;
    color: darken( $blue, 30% );
    @include underline;
  }
}
{% endhighlight %}

### Using Sass with existing CSS

If you're on a project that doesn't currently use Sass, you can easily convert existing CSS files to any Sass format.

- The `sass-convert` program allows you to convert files between CSS, SASS, SCSS, and even LESS.

- `sass-convert` will try to guess the format based on input or output extension, but you can specify them with the `--from` and `--to` options.

- Run `sass-convert --help` for all options.

## What is Compass?

- A stylesheet authoring framework that makes your stylesheets and markup easier to build and maintain. With compass, you write your stylesheets in Sass instead of CSS.

- Basically a **ton** of pre-built Sass mixins to help you author your stylesheets.

## Why use Compass?
  
- Comes with a CSS3 mixin set with all browser inconsistencies considered.

- Comes bundled with [Eric Meyer's CSS Reset 2.0](http://meyerweb.com/eric/tools/css/reset/index.html) and [Blueprint](http://www.blueprintcss.org/).

- Provides a bunch of Sass enhancements to help beef up your stylesheets.

## How to use Compass:

- Install it with `gem install compass`

- Create a project with `compass create <myproject>`

- Compass will create some files to get you started.

- Run `compass watch [path/to/project]`

Compass will watch your files for any changes and compile them, just like Sass.

- That's it!

### CSS3 Mixins

Compass has a ton of CSS3 mixins for:

- Background Clip
- Background Origin
- Background Size
- Border Radius
- Box Shadow
- Box Sizing
- CSS3 Pie
- Columns
- Font Face
- Gradient
- Images
- Inline Block
- Opacity
- Text Shadow
- Transform
- Transition

... and more. Ready to go.

#### Box Shadows (handles Webkit, Gecko, and CSS3)

Before:

{% highlight scss %}
.box {
  -moz-box-shadow: #637080 0 -3px 10px 0;
  -webkit-box-shadow: #637080 0 -3px 10px 0;
  -o-box-shadow: #637080 0 -3px 10px 0;
  box-shadow: #637080 0 -3px 10px 0;  
}
{% endhighlight %}

Compass:

{% highlight scss %}
.box {
  @include box-shadow( #637080 0 -3px 10px )
}
{% endhighlight %}

#### Border Radius (handles Webkit, Mozilla, Gecko, IE9, and CSS3)

Before:

{% highlight scss %}
.box {
  -moz-border-radius: 6px;
  -webkit-border-radius: 6px;
  -o-border-radius: 6px;
  -ms-border-radius: 6px;
  -khtml-border-radius: 6px;
  border-radius: 6px;
}
{% endhighlight %}

Compass:

{% highlight scss %}
.box {
  @include border-radius( 6px )
}
{% endhighlight %}

#### Functions

Compass provides a bunch of useful Sass functions, like `image-height`, which can read in an image and provide the dimensions for you in your stylesheet. No more measuring!

{% highlight scss %}
.profile {
  $img: "avatar.jpg"
  width: image-width( $img )
  height: image-height( $img )
}
{% endhighlight %}

## What is Mustache.js?

- HTML templating with JavaScript.

- JavaScript implementation of Mustache - [https://github.com/janl/mustache.js](https://github.com/janl/mustache.js)

- Logic-less templates.

- What could be more logically awesome than no logic at all?

## What is Templating?

- HTML markup minus the data.

- Useful when working with a backend to create a dynamic page.

A Mustache template ...

{% highlight html %}
<div>
  <h1>Hello, {{'{{name'}}}}!</h1>
  <h2>You have {{'{{points'}}}} points.</h2>
</div>
{% endhighlight %}

... plus **data** ...

{% highlight js %}
var user = { name : 'Larissa', points : 5000 };
{% endhighlight %}

... equals some good lookin' markup:

{% highlight html %}
<div>
  <h1>Hello, Larissa!</h1>
  <h2>You have 5000 points.</h2>
</div>
{% endhighlight %}

### How would you have done that without Templating?

Probably like this:

{% highlight js %}
var user = { name : 'Larissa', points : 5000 };

var markup = "<div><h1>Hello, "
  + user.name 
  + "!</h1><h2>You have "
  + user.points
  + " points.</h2></div>";
{% endhighlight %}

But this puts HTML into your JavaScript as strings, and maintaining that is a real pain.

## Why use Mustache.js?

- Separates your views from your logic. HTML and JavaScript are not mixed.

- Makes it very simple to work with dynamic backends using JSON.

- Allows for a simultaneous multi-developer work flow. One to work on view templates, another for logic and mediation.

- Mustache templates can be source controlled as independent files.

- Because templates are logic-less, they are language-agnostic. Mustache implementations have been written for JavaScript, Ruby, PHP, etc...

## How to use Mustache.js:

Set up a template and a place to put your HTML:

{% highlight html %}
<script id="my-template" type="text/x-mustache-template">
  <h1>{{'{{message'}}}}</h1>
</script>

<div id="target-div"></div>
{% endhighlight %}

Then interpolate javascript values into it:

{% highlight js %}
var jsonData = { message: "Hello World!" };

var myTemplate = $( '#my-template' ).text();

$( '#target-div' ).html(Mustache.to_html(myTemplate, jsonData));
{% endhighlight %}

Mustache takes the properties from the data and puts it into your template.

{% highlight html %}
<div id="target-div">
  <h1>Hello World!</h1>
</div>
{% endhighlight %}

### Iterating over collections

Mustache has the ability to implicitly iterate over a collection it parses.

{% highlight html %}
<script id="my-template" type="text/x-mustache-template">
  {{'{{#peeps'}}}}
  <div>Hello, {{'{{name'}}}}!</div>
  {{'{{/peeps'}}}}
</script>
{% endhighlight %}

The data model has a `peeps` field with an array of objects.

{% highlight js %}
var jsonData = { peeps : [
  { name : "Alice" }, 
  { name : "Bob" }, 
  { name : "Candice" }
] };

var myTemplate = $( "#my-template" ).html( );

$( "#target-div" ).html( Mustache.to_html( myTemplate, jsonData ) );
{% endhighlight %}

Each object will be passed to the iterator, so we can grab all of the names.

{% highlight html %}
<div id="target-div">
  <div>Hello, Alice!</div>
  <div>Hello, Bob!</div>
  <div>Hello, Candice!</div>
</div>
{% endhighlight %}

## Conclusion

HTML and CSS were meant to build documents, not applications.

With Sass, Compass, and Mustache, we now have better tools for authoring and managing our static web content.
