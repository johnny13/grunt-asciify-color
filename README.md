# grunt-asciify-color

**GruntJS Ascii awesomness** (now in technicolor). This grunt task is perfect if you want to sex up your banners and/or drop some ascii hotness into your logs.

```
    _____     __________________  .___ .___ ________________.___.._.
   /  _  \   /   _____/\_   ___ \ |   ||   |\_   _____/\__  |   || |
  /  /_\  \  \_____  \ /    \  \/ |   ||   | |    __)   /   |   || |
 /    |    \ /        \\     \____|   ||   | |     \    \____   | \|
 \____|__  //_______  / \______  /|___||___| \___  /    / ______| __
         \/         \/         \/                \/     \/        \/
```
[![Dependency Status](https://david-dm.org/olizilla/grunt-asciify.png)](https://github.com/johnny13/grunt-asciify-color)
[![Build Status](https://travis-ci.org/olizilla/grunt-asciify.png)](https://github.com/johnny13/grunt-asciify-color)

Running the asciify task as configured below will push your **ascii-awesome** text into property called `asciify_myBanner` which can then be used else where, as the template for an awesome file banner for example.

```js
asciify: {
  myBanner: {
    text: 'Text to asciify',
		font  : "graffiti",
		color : "red",
	}
},
uglify:{
  options: {
    banner: '/*!\n <%= asciify_myBanner %> \n*/\n'
  },
  all:{
    src:'Gruntfile.js',
    dest:'Gruntfile.withbanner.min.js'        
  }
}
```
Asciify picks a property name to store the output by prepending your target name with `asciify_`. In the above example we used `myBanner` as the target, so the property name became `asciify_myBanner`.

## Getting Started
This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-asciify-color --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-asciify-color');
```

## The "asciify" task

In your project's Gruntfile, add a section named `asciify` to the data object passed into `grunt.initConfig()`.

### Options

#### Default Options
```js
options:{
  font:'graffiti'
  log:false,
	color:'red'
}
```

#### options.font
Type: `String`
Default value: `graffiti`

The name of the figlet font to use. View the [font list](https://github.com/olizilla/figlet-js/tree/master/fonts) and [examples](http://www.figlet.org/examples.html). Use the [asciify](https://npmjs.org/package/asciify) module to show all fonts for your text: `asciify -a "All The Fonts!"`.

#### options.log
Type: `Boolean`
Default value: `false`

Write your asciified text to the console

![asciify options.log=true](https://raw.github.com/olizilla/grunt-asciify/master/doc/grunt-asciify.png)

#### options.color
Type: `String`
Default value: `red`

Use any color supported by **chalk**, the NodeJS color library.

### Usage Examples

```js
grunt.initConfig({
    
  asciify: { 
    banner:{
      text: 'GRUNT-ASCIIFY!',
      
      // Add the awesome to the console, and use the best font.
      options:{ 
        font:'graffiti',
        log:true,
				color:'blue'
      }
    }
  },

  
  uglify:{
    
    // Use the property holding our awesomised text in the banner template      
    options: {
      banner: '/*!\n <%= asciify_banner %> \n*/\n'
    },
    all:{
      src:'Gruntfile.js',
      dest:'Grunfile.withbanner.min.js'
    }
  }
});

grunt.loadNpmTasks('grunt-asciify-color');
grunt.loadNpmTasks('grunt-contrib-uglify');

// Run asciify before uglify so the asciify_banner property is available.
grunt.registerTask('default', ['asciify', 'uglify']);
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
* 0.0.1 - IT BEGINS. ASCII BANNERS NOW MANDTORY.
