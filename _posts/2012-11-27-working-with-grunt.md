---
layout: post
title: Working with Grunt
date: 2012-11-27 10:54:10
author: Steve Rydz
---

A few weeks ago I attended a series of tooling workshops in Brighton. One of the workshops was focused around build process, and particularly [Grunt](http://gruntjs.com).

Currently we use [CodeKit](http://incident57.com/codekit/) to compile our Less and JavaScript files so we end up with concatenated, minified versions of each. So far this has worked well but we have found it difficult to keep things synchronised between team members.

Soon after returning from the workshops I started to investigate Grunt in more detail and we put a plan in place on how we could use it to aid our build process.

What we came up with was the following file structure:

		Site_Name/
			|__ public/
			|			|__ static/
			|			|			|__ css/
			|		  	|			|__ js/
			|			|			|__ img/
			|			|
			|			|__ index.html
			|
			|__ spec/
			|
			|__ static-src/
			|			|__ less/
			|			|__ js/
			|
			|__ grunt.js
			|__ README.md

### public
The public directory contains anything public facing, including all static assets such as stylesheets, scripts and images. Anything in the <code>static/css/</code> and <code>static/js/</code> directories is compiled from <code>static-src/</code>.

### spec
The spec directory contains our selenium tests.

### static-src
This is where we keep all of our pre-compiled files. 

### Compiling LESS
Our Less files are broken down into modules. There is a master file that imports all dependencies. This master file is then compiled into CSS, minified and placed in the <code>static/css/</code> directory.

### Compiling JavaScript
Just like our Less files, all our JavaScript is broken down into modules. These are then concatenated to a master JavaScript file which is placed in the <code>static/js/</code> directory. We also create a minified version for production which sits alongside the master file in the <code>static/js/</code> directory.

### Enter Grunt
Grunt makes the process of performing all of the above tasks very simple. Everything is defined inside our <code>grunt.js</code> file:

    module.exports = function(grunt) {

      grunt.initConfig({
        lint: {
          files: ['static-src/js/*.js']
        },
        less: {
          development: {
            options: {
              paths: ['static-src/less/'],
              yuicompress: true
            },
            files: {
              'public/static/css/master.css': 'static-src/less/master.less'
            }
          }
        },
        concat: {
          dist: {
            src: [
              'static-src/js/lib/jquery/jquery.js',
              'static-src/js/lib/jquery/jquery.cookie.js',
              'static-src/js/app.js'
            ],
            dest: 'public/static/js/master.js'
          }
        },
        min: {
          dist: {
            src: 'public/static/js/master.js',
            dest: 'public/static/js/master.min.js'
          }
        },
        watch: {
          files: ['static-src/js/*.js', 'static-src/less/*.less'],
          tasks: 'default'
        }
      });

      grunt.loadNpmTasks('grunt-contrib-less');
      
      grunt.registerTask('default', 'lint less concat min');

    };

### Extending Grunt
Grunt is very extensible and here we are using it in it's most basic form using (with the exception of Less) only it's built-in tasks. The goal here was to become less reliant on a third-part app such as CodeKit in favour of a platform that we can easily build upon.

Going forward, this is likely to be the way we do things. We will no doubt build on this in time, making use of more advanced features, and maybe even build some tasks of our own, but even as it stands, this is a good position for us to be in.

