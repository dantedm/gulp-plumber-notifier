# gulp-plumber-notifier

> Prevent pipe breaking, log and notify using [gulp-plumber] and [node-notifier]

[gulp-plumber]: https://github.com/floatdrop/gulp-plumber

[node-notifier]: https://github.com/mikaelbr/node-notifier

![](https://raw.githubusercontent.com/Pleasurazy/gulp-plumber-notifier/master/img2.jpg)

![](https://raw.githubusercontent.com/Pleasurazy/gulp-plumber-notifier/master/img1.jpg)

Use Cases:

```js
//////////////////////////////////////////////////
// JavaScript Task                              //
//////////////////////////////////////////////////

var plumberNotifier = require('gulp-plumber-notifier');

gulp.src('./src/**/*.js')
  .pipe(plumberNotifier())
  .pipe(sourcemaps.init())
  .pipe(babel({ modules: 'umd' }))
  .pipe(sourcemaps.write())
  .pipe(gulp.dest('./dist'))
  .pipe(connect.reload());
```

```js
//////////////////////////////////////////////////
// Styles Task                                  //
// + SASS -> CSS                                //
// + Remove unused CSS                          //
// + Add vendor prefixes                        //
// + Minify                                     //
//////////////////////////////////////////////////

gulp.task('styles', function () {
    return gulp
        .src('scss/**/*.scss')
        .pipe(plumberNotifier())
        .pipe(sass({
            outputStyle: 'compressed',
            sourcemap: true,
        }))
        .pipe(uncss({
            html: ['index.html', 'posts/**/*.html', 'http://example.com']
        }))
        .pipe(prefix('last 2 versions'))
        .pipe(csso())
        .on('error', errorLog)
        .pipe(gulp.dest('build/css'))
        .pipe(livereload());
});
```
