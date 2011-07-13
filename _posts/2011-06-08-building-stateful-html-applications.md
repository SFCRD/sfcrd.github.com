---
layout: post
published: false

---
Building Stateful HTML Applications
===================================

Teach people how to build a fully dynamic website with no page refreshes.

TODO
----

And some `inline` code too! Maybe some **strong** and *emphasized* text as well?

Here's the basic idea:

	$( 'a' ).click( function( )
	{
		$.get( $( this ).attr( 'href' ), function( response )
		{
			$( '#content' ).html( response );
		} );

		return false;
	} );

What is a stateful HTML application?
------------------------------------

- A website without page refreshes.

- Absence of a unique URL linking to a state of the application.

- The state of the application is kept in memory managed by JavaScript, instead of stored in a cookie, stored in a session or passed by query string. 

- Data is requested by AJAX methods rather than form posts or page refreshes with query string parameters.

Why a stateful HTML application?
--------------------------------

- Page refreshes can disrupt a user experience by removing the user from an environment.

- Loading and transitions between states can be designed and art directed.

- HTML works on all devices.

- The creative concept does not require features provided by Flash or Silverlight.
	
Reasons to not have a stateful HTML application
-----------------------------------------------

- The creative concepts needs features provided by Flash or Silverlight (i.e. bitmap manipulation, web cams, heavy use of video, sound, complex animation).

- Tracking and accessing information is the top priority and fully qualified URLs are needed.

Components of a stateful HTML application
-----------------------------------------

- CSS - Defines the style and design rules.

- HTML - Defines the view structure and order.

- JavaScript - Defines the data flow and transition logic.

- A server-side technology - Provides the interface to databases and other web services.

Challenges in creating stateful HTML applications
-------------------------------------------------

- Difficult to deep link and maintain browser history.

- Cross browser issues with CSS and JavaScript.

- Lack of structure in JavaScript.

The solution stack
------------------

- CSS - Sass and Compass

- HTML - Mustache.js

- JavaScript - Backbone.js and jQuery

- Server-side - Ruby on Rails

There are variations, but the goal is the same.

DEFINITIONS AND ARGUMENTS

What is Ruby on Rails?
----------------------

An open-source web framework that’s optimized for programmer happiness and sustainable productivity. It lets you write beautiful code by favoring convention over configuration.

Note: “Ruby” is a programming language. “Ruby on Rails” is an MVC framework for the the “Ruby” programming language. 

Why use Ruby on Rails?
----------------------

- Low barrier to entry and easy setup.

- Mass availability of third-party libraries (Gems).

- There is only one way. The Rails way.

- It is the most common platform in our technology department at AKQA SF.

Alternatives:
-------------

- Sinatra (Ruby)

- C#.NET MVC (C#)

- CodeIgniter (PHP)

- Apache Struts (Java)

- Django (Python)

What is Backbone.js and jQuery?
-------------------------------

- Backbone.js - Supplies structure to JavaScript-heavy applications by providing models with key-value binding and custom events, collections with a rich API of enumerable functions, views with declarative event handling, and connects it all to your existing application over a RESTful JSON interface.

- jQuery - A fast and concise JavaScript Library that simplifies HTML document traversing, event handling, animating, and Ajax interactions for rapid web development. jQuery is designed to change the way that you write JavaScript.

Why use Backbone.js and jQuery?
-------------------------------

- Removes cross-browser pains with JavaScript.

- Provides helpers for working with AJAX, animation, DOM manuipulation, etc.

- Promotes structure and order through use of an MVC design pattern and OO practices.

- Provides a hash tag routing system for maintaining state and deep linking.