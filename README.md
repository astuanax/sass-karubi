sass-karubi
===============

Bootstrap based starterkit for well organized sass projects.

- Automatically create color scheme variations 
- Build media query based stylesheets.
- Above the fold seprated stylesheet. (WIP)

The sass-karubi kit generates several stylesheet that can be loaded to optimise the loading time of your pages
according to the device being loaded. 
Additionaly it will generate several different color schemes for your pages
generating a myriad of themes and possibilities


## Installation

Sass-starterkit depends on **compass**, **bootstrap-sass**, **color-schemer**, **autoprefixer** and **jacket**.

- bootstrap-sass: https://github.com/twbs/bootstrap-sass#installation
	- variable and the bootstrap stylesheet are already in the project. No need to bundle it. 
- color-schemer: https://github.com/Team-Sass/color-schemer#install
- autoprefixer: https://github.com/ai/autoprefixer#compass
- jacket: https://github.com/Team-Sass/jacket#installation


## Usage

Sass-karubi is based on compass, so all you need to do is `compass compile` to get the stylesheets generated

### Color schemes.

The default color scheme comes close to the values from the initial bootstrap file, and can be found in the colors folder in the file _variation-1.scss.

The color-schemer gem provides a choice of color schemes generators, but for now only the *tetrad* variation is used.
For more information on using color-schemer have a look at the documentation: https://github.com/Team-Sass/color-schemer

The default values are set in _base.scss and are: 

```sass
$cs-primary : #428bca;
$cs-scheme : tetrad; // mono, complement, triad, tetrad, analogic, accented-analogic
$cs-color-model: ryb;

$primary: cs-primary() !default;
$primary-light : ryb-adjust-hue(tint(set-saturation(cs-primary(), 60%),40),-8deg) !default;
$secondary: cs-secondary() !default; 
$tertiary: ryb-adjust-hue(set-saturation(cs-tertiary(), 100%),17deg) !default;
$quadrary : cs-quadrary() !default;
```

### Above the fold CSS

For each color scheme there are 2 CSS files being generated: a stylesheet with a '-fold' affix. This stylesheet should be loaded in the `head`of the html page.
The other stylesheet can be lazy loaded with the following javascript snippet from the Google speed documentation. 

```javascript
<script>
      var cb = function() {
        var l = document.createElement('link'); l.rel = 'stylesheet';
        l.href = 'assets/css/main.css';
        var h = document.getElementsByTagName('head')[0]; h.parentNode.insertBefore(l, h);
      };
      var raf = requestAnimationFrame || mozRequestAnimationFrame ||
          webkitRequestAnimationFrame || msRequestAnimationFrame;
      if (raf) raf(cb);
      else window.addEventListener('load', cb);
    </script>
```
[Google Speed](https://developers.google.com/speed/docs/insights/OptimizeCSSDelivery#example)

## Name

This project is named after the mythological cherub or karubi. 
A karubi is envisaged as blue or golden, in the form of a man with a four-fold head standing on wheels.

