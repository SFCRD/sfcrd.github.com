--- 
layout: post
title: "Case Study: Target Weekly Ad"
excerpt: A short description about the post goes here.
authors: 
- name: Kyle Beikirch
  email: kyle.beikirch@gmail.com
- name: Jeremy Ruppel
  email: jeremy.ruppel@gmail.com

---

# Case Study: Target Weekly Ad

A short description about the post goes here.

## New Section

Some more text. Happy posting!


## Ideas

- [Jammit](http://documentcloud.github.com/jammit/) - asset groups, keep javascripts separated and page weight down
- [Cucumber](http://cukes.info/) - automated acceptance testing, tied into jenkins so we know when the build breaks
- [Haml](http://haml-lang.com/)/[SASS](http://sass-lang.com/)/[Mustache](http://mustache.github.com/) - just sayin, we use the newest hotness
- Custom client-side persistence layer for Quick List - degrades gracefully all the way back to IE5.5
- Git/GitHub (this is actually a huge one)
	- branching - continuing development on phase 2 but maintenance on 1 is a breeze
	- pull requests - continual system of code review for any development that matters
	- readme - perfect place for developer documentation

### Libraries

  - [Raphael](http://raphaeljs.com/) - Hotspots  
  {% highlight js %}
  // creates a paper that is attached to the div with class "canvas" and then sets size.
  var paper = Raphael($('.canvas', 1200, 1500));

  // Creates shape based off SVG string and adds to the paper
  var hotspot = paper.path( "M 355.8 287.55 L 354.825 608 558.92 608.975 558.92 503.35 649.6 510.5" );
  
  // sets the hotspot opacity to 0 so it is invisible
  hotspot.attr( "opacity" , 0 );
  
  // Add jquery functionality functionality
  $( hotspot.node ).hover( function( event )
  {
     ///code goes here
  });
  {% endhighlight %}
  
  - [jQuery Tools](http://flowplayer.org/tools/scrollable/index.html) - Scroller
  
  HTML
  {% highlight html %}
  <!-- root element for scrollable -->
  <div class="scrollable">   

     <!-- root element for the items -->
     <div class="items">

        <!-- Page Content Divs -->
        <div>
           <!-- Page Content -->
        </div>
        
        <div>
           <!-- Page Content -->
        </div>
        
     </div>
  </div>
  {% endhighlight %}
  CSS
  {% highlight css %}
  /*
  	root element for the scrollable.
  	when scrolling occurs this element stays still.
  */
  .scrollable {

  	/* required settings */
  	position:relative;
  	overflow:hidden;
  	width: 660px;
  	height:90px;
  }

  /*
  	root element for scrollable items. Must be absolutely positioned
  	and it should have a extremely large width to accommodate scrollable items.
  	it's enough that you set width and height for the root element and
  	not for this element.
  */
  .scrollable .items {
  	/* this cannot be too large */
  	width:20000em;
  	position:absolute;
  }

  /*
  	a single item. must be floated in horizontal scrolling.
  	typically, this element is the one that *you* will style
  	the most.
  */
  .items div {
  	float:left;
  }
  {% endhighlight %}
  Javascript
  {% highlight js %}
  // create the scrollable
  $( '.scrollable' ).scrollable();
  
  //get the api
  var api = $( '.scrollable' ).data( 'scrollable' );
  
  //scroll to a certain page
  api.seekTo( pageNum );
  {% endhighlight %}
