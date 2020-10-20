---
layout: post
title:  How to create sticky left sidebar which sticks on scrolling 
date:   2017-12-22 10:27:01 +0000
---


![sticky](https://i.stack.imgur.com/UhW5w.gif)

<script src="https://gist.github.com/rajatsingla/2499089979748813b67699873679405d.js"></script>
On scroll we call `stickyMenu` function, 

We check sidemenu's `ele.offset().top`, which means y coordinate on page where element starts.

And then we compare it with `$(document).scrollTop()`, if `offset().top` is less than `scrollTop`, then we have passed by sidemenu, so we add `sticky` class to make it `fixed`, otherwise we remove `sticky` class.

and then when we scrolled past links container and reaching footer, we add the diff of height of parent and `scrolltop` as top to stickyMenu to push it upwards.
<script src="https://gist.github.com/rajatsingla/ca3b584bf9d44c765eac6c3555857545.js"></script>
<script src="https://gist.github.com/rajatsingla/0194f71dd11bf470a3259c2db8f96207.js"></script>