---
layout: post
title: "mustache.js"
excerpt: "Logic-less templates for JavaScript."
authors:
  - Jeremy Ruppel

---

# mustache.js

Logic-less templates for JavaScript.

[https://github.com/janl/mustache.js](https://github.com/janl/mustache.js)

## The Skinny

Client-side templating can help ease the pain of developing HTML apps by separating view logic from business logic.

There are quite a few templating solutions out there, but **mustache.js** is pretty popular right now.

This guide will take you through:

- **What** is client-side templating?

- **Why** is it considered a best practice?

- **How** can I get started using **mustache.js**?

- **What** are some more advanced techniques for using **mustache.js**?

## Client-side templating

Client-side templating refers to the process of separating your HTML views from the business logic behind them.

It is an attempt to eliminate two big code smells:

- HTML code with JavaScript logic smattered throughout

{% highlight html %}
<div id="login"></div>
<script type="text/javascript">
  if( user.isLoggedIn )
  {
    $( '#login' ).text( 'Hello, ' + user.name + '!' );
  }
  else
  {
    $( '#login' ).text( 'Please log in' );
  }
</script>
{% endhighlight %}

- JavaScript strings of HTML being stuck together and inserted into the DOM

{% highlight html %}
<script type="text/javascript">
  var login = '<div id="login">';

  if( user.isLoggedIn )
  {
    login += 'Hello, ' + user.name + '!';
  }
  else
  {
    login += 'Please log in';
  }
  
  login += '</div>';

  $( 'body' ).append( login );
</script>
{% endhighlight %}

Both of these examples mix up the HTML view with the business logic. In both cases, it's actually kind of difficult to tell that this code ends up spitting out HTML. *Shouldn't HTML look like HTML?*

## A {{'{{mustached'}}}} solution

Here's an example of our login div using **mustache.js**:

**The view template:**

{% highlight html %}
<div id="login">
  {{'{{#isLoggedIn'}}}}
  Hello, {{'{{name'}}}}!
  {{'{{/isLoggedIn'}}}}
  
  {{'{{^isLoggedIn'}}}}
  Please log in
  {{'{{/isLoggedIn'}}}}
</div>
{% endhighlight %}

**The JavaScript code-behind:**

{% highlight html %}
<script type="text/javascript">
  var login = $( '#login' ).html( );
  
  $( 'body' ).append( Mustache.to_html( login, user ) );
</script>
{% endhighlight %}

The **view** has been clearly separated from the **logic** behind it.

## {{'{{mustache'}}}} API

Including **mustache.js** in your page gives you the **Mustache** object.

**Mustache** only has one method you will ever need: `to_html`.

`Mustache.to_html( template, data ); // returns your templated HTML`

`template` is your HTML template with mustaches. A good way to get this data is to use `jQuery.html( )`, which returns all of the text within a node.

`data` is the javascript object to use as the data for the template. In the previous example, it was named `user` and had `user.isLoggedIn` and `user.name` defined.

## {{'{{mustache'}}}} syntax

**mustache.js** has a very limited number of things it can do through templates.

*This is totally intentional.*

Ideally, there shouldn't be too much logic in our views at all!

Views should be as *dumb* as possible; logic should be placed elsewhere in the application.

### Values

The simplest part of **mustache** syntax is inserting values in your templates.

If you have a data object `{ hello : 'world' }` that you pass to `Mustache.to_html`, if you put `{{'{{hello'}}}}` in your template, it will be replaced with `world`.

Likewise, if the value of your property is a function, mustache will call that function and use whatever the function returns in the template.

### Conditionals

One of the only 'logic'-ish things **mustache.js** supports is conditionals. We used these in the previous example.

Use a **hash (#)** to only render something if that value is truthy. Close the conditional section with a **slash (/)**:

{% highlight html %}
<script type="text/javascript">
  // the data object
  var data = { prop : true }; // or 1 or 'yes' or anything truthy
</script>

{{'{{#prop'}}}}
The value of 'conditional' was truthy!
{{'{{/prop'}}}}
{% endhighlight %}

Likewise, use a **caret (^)** to only render something if that value is falsy.

{% highlight html %}
<script type="text/javascript">
  // the data object
  var data = { prop : false }; // or null or undefined or anything falsy
</script>

{{'{{^prop'}}}}
The value of 'conditional' was falsy!
{{'{{/prop'}}}}
{% endhighlight %}

### Iteration

If your data object has a property that is an array, you can iterate over the items in that array by again using a **hash (#)**. You can access the current item in the array with **{{'{{.'}}}}**:

{% highlight html %}
<script type="text/javascript">
  // the data object
  var data = { prop : [ 1, 2, 3, 4 ] };
</script>

// with the template
{{'{{#prop'}}}}
I can count to {{'{{.'}}}}!
{{'{{/prop'}}}}

// gives us:
I can count to 1!
I can count to 2!
I can count to 3!
I can count to 4!
{% endhighlight %}

### Dereferencing Sections

If you have nested objects in your data objects, you can use the same **hash (#)** syntax to descend into those objects:

{% highlight html %}
<script type="text/javascript">
  // the data object
  var data = {
    greeting : 'Salutations!',
    user : {
      name : 'Harold'
    }
  };
</script>

// with the template
{{'{{greeting'}}}}, {{'{{#user'}}}}{{'{{name'}}}}{{'{{/user'}}}}!

