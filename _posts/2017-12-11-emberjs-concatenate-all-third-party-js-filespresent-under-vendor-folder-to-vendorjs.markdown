---
layout: post
title:  Ember js  concatenate all third party js files present under vendor folder   to vendor js 
date:   2017-12-11 10:32:40 +0000
---


`app.import('vendor/scripts/jquery_validation-1.17.0.min.js');`
adding this file to `ember-cli-build.js` will add this file to vendor.js

**You can't append** all the files together by using something like `app.import('vendor/scripts/*.js');`

Because of the dependency of JS libraries on each other
* which file to be loaded first?

So ember cli provides cleaner way to load i.e. **the file added first, will be loaded first.**

```js
const EmberApp = require('ember-cli/lib/broccoli/ember-app');

module.exports = function(defaults) {
  var app = new EmberApp(defaults, {
  });

  // You can add all the third party JS files here and they will be appended to vendor.js
  app.import('vendor/scripts/jquery_validation-1.17.0.min.js');
	
	return app.toTree();
};
```

Happy Coding
