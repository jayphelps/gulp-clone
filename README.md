# [gulp](https://github.com/wearefractal/gulp)-clone [![Build Status](https://secure.travis-ci.org/mariocasciaro/gulp-clone.png?branch=master)](https://travis-ci.org/mariocasciaro/gulp-clone) [![NPM version](https://badge.fury.io/js/gulp-clone.png)](http://badge.fury.io/js/gulp-clone) [![Dependency Status](https://gemnasium.com/mariocasciaro/gulp-clone.png)](https://gemnasium.com/mariocasciaro/gulp-clone)

> Duplicate files in memory.

## Install

Install with [npm](https://npmjs.org/package/gulp-clone).

```
npm install --save-dev gulp-clone
```

## Examples

gulp-clone is useful in all those situations where you perform a destructive operation on your files (as for example concat) and you want to keep your original files for further processing or saving...everything in just one stream pass.

```js
var gulp = require('gulp');
var concat = require('gulp-concat');
var clone = require('gulp-clone');

var cloneSink = clone();

gulp.task('default', function () {
    gulp.src('assets/**/*.js')
        .pipe(cloneSink)                //<- clone objects streaming through this point
		.pipe(concat("bundle.js"))
        .pipe(cloneSink.tap())          //<- output cloned objects + bundle.js
        .gulp.dest('out/');             //<- saves bundle.js + original files in one pass
});
```

## License

[MIT](http://en.wikipedia.org/wiki/MIT_License) @ Mario Casciaro