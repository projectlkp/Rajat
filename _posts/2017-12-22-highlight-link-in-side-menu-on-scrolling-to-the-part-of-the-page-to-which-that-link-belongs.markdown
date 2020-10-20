---
layout: post
title:  Highlight link in side menu  on scrolling to the part of the page to which that link belongs 
date:   2017-12-22 12:34:46 +0000
---


![activelinks](https://www.elegantthemes.com/blog/wp-content/uploads/2017/08/activelinks.gif)

<script src="https://gist.github.com/rajatsingla/d124d78951773ba6feb48c093fe7df01.js"></script>

We iterate over all parts of the page.

For each part we calculate `part.offset().top`, which means y coordinate on page where element starts. If it is less than `scrollTop`. It means we have scrolled past this part of page and it is time to highlight it's link. and we keep the last part to which we have scrolledTo.

If no `offset().top` of any part is less than `scrollTop`. We keep last part.

Then we remove active class from all links and add active class to link of the part we kept.
<script src="https://gist.github.com/rajatsingla/ca3b584bf9d44c765eac6c3555857545.js"></script>

Happy Coding.