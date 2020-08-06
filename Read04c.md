## On Callbacks and Promises
JavaScript is synchronous by default, and is single threaded. This means that code cannot create new threads and run in parallel.
Computers are asynchronous by design.
Asynchronous means that things can happen independently of the main program flow.
But JavaScript was born inside the browser, its main job, in the beginning, was to respond to user actions, like onClick, onMouseOver, onChange, onSubmit and so on.
The browser provides a way to do it by providing a set of APIs that can handle this kind of functionality.

You can’t know when a user is going to click a button, so what you do is, you define an event handler for the click event. This event handler accepts a function, which will be called when the event is triggered: This is the so-called callback.

A callback is a simple function that’s passed as a value to another function, and will only be executed when the event happens.

How do you handle errors with callbacks? One very common strategy is to use what Node.js adopted: the first parameter in any callback function is the error object: error-first callbacks

## Asynchronous
In this module we take a look at asynchronous JavaScript, why it is important, and how it can be used to effectively handle potential blocking operations such as fetching resources from a server.

## Using Promises
A Promise is an object representing the eventual completion or failure of an asynchronous operation. Since most people are consumers of already-created promises, this guide will explain consumption of returned promises before explaining how to create them.

Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.

Guarantees
Unlike old-fashioned passed-in callbacks, a promise comes with some guarantees:
    - Callbacks will never be called before the completion of the current run of the JavaScript event loop.
    - Callbacks added with then(), as above, will be called even after the success or failure of the asynchronous operation.
    - Multiple callbacks may be added by calling then() several times. Each callback is executed one after another, in the order in which they were inserted.
    - One of the great things about using promises is chaining.

Chaining
A common need is to execute two or more asynchronous operations back to back, where each subsequent operation starts when the previous operation succeeds, with the result from the previous step. We accomplish this by creating a promise chain.

Promise rejection events
Whenever a promise is rejected, one of two events is sent to the global scope (generally, this is either the window or, if being used in a web worker, it's the Worker or other worker-based interface).

Creating a Promise around an old callback API
A Promise can be created from scratch using its constructor. This should be needed only to wrap old APIs.

Composition
Promise.resolve() and Promise.reject() are shortcuts to manually create an already resolved or rejected promise respectively. This can be useful at times.
Promise.all() and Promise.race() are two composition tools for running asynchronous operations in parallel.

Timing
To avoid surprises, functions passed to then() will never be called synchronously.

Nesting
Simple promise chains are best kept flat without nesting, as nesting can be a result of careless composition

## Promises in 20 minutes
JavaScript is a single-threaded language, which means that it can only do one thing at a time.

The A+ specification defines a promise this way: A promise represents the eventual result of an asynchronous operation. The primary way of interaction with a promise is through its then method, which registers callbacks to receive either a promise’s eventual value or the reason why the promise cannot be fulfilled.

A promise is basically a container for an asynchronous action — what this tells us is that, at a minimum, promises have to give us everything in terms of capability that vanilla async callbacks give us, because a promise is something that is taking a vanilla async callback and putting it into a format that will be less heinous to actually implement.

Promises don’t rely on anything other than basic JavaScript.

A promise takes an executor.

A promise has an internal state (which we cannot access or alter directly). Every promise starts out having a state of “pending.” Only once, in it’s whole “lifespan” can it change.

A promise has a value. This value in a success case will be the data we want, or an error (or a “reason”) if things go wrong. 

Finally, for a promise to be a promise, it has to have access to a “then” method (and we’re going to talk about this in more depth in a sec).

There are two main ways we’ll encounter promises in the wild. In JavaScript, we do have access to the promise constructor, so we can instantiate a new Promise, and pass it our executor and callbacks ourselves.

By passing this array to the JavaScript Promise’s all method, we will return a single promise that will either resolve when every promise has resolved, or reject with the reason of the first value in the array that reject.

## Google Developer on Promises
A promise can be:
- fulfilled - The action relating to the promise succeeded
- rejected - The action relating to the promise failed
- pending - Hasn't fulfilled or rejected yet
- settled - Has fulfilled or rejected

## Using Fetch
The Fetch API provides a JavaScript interface for accessing and manipulating parts of the HTTP pipeline, such as requests and responses. It also provides a global fetch() method that provides an easy, logical way to fetch resources asynchronously across the network.

Fetch provides a better alternative that can be easily used by other technologies such as Service Workers.

The fetch specification differs from jQuery.ajax() in three main ways:
    - The Promise returned from fetch() won’t reject on HTTP error status even if the response is an HTTP 404 or 500. Instead, it will resolve normally (with ok status set to false), and it will only reject on network failure or if anything prevented the request from completing.
    - fetch() won't can receive cross-site cookies; you can’t can establish a cross site session using fetch. Set-Cookie headers from other sites are silently ignored.
    - fetch won’t send cookies, unless you set the credentials init option. (Since Aug 25, 2017. The spec changed the default credentials policy to same-origin. Firefox changed since 61.0b13.)

The fetch() method can optionally accept a second parameter, an init object that allows you to control a number of different settings:

To cause browsers to send a request with credentials included, even for a cross-origin call, add credentials: 'include' to the init object you pass to the fetch() method.

## Fetching data
fetch() is not the only way JS can deal with data from servers, but it might be the easiest.

1. fetch() makes network request to a url and returns a promise.
2. That promise resolves with a response object when the remote server responds with headers.
3. To read the response body, we have to call a response method on it, like text() or json(), which will return another promise whose resolve value is the body of the response.

fetch() creates a promise that resolves with a response object.

Our apps would hardly be dynamic if they could only read data, so fetch() can take a second argument, a request. You simply pass in an object to fetch() that specifies the type of request you want to make, along with the headers and body and whatever else you need. 

fetch() can go to any url, including your own server. To visit your site’s own files, just give a relative path name instead of a URL.