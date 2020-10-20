---
layout: post
title:  Emberjs achieve two way binding with native input tag and discard input helper 
date:   2017-12-11 13:46:29 +0000
---


Input helper provided by emberjs is limited, to be actually useful in validation rich forms.

Native input tag is way much more flexible than input helper, but problem with native input tag is two way value binding.

<script src="https://gist.github.com/rajatsingla/af32a277b2fcaadf767a7e0102ae625b.js"></script>

In above example input tag will initially get its value from `email` property, but when user changes the email input, same will not be reflected on `email` property.

<script src="https://gist.github.com/rajatsingla/7203535048b780c2bf89713525e06196.js"></script>
, here `email` property will be automatically updated, but as i said earlier this helper is limited.

So how to get best of both world?

Make a component for custom-input:
```js
// custom-input.js
import Ember from 'ember';
export default Ember.Component.extend({
  classNames: ['custom-input'],
  tagName: 'div',
});
```
<script src="https://gist.github.com/rajatsingla/892b4172cb4a3d14b5d8fcd5ed5ef8bf.js"></script>

<script src="https://gist.github.com/rajatsingla/b3c8f75e1ed8e9089d701150346d44f8.js"></script>

* In above example we are using onchange callback of input tag.
* Current value of input will be available in `target.value`.
* mut helper provided by ember, will mutate the property(`val`) passed to it, by given value(`target.value`), passed as 2nd argument.
* `val` is the value binding we have done while calling the component, check example usage,
* It is similar to input helper, but we have total control over it.
*  Properties not passed while calling component will be automatically ignored.
*  I use ` data-value` particularly to have value visible in DOM, because by default ember hide value attribute in DOM. I use it for css purpose.

Input helper will suffice in most cases, but you can create a custom-input, which you can modify according to your need.

Happy Coding.




