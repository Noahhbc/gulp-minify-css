# gulp-minify-css

[![NPM version](http://img.shields.io/npm/v/gulp-minify-css.svg)](https://www.npmjs.com/package/gulp-minify-css)
[![Build Status](https://travis-ci.org/murphydanger/gulp-minify-css.svg?branch=master)](https://travis-ci.org/murphydanger/gulp-minify-css)
[![Build status](https://ci.appveyor.com/api/projects/status/eidg7ju694an2i74?svg=true)](https://ci.appveyor.com/project/ShinnosukeWatanabe/gulp-minify-css)
[![Coverage Status](https://img.shields.io/coveralls/murphydanger/gulp-minify-css.svg)](https://coveralls.io/r/murphydanger/gulp-minify-css)
[![Dependency Status](https://img.shields.io/david/murphydanger/gulp-minify-css.svg?label=deps)](https://david-dm.org/murphydanger/gulp-minify-css)
[![devDependency Status](https://img.shields.io/david/dev/murphydanger/gulp-minify-css.svg?label=devDeps)](https://david-dm.org/murphydanger/gulp-minify-css#info=devDependencies)

[gulp](http://gulpjs.com/) plugin to minify CSS, using [clean-css](https://github.com/jakubpawlowicz/clean-css)

## Regarding Issues

This is just a simple [gulp](https://github.com/gulpjs/gulp) plugin, which means it's nothing more than a thin wrapper around `clean-css`. If it looks like you are having CSS related issues, please contact [clean-css](https://github.com/jakubpawlowicz/clean-css/issues). Only create a new issue if it looks like you're having a problem with the plugin itself.

## Installation

[Use npm.](https://docs.npmjs.com/cli/install)

```
npm install --save-dev gulp-minify-css
```

## API

```javascript
var minifyCss = require('gulp-minify-css');
```

### minifyCss([*options*])

*options*: `Object`  
Return: `Object` ([stream.Transform](https://nodejs.org/docs/latest/api/stream.html#stream_class_stream_transform))

Options are directly passed to the [`CleanCSS` constructor](https://github.com/jakubpawlowicz/clean-css#how-to-use-clean-css-programmatically) so all the clean-css options are available.

```javascript
var gulp = require('gulp');
var minifyCss = require('gulp-minify-css');

gulp.task('minify-css', function() {
  return gulp.src('styles/*.css')
    .pipe(minifyCss({compatibility: 'ie8'}))
    .pipe(gulp.dest('dist'));
});
```

[Source Maps](http://www.html5rocks.com/tutorials/developertools/sourcemaps/) can be generated by using [gulp-sourcemaps](https://github.com/floridoo/gulp-sourcemaps).

```javascript
var gulp = require('gulp');
var minifyCss = require('gulp-minify-css');
var sourcemaps = require('gulp-sourcemaps');

gulp.task('minify-css', function() {
  return gulp.src('./src/*.css')
    .pipe(sourcemaps.init())
    .pipe(minifyCss())
    .pipe(sourcemaps.write())
    .pipe(gulp.dest('dist'));
});
```

## LICENSE

[MIT](./LICENSE) © [Murphy Danger](https://github.com/murphydanger)
