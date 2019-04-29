# Front-end Boilerplate using Sass and Gulp 4

Using a set of boilerplate files when you're starting a website project can be a huge time-saver. Instead of having to start from scratch or copy and paste from previous projects, you can get up and running in just a minute or two.

I wanted to share my own boilerplate that I use for simple front-end websites that use HTML, SCSS, and JavaScript. And I'm using Gulp 4 to compile, prefix, and minify my files.

I also wrote a rather detailed walkthrough on how to get up and running with Gulp 4, as well as migration tips from Gulp 3. 

You can read that on my blog [here](https://coder-coder.com/gulp-4-walk-through).

## Quickstart guide

* Clone or download this Git repo onto your computer.
* Install [Node.js](https://nodejs.org/en/) if you don't have it yet.
* Run `npm install`
* Run `gulp` to run the default Gulp task

In this proejct, Gulp is configured to run the following functions:

* Compile the SCSS files to CSS
* Autoprefix and minify the CSS file
* Concatenate the JS files
* Uglify the JS files
* Move final CSS and JS files to the `/dist` folder
 


## Problems Migrating from Gulp 3? 

If you’ve been using Gulp 3 and all you want is to get the dang thing working with Gulp 4, you’re in luck!

The main breaking change involves how you run tasks.

Gulp 4 introduces two new functions to run tasks: series() and parallel(). It gives you the option of running multiple tasks concurrently, or one after the other.

Before, in Gulp 3, you could simply list a single function or multiple functions in an array. However, in Gulp 4, doing so without wrapping them in either series() or parallel() will throw an error now.

Something like:

AssertionError [ERR_ASSERTION]: Task function must be specified


Here’s how you can quickly fix that:


Tasks in (old) Gulp 3 syntax

In Gulp 3, you might have run tasks this way:

gulp.task('default', ['sass', 'js', 'watch']);

gulp.watch('app/scss/*.scss', ['sass']);


Tasks in Gulp 4 syntax

Put those tasks into a series() function like this:

gulp.task('default', gulp.series('sass', 'js', 'watch'));

gulp.watch('app/scss/*.scss', gulp.series('sass'));


And that will fix the task function error with the smallest change possible!