[![npm version](http://b.adge.me/npm/v/grunt-sass-imports.svg) &nbsp; [![gittip donate](http://b.adge.me/:gittip-donate-lightgrey.svg)](https://www.gittip.com/ITspirit/) 

---

# grunt-sass-imports

> A grunt task to create sass/scss @import statements from a collection of stylesheet files.

Why use this? To get useful error messages from the sass/scss parser, that tell you in what file the error was encountered!
sass/scss uses @import statements to aggregate files and will tell you about parsing errors in those files.
But maintaining these statements by hand is a pain. In order to automatically aggregate all the style files in a project,
a method of first concatenating the files before parsing is widely used. This works but you loose the valuable
information about where to fix your mistakes.

So, automate @import creation with this plugin and use the resulting file as the source for the sass/scss parser.

By default any .css source files are inlined in the output before the @import statements for the sass/scss files start.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the
[Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a
[Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with
that process, you may install this plugin with this command:

```shell
npm install grunt-sass-imports --save-dev
```

`--save-dev` adds the plugin to your devDependencies.

Once the plugin has been installed, load it in your `Gruntfile.js` like so:

```js
grunt.loadNpmTasks('grunt-sass-imports');
```

## The "sass_imports" task

### Overview
In your project's Gruntfile, add a section named `sass_imports` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  sass_imports: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    }
  }
})
```

### Options

In addition grunt-glue-nu has a few configuration options that are not passed on to glue.

- **options.inlineCSS** `{Boolean} true` – By default any .css source files are inlined in the output before the @import statements for the sass/scss files start.
                                                  sass/scss itself will generate CSS from `.sass` @import statements, but any `.css` @imports are left as is. If that's the behavior
                                                  you want, set `inlineCSS` to false. The @imports will be created in order of the provided files.

- **options.banner** `{String} "// This file was generated by grunt-sass-imports"` – This option contains the banner that is added to the beginning of the generated output file.



```js
grunt.initConfig({
  sass_imports: {
    options: {
      inlineCSS: false // default: true
    },
    src: [ 'styles/*.css', 'styles/*.sass'],
    dest: 'dist/imports.sass'
  }
})
```

---

### Usage Examples

#### Using src and dest
In this example, `src` and `dest` properties are used to specify input files and the output file.

```js
grunt.initConfig({
  sass_imports: {
    options: {
      inlineCSS: true
    },
    src: [ 'styles/*.css', 'styles/*.sass'],
    dest: 'dist/imports.sass'
  }
})
```

#### Using 'files' shorthand notation
In this example, a `files` shorthand is used to specify input files and the output file.

```js
grunt.initConfig({
  sass_imports: {
    options: {
    },
    files: {
      'dist/imports.sass': ['styles/styles.css', 'styles/styles.sass']
    }
  }
})
```

## Troubleshooting

	Warning: Arguments to path.join must be strings

Most likely caused by a change in Node 0.10.0. Fixed in Grunt 0.4.1.
Update grunt and grunt-cli.


## Release History
see [CHANGELOG.md](CHANGELOG.md)
