--- 
layout: post
title: "Case Study: Club Wedd 101 Things"
excerpt: http://apps.facebook.com/targetclubwedd/
authors: 
- name: Jeremy Ruppel
  email: jeremy.ruppel@gmail.com

---

# Case Study: Club Wedd 101 Things

[http://apps.facebook.com/targetclubwedd/](http://apps.facebook.com/targetclubwedd/)

## Background

101 Things is a site for the Target brand, Club Wedd, that allows fiancees to browse through 101 different activities that they can do as newlyweds. 

As a couple, they can create a list of activities they would like to do in the future, check off activities they have completed, and attach a comment and photo to preserve it all. 

Attached to every activity is a collection of products they can add to their Target wedding registry right from the site.

## The Challenges

- No Flash, completely HTML/CSS/JavaScript

- Totally dynamic site

- No page refreshes

- Completely deep-linkable

- User authentication and persistance

- Facebook integration

## The Stack

- jQuery - [http://jquery.com/](http://jquery.com/)

- Rails - [http://rubyonrails.org/](http://rubyonrails.org/)

- Mustache - [http://mustache.github.com/](http://mustache.github.com/)

- Backbone - [http://documentcloud.github.com/backbone/](http://documentcloud.github.com/backbone/)

- Uploadify - [http://www.uploadify.com/](http://www.uploadify.com/)

- Compass - [http://compass-style.org/](http://compass-style.org/)

- Underscore - [http://documentcloud.github.com/underscore/](http://documentcloud.github.com/underscore/)

## Challenge: Build a Flash-like site, *without Flash*.

### Choosing a framework

Since we were tasked with building such a large application in JavaScript, it quickly became clear we needed a framework to help us organize our app. 

Because we were going to be sitting on top of a (mostly) **RESTful** backend, we went with Backbone.

### Why Backbone?

- Backbone provides *Models* and *Collections* that correspond to Rails resources.

- **CRUD** actions for those models are completely handled by Backbone.

- Backbone provides a **History** module to support deep-linking.

{% highlight js %}
ClubWed.Activities = Backbone.Collection.extend(
{
  model : ClubWed.Activity,
  url   : "/activities"
} );
{% endhighlight %}

## Challenge: Handle **tons** of dynamic content from the backend.

### Mustache

Mustache allowed us to translate the copious amount of data from the backend into our views cleanly.

{% highlight html %}
<ul class="carousel">
  {{'{{#products'}}}}
  <li>
    <div class="jcarousel-item-wrapper">
      <div class="product">      
        <img src="{{main_url}}" width="52" height="52" alt="Temp Product Icon">
        <div class="name">    
          {{'{{#hasBrand'}}}}
          <span class="bolded">{{'{{brand'}}}}</span><br/>
          {{'{{name'}}}}
          {{'{{/hasBrand'}}}}

          {{'{{#noBrand'}}}}
          <span class="bolded no-brand">{{'{{name'}}}}</span>
          {{'{{/noBrand'}}}}
        </div>   
      </div>
    </div>
  </li>
  {{'{{/products'}}}}
</ul>
{% endhighlight %}

## Challenge: Use a custom web font and *@font-face*.

### Some pitfalls

- Web licensing of fonts is different from other licensing.

- Need to have at least four different versions of each font.

### Font Squirrel

[http://www.fontsquirrel.com/fontface/generator](http://www.fontsquirrel.com/fontface/generator)

- Font Squirrel can convert your font into all of the web font variations.

- Many great options available to massage your fonts during conversion.

- **Free** as in free beer. Can't beat that.

### Compass

If you're familiar with web fonts and `@font-face`, you know it's very finicky.

Your CSS needs to be *perfect* to include web fonts across browsers.

Luckily, there's a [compass mixin](http://compass-style.org/reference/compass/css3/font_face/#mixin-font-face) for that!

{% highlight sass %}
@include font-face("this name", font-files("this.woff", "woff", "this.otf", "opentype"), "this.eot")
{% endhighlight %}
