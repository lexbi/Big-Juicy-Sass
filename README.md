Big Juicy Sass
==============

My own boilerplate for a typical CraftCMS setup. Filled with useful craft configs, templates, js, and css.

![Big Juicy Sass](http://i.imgur.com/4SJeSlz.gif "from 'Drop girl' by IceCube")

## Gulp

My gulp setup has several tasks which uses:

- Path variables for a easy/quick setup
- SASS/JS compiler/linter/sourcemaps
- Image minifier (imagemin) task using pngquant (lossless) & jpeg recompress
- Watch task - watches js/sass/template files and uses livereload

## Bower

### SASS/SCSS/CSS

Includes:

- SASS REM (bower) - [https://github.com/ry5n/rem/](https://github.com/ry5n/rem/)
- Normalize.css (bower) - [http://necolas.github.io/normalize.css/](http://necolas.github.io/normalize.css/)
- Font Awesome (bower) - [http://fortawesome.github.io/Font-Awesome/](http://fortawesome.github.io/Font-Awesome/)
- Materialize - generally only use the parallax js plugin

### JS/jQuery
- jQuery 1.11.3 (CDN & local fallback (bower))
- jQuery 2.1.4 (CDN & local fallback (bower))
- GSAP (bower) - [http://greensock.com/gsap](http://greensock.com/gsap)
- Modernizr.js - (bower) [https://modernizr.com/](https://modernizr.com/)
- Moment.js - (bower) [http://momentjs.com](http://momentjs.com)
- Magnific Popup (bower) - [https://github.com/dimsemenov/magnific-popup](https://github.com/dimsemenov/magnific-popup)
- Photoswipe (bower)
- Slick Carousel (bower) - [http://kenwheeler.github.io/slick/](http://kenwheeler.github.io/slick)
- jQuery Validate (bower) - [https://github.com/jzaefferer/jquery-validation](https://github.com/jzaefferer/jquery-validation)
- Waypoints.js (bower) - [https://github.com/imakewebthings/jquery-waypoints](https://github.com/imakewebthings/jquery-waypoints)
- html5shiv (bower) - [https://github.com/afarkas/html5shiv](https://github.com/afarkas/html5shiv)
- FitText.js
- isotope.js
- MatchHeight.js

# CraftCMS Plugins

I'm not going to include any plugins within this repo because they are all updated very frequently, and, their use is very much situational dependent on the project & the client.

### FormBuilder2
[https://github.com/roundhouse/FormBuilder-2-Craft-CMS](https://github.com/roundhouse/FormBuilder-2-Craft-CMS)<br> [https://github.com/roundhouse/FormBuilder-2-Craft-CMS/archive/master.zip](https://github.com/roundhouse/FormBuilder-2-Craft-CMS/archive/master.zip)

Formbuilder2 is probably the best free solution for the time being.

### Freeform
[https://solspace.com/craft/freeform](https://solspace.com/craft/freeform)

Not tried it yet, but, their ExpressionEngine plugin was the best for it's time. $99 price tag maybe off putting, though it might be the best optino.

### Minify
[https://github.com/nystudio107/minify](https://github.com/nystudio107/minify)<br>
[https://github.com/nystudio107/minify/archive/master.zip](https://github.com/nystudio107/minify/archive/master.zip)

A simple plugin that allows you to minify code, a more vigorous version of the twig tags "spaceless"

### FeedMe
[https://github.com/engram-design/FeedMe](https://github.com/engram-design/FeedMe)<br>
[https://github.com/engram-design/FeedMe/archive/master.zip](https://github.com/engram-design/FeedMe/archive/master.zip)

This is probably the only plugin I have found that is worth using without major issues. You can either import entries from JSON, RSS, XML, and you can even import data into a matrix field!

### File Get Contents
[https://github.com/lexbi/File-Get-Contents-Plugin---CraftCMS](https://github.com/lexbi/File-Get-Contents-Plugin---CraftCMS)<br>
[https://github.com/lexbi/File-Get-Contents-Plugin---CraftCMS/archive/master.zip](https://github.com/lexbi/File-Get-Contents-Plugin---CraftCMS/archive/master.zip)

A very simple plugin which makes a handful of php functions available in CraftCMS templates. This is mainly utilised to inject CSS into the head element to get that all important high Google Page Speed score.

### Image Resizer

[https://github.com/engram-design/ImageResizer](https://github.com/engram-design/ImageResizer)<br>
[https://github.com/engram-design/ImageResizer/archive/master.zip](https://github.com/engram-design/ImageResizer/archive/master.zip)

Quite often it is the case that the users that have been provided access to a CMS unfortunately are not very technical. This has often resulted in dramatically large images being uploaded to a CMS, as an example this could be an image with dimensions of 8000px x 6000px, this plugin resizes images like that to parameters that you can set in the backend. I normally set this to be a max width & height of 2000px, which saves server space, and, potentially a broken webpage.

### Imager
[https://github.com/aelvan/Imager-Craft](https://github.com/aelvan/Imager-Craft)<br>
[https://github.com/aelvan/Imager-Craft/archive/master.zip](https://github.com/aelvan/Imager-Craft/archive/master.zip)

Imager allows you to optimise the images in your templates... Basically, the plugin replace's Craft's built in image transforms, Craft, unfortunately, does not optimise your images _that_ well. Imager utilises lossy compression with [pngquant](https://pngquant.org/) for pngs (similar to [TinyPNG](https://tinypng.com/) compression), and other jpg compression such as [mozjpeg](https://github.com/mozilla/mozjpeg) This plugin allows you to utilise the srcset attribute to it's full potential, and creates individual images for every width  you set. Here is an example:

    {% set transformedImages = craft.imager.transformImage(img, [
        { width: 1200 },
        { width: 1000 },
        { width: 800 },
        { width: 600, jpegQuality: 75 },
        { width: 400, jpegQuality: 70 }
        ], { ratio: 4/3, mode: "fit", jpegQuality: 80 }) %}

    <figure>
        <a href="{{ img.url }}">
            <img src="{{ craft.imager.base64Pixel(4, 3) }}" srcset="{{ craft.imager.srcset(transformedImages) }}" alt="{{ img.alt }}" title="{{ img.title }}">
        </a>
        {% if img.caption %}
            <figcaption>{{ img.caption }}</figcaption>
        {% endif %}
    </figure>

### Hacksaw
[https://github.com/ryanshrum/hacksaw](https://github.com/ryanshrum/hacksaw)<br>
[https://github.com/ryanshrum/hacksaw/archive/master.zip](https://github.com/ryanshrum/hacksaw/archive/master.zip)

A simple text truncation plugin for Craft CMS that takes your content and hacks it down to more manageable sizes.

### Client Widgets
[https://github.com/lexbi/craftcms-dashboard-client-widgets](https://github.com/lexbi/craftcms-dashboard-client-widgets)<br>
[https://github.com/lexbi/craftcms-dashboard-client-widgets/archive/master.zip](https://github.com/lexbi/craftcms-dashboard-client-widgets/archive/master.zip)

My own creation, this adds the ability to add a few widgets to the dashboard which attempt to give a decent explanation between singles, channels & structures to a user that may not be familiar with CraftCMS.

### Asset Links
[https://github.com/Hambrook/AssetLinks](https://github.com/Hambrook/AssetLinks)<br>
[https://github.com/Hambrook/AssetLinks/archive/master.zip](https://github.com/Hambrook/AssetLinks/archive/master.zip)

This adds a download icon to the backend where assets are used. CraftCMS doesn't make it easy to actually download the asset when you have selected one on an entry.

### Control Panel CSS

[https://github.com/lindseydiloreto/craft-cpcss](https://github.com/lindseydiloreto/craft-cpcss)<br>
[https://github.com/lindseydiloreto/craft-cpcss/archive/master.zip](https://github.com/lindseydiloreto/craft-cpcss/archive/master.zip)

This plugin lets you add styles to the dashboard/control panel area in CraftCMS.

### Reasons
[https://github.com/mmikkel/Reasons-Craft](https://github.com/mmikkel/Reasons-Craft)<br>
[https://github.com/mmikkel/Reasons-Craft/archive/master.zip](https://github.com/mmikkel/Reasons-Craft/archive/master.zip)

This plugin lets you show & hide fields dependent on the result entered for another. You could setup some behaviour where if a checkbox was checked, that could either hide existing, or, show additional fields on that entry.
