--- 
layout: post
title: CoffeeScript
excerpt: A (kick ass) little language that compiles into JavaScript.
authors: 
- name: steckel
  email: curtis.steckel@akqa.com

---

# CoffeeScript

A (kick ass) little language that compiles into JavaScript.

## JavaScript is kind of a big deal.

- JavaScript is the programming language of the web.

- JavaScript is arguably the most popular and widespread programming language.

- JavaScript is widely misunderstood due to its "bad parts".

- Most people write JavaScript without understanding JavaScript.

- JavaScript is gaining momentum as a general-use programming language.

## So what the hell is CoffeeScript?

- CoffeeScript is "the good parts" of JavaScript with a major syntax redesign.

- It is a less verbose version of JavaScript, not a different or simplified language.

- **CoffeeScript is to Javascript** as **Sass is to CSS** or **Haml is to HTML**.

- The golden rule of CoffeeScript is: "It's just JavaScript".

## Why would I want to learn CoffeeScript?

- CoffeeScript lets you write, and **learn**, **more**, **good**, JavaScript **quicker**, with greater **ease**.

- CoffeeScript's syntax forces strict formatting concepts resulting in better **human readability** and **consistency** between developers and teams.

- It is not CoffeeScript v.s. JavaScript. It is CoffeeScript enhancing the JavaScript programming experience.

- Major influencers of JavaScript plan to evolve the language to reflect CoffeeScript in the future.

## Installing CoffeeScript

### With Homebrew (preferred method)

