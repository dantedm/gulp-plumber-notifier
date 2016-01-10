# gulp-plumber-notifier

> Prevent pipe breaking, log and notify using [gulp-plumber] and [node-notifier]

[gulp-plumber]: https://github.com/floatdrop/gulp-plumber

[node-notifier]: https://github.com/mikaelbr/node-notifier

![](https://raw.githubusercontent.com/Pleasurazy/gulp-plumber-notifier/master/img2.jpg)

![](https://raw.githubusercontent.com/Pleasurazy/gulp-plumber-notifier/master/img1.jpg)
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