// gives us:
Salutations, Harold!
{% endhighlight %}

### Escaping

By default, **mustache.js** escapes certain entities in any value provided by the data object. These values include `& \ " < >`. If you need to un-escape your value in your template, use a **{{'{{{triple mustache!'}}}}}**.

## Advanced mustaching

### Embedded templates

A common question when working with **mustache.js** is "Where should I put my templates?".

A recommended approach for HTML templating, not just for mustache, is to embed your templates in your page.

We do so by using a script tag with a content-type no browser will understand, like `text/html` or `text/x-mustache-template`.

You can then easily grab the contents of the script tag by its ID and mustache away!

{% highlight html %}
<script id="user" type="text/html">
  <div>
      <div>Hello, {{'{{name'}}}}!</div>
  </div>
</script>
<script type="text/javascript">
  var user = { name : 'Harold' };

  $( 'body' ).append( Mustache.to_html( $( '#user' ).html( ), user ) );
</script>
{% endhighlight %}

### ICanHaz.js

[ICanHaz.js](http://icanhazjs.com/) is a great little tool for mustaching using the embedded template technique mentioned above.

The script includes a copy of **mustache.js** in it, so you only need to include **ICanHaz.js** in your page.

After the page loads, **ICanHaz.js** grabs all of your templates (script tags with content type **'text/html'** and a valid **id** attribute) and caches them.

You could then access any of them through the `ich` object. The script in the above example could then be simplified to:

{% highlight html %}
<script id="user" type="text/html">
  <div>
      <div>Hello, {{'{{name'}}}}!</div>
  </div>
</script>
<script type="text/javascript">
  var user = { name : 'Harold' };
  
  $( 'body' ).append( ich.user( user ) );
</script>
{% endhighlight %}

### Consume JSON API's

One of the best parts about JavaScript templating is that it plays **really** nicely with JSON services.

Many times, you can take the service result verbatim and hand it off to your template. This approach really simplifies your code-behind.

This full example retrieves information about SFCRD from GitHub, templates it, and inserts it into the DOM:

{% highlight html %}
<!-- include icanhaz.js, which includes mustache.js -->
<script src="/javascripts/icanhaz.js" charset="utf-8"></script>

<!-- make a simple HTML template with mustaches -->
<script type="text/html" id="github">
  <div>
    <img src="{{'{{avatar_url'}}}}" alt="{{'{{name'}}}}'s GitHub Avatar" />
    <a href="{{'{{html_url'}}}}" target="_blank">
      <p>{{'{{name'}}}}</p>
    </a>
  </div>
</script>

<!-- make an API call to github and pass the JSON response off to our template straight up -->
<script type="text/javascript">
  $( function( )
  {
    $.get( 'https://api.github.com/users/sfcrd', function( response )
    {
      $( '#sfcrd' ).append( ich.github( response.data ) );
    },
    'jsonp' );
  } );
</script>

<!-- placeholder div that we'll insert the content into -->
<div id="sfcrd"></div>
{% endhighlight %}

<script src="/javascripts/icanhaz.js" charset="utf-8"></script>
<script type="text/html" id="github">
  <div>
    <img src="{{'{{avatar_url'}}}}" alt="{{'{{name'}}}}'s GitHub Avatar" />
    <a href="{{'{{html_url'}}}}" target="_blank">
      <p>{{'{{name'}}}}</p>
    </a>
  </div>
</script>
<script type="text/javascript">
  $( function( )
  {
    $.get( 'https://api.github.com/users/sfcrd', function( response )
    {
      $( '#sfcrd' ).append( ich.github( response.data ) );
    },
    'jsonp' );
  } );
</script>
<div id="sfcrd"></div>

### Augment API responses

Often times, when using the technique above, the service response doesn't provide the exact data we need, or we need to do some pre-processing before templating.

In these cases, instead of manipulating the data in the response handler, it would be a better idea to adorn the response object with our custom methods.

Consider the following API response that returns user information:

{% highlight js %}
{
  "user" :
  {
    "id" : 12,
    "first_name" : "Harold",
    "last_name" : "Potter"
  }
}
{% endhighlight %}

We would be much better off trying to make this response a first-class object, that way it'll be re-usable and contained.

Here, we create our user domain methods and augment them onto our response using `jQuery.extend`:

{% highlight html %}
<script type="text/javascript">
  var user = {
    full_name : function( )
    {
      return [ this.first_name, this.last_name ].join( ' ' );
    }
  };
  
  $.get( 'https://api.example.com/users/12', function( response )
  {
    $( 'body' ).append( ich.github( $.extend( response, user ) ) );
  },
  'json' );
</script>
{% endhighlight %}

Now we can add as many other custom methods as we want and we still keep the response handler super simple.

## Alternatives

While **mustache.js** is an awesome and popular solution for client-side templating, many other solutions exist.

- [jquery-tmpl](https://github.com/jquery/jquery-tmpl)

- [EJS](http://embeddedjs.com/)

- [haml-js](https://github.com/creationix/haml-js)

- [pure](http://beebole.com/pure/)
