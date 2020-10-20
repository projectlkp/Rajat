---
layout: post
title:  Clean way to handle scroll events in emberjs app without blocking task queue and runtime 
date:   2017-12-22 09:27:55 +0000
---


Solving following two Problems:-
* Scroll events can fire at a high rate. So It is recommended to add callback once user stops scrolling.
* And another problem is multiple scroll listeners in your emberjs app here and there. Instead there should be an array of all scroll callbacks and a single scroll listener.

* **Create a service for scroll-events which binds a scroll listener and a callback functions array.**
<script src="https://gist.github.com/rajatsingla/dd7eb66533039a94166cc22333156823.js"></script>

In `init` function we bind a scroll event listener, which keeps checking whether scrolling stopped or not. After scrolling stops it executes a function `dosomething`.

`dosomething` executes all callbacks present in the callbacks array.

`addcallback` function adds the callback in array, if callback is not already present.


* **Add this service anywhere you want to add callback function.**
<script src="https://gist.github.com/rajatsingla/d6fa2bfd97d531184156e1e44767d120.js"></script>

By default `init` function defined in ember service is lazy and will be called first time we inject the service. So we can be sure that we are registering only one scroll listener.

Then we will push the callback into callback array (in example we are pushing `parallaxImage` function), which will be called and get scroll top y coordinate as a param.

You can also define remove_callback to remove a callback from callbacks array and call it in willDestroyElement hook, depending on your requirement. But you get the idea.

Happy Coding.

