---
layout: post
title: "What is Resourceful?"
excerpt: "A whirlwind tour of resourcefulness in Rails."

---

# What is Resourceful?

A whirlwind tour of resourcefulness in Rails.

## What is a Resource?

- A Resource is a **thing**, a noun, a specific source of information.
- You can have a collection of things, or pick out a specific thing.
- Furthermore, you can do things to things. This is where verbs come in.

## The seven Rails verbs

Rails is an opinionated framework, they provide seven main verbs for working with resources.

- index
- show
- new
- create
- edit
- update
- destroy

These are a very specific set of verbs. Let's find out where they came from.

### Four main HTTP verbs:

- **GET**: Gets the resource
- **POST**: Creates a new resource
- **PUT**: Updates an existing resource
- **DELETE**: Destroys a resource

These verbs can either apply to **one** resource, or the entire **collection** of resources.

### Verbs in relation to the individual

`http://example.com/resources/1`

- **GET**: Show the individual record.
- **POST**: Treat the record as a collection and create a new entry in it.
- **PUT**: Update or replace an existing record.
- **DELETE**: Destroy the individual record.

### Verbs in relation to the collection

`http://example.com/resources/`

- **GET**: List all of the collection's records.
- **POST**: Create a new record in the collection.
- **PUT**: Replace the entire collection with another collection.
- **DELETE**: Destroy the entire collection.

### The most common verbs

Typically, when dealing with resources, you end up with five verb/subject combinations you use almost exclusively.

~~~~
GET     /books      # show all of the books
POST    /books      # create a new book
GET     /books/:id  # show a specific book
PUT     /books/:id  # update a specific book
DELETE  /books/:id  # destroy a specific book
~~~~

### How the common verbs map to Rails

Since web browsers only `GET`, we end up with two of these routes by name in rails:

~~~~
books  GET     /books      # show all of the books
       POST    /books      # create a new book
 book  GET     /books/:id  # show a specific book
       PUT     /books/:id  # update a specific book
       DELETE  /books/:id  # destroy a specific book
~~~~

But that's only five verbs. What are the other two?

### Forms, forms, forms

It wouldn't make sense for us to `POST` to create a new book or `PUT` to update a book without describing what data we would like the book to have.

This is where forms come in. We get two more verbs now, **new** and **edit**, describing the actions *before* **create** and **update** respectively.

These both should give us a form to let us describe what data we would like to send with the request.

~~~~
    books  GET     /books           # show all of the books
           POST    /books           # create a new book
 new_book  GET     /books/new       # form for a new book
edit_book  GET     /books/:id/edit  # form for an existing book
     book  GET     /books/:id       # show a specific book
           PUT     /books/:id       # update a specific book
           DELETE  /books/:id       # destroy a specific book
~~~~

### A Rails Resource

In fact, this is the exact output for a new rails resource when you run `rake routes`.

~~~~
    todos GET    /todos(.:format)          {:controller=>"todos", :action=>"index"}
          POST   /todos(.:format)          {:controller=>"todos", :action=>"create"}
 new_todo GET    /todos/new(.:format)      {:controller=>"todos", :action=>"new"}
edit_todo GET    /todos/:id/edit(.:format) {:controller=>"todos", :action=>"edit"}
     todo GET    /todos/:id(.:format)      {:controller=>"todos", :action=>"show"}
          PUT    /todos/:id(.:format)      {:controller=>"todos", :action=>"update"}
          DELETE /todos/:id(.:format)      {:controller=>"todos", :action=>"destroy"}
~~~~

There are four verbs we can `GET`, and these end up being our pages. 

The other three non-`GET` verbs are used by the server itself or by a non-browser client.

## Why is being resourceful important?

- Being resourceful is all about following standards.
- If we can treat all resources the same way, it's easy to start working with another one.
- Some RIA frameworks like ActiveResource and Backbone count on it.

### Backbone.js

**Backbone** is a framework that allows you to easily work with Rails resources.

Backbone, however, does **NOT** easily let you work with anything else.

If the back-end's API is anything different than the resourceful set of routes we described earlier, *give up on Backbone now.*

<!--
	TODO more stuff here?
-->

## Further Reading

- [Representational State Transfer on Wikipedia](http://en.wikipedia.org/wiki/Representational_State_Transfer)
- [Ryan Tomayko: How I Explained REST to My Wife](http://tomayko.com/writings/rest-to-my-wife)