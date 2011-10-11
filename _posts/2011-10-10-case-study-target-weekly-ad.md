--- 
layout: post
title: "Case Study: Target Weekly Ad"
excerpt: A short description about the post goes here.
authors: 
- name: Jeremy Ruppel
  email: jeremy.ruppel@gmail.com

---

# Case Study: Target Weekly Ad

A short description about the post goes here.

## New Section

Some more text. Happy posting!


## Ideas

- Jammit - asset groups, keep javascripts separated and page weight down
- Cucumber - automated acceptance testing, tied into jenkins so we know when the build breaks
- Haml/SASS/Mustache - just sayin, we use the newest hotness
- Custom client-side persistence layer for Quick List - degrades gracefully all the way back to IE5.5
- Git/GitHub (this is actually a huge one)
	- branching - continuing development on phase 2 but maintenance on 1 is a breeze
	- pull requests - continual system of code review for any development that matters
	- readme - perfect place for developer documentation

### Libraries

  - Hotspots -  [Raphael](http://raphaeljs.com/).
  {% highlight js %}
  // creates a paper that is attached to the div with class "canvas" and then sets size.
  var paper = Raphael($('.canvas', 1200, 1500));

  // Creates shape based off SVG string and adds to the paper
  var hotspot = paper.path( "M 355.8 287.55 L 354.825 608 558.92 608.975 558.92 503.35 649.6 510.5" );
  // sets the hotspot opacity to 0 so it is invisible
  hotspot.attr( "opacity" , 0 );

  // Disables stroke
  hotspot.attr( "stroke" , false );
  
  // Add jquery functionality functionality
  $( hotspot.node ).hover( function( event )
  {
     ///code goes here
  });
  {% endhighlight %}
  
  - Scroller - [jQuery Tools](http://flowplayer.org/tools/scrollable/index.html).
