---
layout: post
title: "Pimp My TextMate"
excerpt: "How to TextMate like a real baller."
authors:
  - Jeremy Ruppel

---

# Pimp My TextMate

![Xzibit](/images/xzibit.png)

How to TextMate like a real baller.

[TextMate](http://macromates.com/)

## Yo dawg, I herd you like coding...

**TextMate** is the editor of choice for many Mac developers, from ruby to javascript and beyond.

For our web projects, it's a natural choice because of how easy it is to switch contexts.

One of **TextMate's** largest strengths, however, is how extensible it is.

This guide rounds up some of the best plugins, bundles, and tricks out there so you can pimp your TextMate and code like a real baller.

## Before Starting

**TextMate** integrates really tightly with your environment and can run pretty much any unix executable you throw at it.

Lots of the plugins and bundles mentioned later will require you to install some new programs.

To do this quickly and painlessly, make sure you have the following installed:

- [Xcode (with X11)](https://connect.apple.com/)

- [Homebrew](http://mxcl.github.com/homebrew/)

Also, make sure you have `/usr/local/bin` in your **TextMate PATH**:

- Go to the **TextMate Menu > Preferences**

- Go to the **Shell Variables** section.

- If there isn't a variable named **PATH** already, create one (but there ought to be).

- If **PATH** is empty, give it the value `/usr/local/bin`.

- If **PATH** isn't empty, append `:/usr/local/bin` to the end of it.

## Bundles

**TextMate** allows developers to extend the editor's understanding of its content through **Bundles**. To install a bundle, you only need to download it and double-click it. TextMate handles the rest.

### JSHint

![JSHint](/images/jshint.png)

This awesome [JSHint TextMate Bundle](http://fgnass.posterous.com/jslint-in-textmate) includes the JavaScript syntax tool, **jshint**, and can run it for you every time you save a file.

This is not only super helpful in keeping your scripts error-free, but is invaluable in keeping your sanity when it comes time to minify your scripts.

#### Dependencies:

- *node.js*: `brew install node`

#### Installation:

- Download the [zip file](http://github.com/fgnass/jshint.tmbundle/zipball/master) and unpack it.

- Rename the extracted folder to `jshint.tmbundle`.

- Double-click the bundle to install it.

#### Usage:

- By default, **jshint** is bound to **&#x2318;S** (Command-S), so every time you save your file it'll get hinted automatically.

- In the warnings window that pops up, click on a warning and your cursor will be placed at the offending character in your script.

## Plugins

Much like **Bundles**, you can install TextMate **Plugins** simply by double-clicking them. **Plugins** alter the editor itself and can add additional windows, commands, and the like.

### AckMate

![AckMate](/images/ackmate.png)

In really large projects, **TextMate**'s *Find in Project* becomes very slow, and slow search is **not baller.**

Enter [AckMate](https://github.com/protocool/ackmate), a super-slick plugin to provide an interface to `ack`, the blazing fast command-line search tool.

#### Dependencies:

- *ragel*: `brew install ragel`

- *ack*: `brew install ack`

#### Installation:

- Download the latest version from the project's [downloads section](https://github.com/protocool/AckMate/downloads) and unpack it.

- Save any unsaved documents you have open in TextMate. The installation will restart the app.

- Double-click the plugin to install it.

#### Usage:

- By default, **AckMate** is bound to **&#x2324;&#x2325;&#x2318;F** (Control-Option-Command-F). 

- Part of what makes `ack` so fast is that it can filter your search by *file type*. Use the **options** box to limit your search, or just use the tag **text** to search all text-based documents in your project.

## Tips & Tricks

**TODO:**

- TextMate droplets

- Sparkup

- CSS Navigator

- Align Text