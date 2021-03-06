# ✂ gulp-css-tailor

> Gulp plugin that automatically generates CSS from your HTML classes

Utility that turns the classes applied upon the **DOM elements to CSS**. So that you don't have to manually write the CSS for those minor UI enhancements like increasing the padding, adding a little margin, changing the font size, applying a border radius, pumping up the line-height a bit etc.

If you are looking for css-tailor, find it at [kamranahmese/css-tailor](https://github.com/kamranahmedse/css-tailor)

## Usage

> All you have to do is specify the CSS class on any DOM element, CSS will be generated and written to a CSS file of your liking or returned for any programmatical use.

All you have to do is specify any HTML class as follows

```
[formula][value][unit] # If you donot provide the unit, `px` will be used.
```

For example; `mt25` translates to `margin-top: 25px`, `fs14px` to `font-size: 14px;` etc.

The list of supported formulae and examples are given below

## Supported Formulae

Currently supported styles are as follows.

| Formula | CSS Property     | Example Usage                                    |
|---------|------------------|--------------------------------------------------|
| `p`     | `padding`        | `p10` will translate to `padding: 10px`          |
| `pt`    | `padding-top`    | `pt20` will translate to `padding-top: 20px;`    |
| `pb`    | `padding-bottom` | `pb10` will translate to `padding-bottom: 10px;` |
| `pr`    | `padding-right`  | `pr20` will translate to `padding-right: 20px;`  |
| `pl`    | `padding-left`   | `pl23` will translate to `padding-left: 23px;`   |
| `m`     | `margin`         | `m20` will translate to `margin: 20px`           |
| `mt`    | `margin-top`     | `mt20` will translate to `margin-top: 20px;`     |
| `mb`    | `margin-bottom`  | `mb20` will translate to `margin-bottom: 20px;`  |
| `ml`    | `margin-left`    | `ml50` will translate to `margin-left: 50px;`    |
| `mr`    | `margin-right`   | `mr30` will translate to `margin-right: 30px;`   |
| `w`     | `width`          | `w200` will translate to `width: 200px`          |
| `h`     | `height`         | `h60` will translate to `height: 60px;`          |
| `br`    | `border-radius`  | `br5` will translate to `border-radius: 5px;`    |
| `fs`    | `font-size`      | `fs15` will translate to `font-size: 15px`       |
| `fw`    | `font-weight`    | `fw400` will translate to `font-weight: 400px`   |
| `lh`    | `line-height`    | `lh20em` will translate to `line-height: 20em`   |
| `t`     | `top`            | `t6` will translate to `top: 6px;`               |
| `l`     | `left`           | `l30` will translate to `left: 30px`             |
| `b`     | `bottom`         | `b20em` will translate to `bottom: 20em;`        |
| `r`     | `right`          | `r20em` will translate to `right: 20em;`         |


## Notes for Units

All the default CSS units are supported. You can specify it and relevant CSS unit will be used

- Units including `px, pt, em, p, vh, vw, vmin, ex, cm, in, mm, pc` will translate to the same unit in CSS
- If you don't provide any unit `px` will be used
- If you need `%` specify it as `p` e.g. `w50p` will get translated to `width: 50%`
- If no unit is needed, specify `n` e.g. `fw600n` will translate to `font-weight: 600`

## Install

Install it using `npm`

```bash
$ npm install --save-dev gulp-css-tailor
```

### Create a Gulp task

Create a gulp task similar to the following

```javascript

var tailor = require('gulp-css-tailor');

gulp.task('tailor', function () {

  // Process all the HTML files in templates dir
  gulp.src('templates/**/*.html')
    .pipe(tailor({
        filename: 'tailored.css',  // Name of the file that will be generated [default: 'tailored.css']
        minifyOutput: false,       // Whether to minify the generated CSS or not [default: false]
        tabSpacing: 4,             // Tab spacing when `minifyOutput` is disabled [default: 4]
        setImportant: false        // Will add the `!important` flag to all the CSS properties
    }))
    .pipe(gulp.dest('assets/css')); // Directory where CSS is to be generated

});
```

And run `gulp tailor`, it will find all the tailorable classes and generate the CSS at the required destination

### Options

Arguments are optional by default, however, you can pass a variety of them to modify the generated CSS file.

```js
var options = {
    filename: 'tailored.css',  // Name of the file that will be generated [default: 'tailored.css']
    minifyOutput: false,       // Whether to minify the generated CSS or not [default: false]
    tabSpacing: 4,             // Tab spacing when `minifyOutput` is disabled [default: 4]
    setImportant: false        // Will add the `!important` flag to all the CSS properties
};
```

For further usage examples, check the [examples directory](https://github.com/kamranahmedse/gulp-css-tailor/blob/master/examples/gulpfile.js)


## Side Note

This plugin is based upon [CSS Tailor](https://github.com/kamranahmedse/css-tailor). If you would like to use this functionality programmatically or use with some other task runner, make sure to check [kamranahmedse/css-tailor](https://github.com/kamranahmedse/css-tailor)

## Related

- Powered by [css-tailor](http://github.com/kamranahmedse/css-tailor)

## License

MIT &copy; [Kamran Ahmed](http://kamranahmed.info)