If you don't already have Homebrew, download it; It's awesome. [http://mxcl.github.com/homebrew/](http://mxcl.github.com/homebrew/ "http://mxcl.github.com/homebrew/")

- Open terminal.app

- Make sure homebrew is up to date $ `brew update`

- Install CoffeeScript $ `brew install coffee-script`

- Homebrew will take care of installing any dependencies (which in this case means NodeJS).

### With Node(JS) Package Manager

If you want to install NodeJS and NPM without Homebrew you can install NodeJS ([https://github.com/joyent/node/wiki/Installation](https://github.com/joyent/node/wiki/Installation "https://github.com/joyent/node/wiki/Installation")) and NPM ([http://npmjs.org/](http://npmjs.org/ "http://npmjs.org/"))

- Open terminal.app

- $ `npm install -g coffee-script` (g is for global)

### TextMate Support

The official CoffeeScript TextMate bundle can be found at [https://github.com/jashkenas/coffee-script-tmbundle](https://github.com/jashkenas/coffee-script-tmbundle "https://github.com/jashkenas/coffee-script-tmbundle")

- Open terminal.app

- $ `mkdir -p ~/Library/Application\ Support/TextMate/Bundles`

- $ `cd ~/Library/Application\ Support/TextMate/Bundles`

- $ `git clone git://github.com/jashkenas/coffee-script-tmbundle CoffeeScript.tmbundle`

- Reopen TextMate or "Reload Bundles" under "Bundles -> Bundle Editor"

## Writing CoffeeScript

Think JavaScript without the countless semi-colons and brackets. CoffeeScript uses whitespace (or indenting) to define blocks of code. You also don't need to use parentheses to invoke a function when passing arguments or use the keyword `var` when declaring variables. The keyword `function` has also been replaced by `->`.

### Basic CoffeeScript Syntax

Let's convert a simple JQuery click method implementation from JavaScript to CoffeeScript:

![Convert Simple JavaScript to CoffeeScript](/images/coffeescript/convert.png "Convert Simple JavaScript to CoffeeScript")

### example.coffee -> examples.js

![CoffeeScript](/images/coffeescript/example.coffee.png "CoffeeScript")

Compile the CoffeeScript using the terminal.app `coffee -c example.coffee`

![Compiled JavaScript](/images/coffeescript/example.js.png "Compiled JavaScript")
![Rendered JavaScript](/images/coffeescript/example.rendered.png "Rendered JavaScript")

### A few CoffeeScript features

- Heredocs
  ![Heredocs](/images/coffeescript/heredocs.png "Heredocs")

- String Interpolation
 ![String Interpolation](/images/coffeescript/stringInterpolation.png "String Interpolation")

- If, Else, Unless, and Conditional Assignment:  
  ![Conditional Statement](/images/coffeescript/conditionalStatement.png "Conditional Statement")

- Array Comprehensions:  
  ![Array Comprehensions](/images/coffeescript/arrayComprehension.png "Array Comprehensions")

- The Existential Operator  
  ![The Existential Operator](/images/coffeescript/existentialOperator.png "The Existential Operator")

- Classes  
  ![Classes](/images/coffeescript/classes.png "Classes")

- Operators and Aliases:  
  `CoffeeScript`.........`JavaScript`  
  `is`..........................`===`  
  `isnt`.......................`!==`  
  `not`........................`!`  
  `and`........................`&&`  
  `or`..........................`||`  
  `true`, `yes`, `on`......`true`  
  `false`, `no`, `off`.....`false`  
  `@`, `this`.................`this`  
  `of`..........................`in`  
  `in`..........................no JS equivalent

- as well as improved **Object** and **Array** syntax, **Function Binding** (`=>`), **Splats** (`...`), Slicing and Splicing with **Ranges** (`..`), **Cake/Cakefiles**, and more...

### Compiling CoffeeScript:

Like Compass or Sass, you'll be compiling your CoffeeScript files to JavaScript with the terminal.app. Here are some methods of compiling:

- Compile example.coffee to example.js `coffee -c example.coffee`
- Watch a file and continue to re-compile it as it's updated `coffee -cw example.coffee`
- Watch a folder of CoffeeScript files and compile them to a folder of JavaScript files `coffee -co javascripts/ coffeescripts/` (-cwo works too)
- Compile and combine CoffeeScript files into a single JavaScript file `coffee -j javascripts/app.js -c coffeescripts/*.coffee` (my favorite)

### Coffee in the terminal

Coffee is also available in the terminal in more ways than simply a compiler.

- Error reporting
- There is a REPL available in terminal.app by simply typing `coffee`
- Cakefiles (CoffeeScript's version of Makefiles or Rakefiles)
- Shell scripting

![CoffeeScript in the terminal](/images/coffeescript/terminal.png "CoffeeScript in the terminal")

## For the curious ones...

Much like the inventor of JavaScript took initiative to "hack together" JavaScript in under 10 days so there will be a viable competitor to Java for client side programming; Jeremy Ashkenas, creator of CoffeeScript, took initiative to create a "better javascript" because he couldn't simply wait for someone else to do it for him. And like Sarah Conner says, "No fate but what we make." -Terminator II  

### "It helps to have things like CoffeeScript out there it isn't overriding, it doesn't tell us what we must do but its suggestive, and if we want to pave that cow path we can, and I'm in favor."
-Brendan Eich (The creator of Javascript)

### "I think CoffeeScript is clearly good stuff. CoffeeScript is elegant it sort of takes the good parts, removes all of the stupid awful syntax that were inherited from the wrong languages, replaces it with something that is small and elegant and expressive. CoffeeScript is really great. And CoffeeScript is having a big influence on the ECMA Script committee... CoffeeScript is definitely in the right direction and I would like to see future languages looking more like CoffeeScript than like C." 
-Douglas Crockford (Inventor of JSON and JSLint among other JavaScript best practices and general bad assery)

### *"Serious business"*

I've written a more verbose version of this article and posted it for people who may be interested in a more *"serious business"* introduction to CoffeeScript; a brief history of JavaScript and where, and why, CoffeeScript is relevant for web developers. Check it out at [https://gist.github.com/1374768](https://gist.github.com/1374768 "https://gist.github.com/1374768")

## Links and References

### More information on learning CoffeeScript

- Official CoffeeScript website: [http://jashkenas.github.com/coffee-script/](http://jashkenas.github.com/coffee-script/ "http://jashkenas.github.com/coffee-script/")

- Pragmatic Bookshelf's "Introduction to CoffeeScript" screencast: [http://screencasts.org/episodes/introduction-to-coffeescript](http://screencasts.org/episodes/introduction-to-coffeescript "http://screencasts.org/episodes/introduction-to-coffeescript")

- Pragmatic Bookshelf's Book "CoffeeScript: Accelerated JavaScript Development": [http://pragprog.com/book/tbcoffee/coffeescript](http://pragprog.com/book/tbcoffee/coffeescript "http://pragprog.com/book/tbcoffee/coffeescript")

- Peepcode's "Meet CoffeeScrpt" screencast: [http://peepcode.com/products/coffeescript](http://peepcode.com/products/coffeescript "http://peepcode.com/products/coffeescript")

### Projects using CoffeeScript

- Included in Rails 3.1+

- CloudApp: [http://getcloudapp.com/](http://getcloudapp.com/ "http://getcloudapp.com/")

- Pow: [http://pow.cx/](http://pow.cx/ "http://pow.cx/")

- Hubot: [http://hubot.github.com/](http://hubot.github.com/ "http://hubot.github.com/")
