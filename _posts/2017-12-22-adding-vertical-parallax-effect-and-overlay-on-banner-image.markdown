---
layout: post
title:  Adding vertical parallax effect and overlay on banner image 
date:   2017-12-22 09:42:22 +0000
---


![parallaxImage](https://support.squarespace.com/hc/article_attachments/115019176428/parallax_scroll_download.gif)
Parallax scrolling is a web site trend where the background content (i.e. an image) is moved at a different speed than the foreground content while scrolling.

Dimmed overlay with CSS, which give image a blackish effect, so text on it can be visible.

<script src="https://gist.github.com/rajatsingla/ce6d071e5bfe367b8949693caab2ad67.js"></script>
css
```css
.parallax-container {
    overflow: hidden;
    background-color: #070504;
}
img.accordion-banner-image {
    object-fit: cover;
    width: 100%;
    opacity: .5;
}
```
js
```js
    $(document).scroll(function(){
        $('#image-has-parallax').css('transform','translateY('+String($(document).scrollTop()/2)+'px)')
    })
```

Happy Coding.