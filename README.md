baguetteBox.js
==============

[![GitHub version](https://badge.fury.io/gh/feimosi%2FbaguetteBox.js.svg)](https://badge.fury.io/gh/feimosi%2FbaguetteBox.js)
[![Dependency Status](https://img.shields.io/david/feimosi/baguetteBox.js.svg)](https://david-dm.org/feimosi/baguetteBox.js)
[![GitHub license](https://img.shields.io/npm/l/baguettebox.js.svg)]()

Simple and easy to use lightbox script.

[Demo page](https://feimosi.github.io/baguetteBox.js/)

![Demo Page screenshot](http://i.imgur.com/uLSDpuW.png)

## Features

* Written in pure JavaScript, no dependencies required
* Multiple-gallery support, allows custom options for each 
* Supports swipe gestures on touch-screen devices
* Full screen mode available
* Modern and minimal look
* Image captions support
* Responsive images
* CSS3 transitions
* SVG buttons, no extra files to download
* Around 2.7KB gzipped

## Installation

### npm

`npm install baguettebox.js`

### Bower

`bower install baguettebox.js`

### Manually

1. Download `baguetteBox.min.css` and `baguetteBox.min.js` files from `dist` folder.
2. Include them somewhere in your document:

  ```html
<link rel="stylesheet" href="css/baguetteBox.min.css">
<script src="js/baguetteBox.min.js" async></script>
  ```

## Usage

Initialize the script by running:
```js
baguetteBox.run('.gallery');
```
where the first argument is a selector to a gallery (or galleries) containing `a` tags. The HTML code may look like this:
```html
<div class="gallery">
	<a href="img/2-1.jpg" data-caption="Image caption"><img src="img/thumbs/2-1.jpg"></a>
	<a href="img/2-2.jpg"><img src="img/thumbs/2-2.jpg"></a>
  ...
</div>
```

To use captions put `title` or `data-caption` attribute on `a` tag.

## Customization

You can pass an object with custom options as a second parameter. 
```js
baguetteBox.run('.gallery', {
  // Custom options
});
```
The following options are available:

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `captions` | `Boolean` \| `function(element)` | `true` | Display image captions. Passing a function will use a string returned by this callback. The only argument is `a` element containing the image. Invoked in the context of the current gallery array |
| `buttons` | `Boolean` \| `'auto'` | `'auto'` | Display buttons. `'auto'` hides buttons on touch-enabled devices or when only one image is available |
| `fullScreen` | `Boolean` | `false` | Enable full screen mode |
| `noScrollbars` | `Boolean` | `false` | Hide scrollbars when gallery is displayed |
| `titleTag` | `Boolean` | `false` | Use caption value also in the gallery `img.title` attribute |
| `async` | `Boolean` | `false` | Load files asynchronously |
| `preload` | `Number` | `2` | How many files should be preloaded |
| `animation` | `'slideIn'` \| `'fadeIn'` \| `false` | `'slideIn'` | Animation type |
| `afterShow` | `function` | `null` | Callback to be run after showing the overlay |
| `afterHide` | `function` | `null` | Callback to be run after hiding the overlay |
| `onChange` | `function(currentIndex, imagesCount)` | `null` | Callback to be run when image changes |
| `overlayBackgroundColor` | `String` | `'rgba (0,0,0,.8)'` | Background color for the lightbox overlay |
| `filter` | `RegExp` | `/.+\.(gif|jpe?g|png|webp)/i` | Pattern to match image files. Applied to the `a.href` attribute |

## API

* `run` - initialize baguetteBox.js
* `showNext` - switch to the next image
* `showPrevious` - switch to the previous image
* `destroy` - remove the plugin with any event bindings
* `showGallery` - show the gallery with the given id (returned from `run`)

The first two methods return true on success or false if there's no more images to be loaded.

## Responsive images

To use this feature, simply put `data-at-{width}` attributes on `a` tags with value being a path to the desired image. `{width}` should be the maximum screen width the image can be displayed at. The script chooses the first image with `{width}` greater than or equal to the current screen width for best user experience.
That last `data-at-X` image is used also in the case of a screen larger than X.

Here's an example of what the HTML code can look like:
```html
<a href="img/2-1.jpg" 
  data-at-450="img/thumbs/2-1.jpg" 
  data-at-800="img/small/2-1.jpg" 
  data-at-1366="img/medium/2-1.jpg" 
  data-at-1920="img/big/2-1.jpg">
    <img src="img/thumbs/2-1.jpg">
</a>
```
If you have 1366x768 resolution baguetteBox.js will choose `"img/medium/2-1.jpg"`. If, however, it's 1440x900 it'll choose `"img/big/2-1.jpg"`. Keep `href` attribute as a fallback (link to a bigger image e.g. of HD size) for older browsers.

## Compatibility

* IE 8+
* Chrome
* Firefox 3.6+
* Opera 12+
* Safari 5+

## Notes

Feel free to report any issues!

## Credits

Creation of `baguetteBox.js` was inspired by a great jQuery plugin [touchTouch](https://github.com/martinaglv/touchTouch).

## License

Copyright (c) 2016 [feimosi](https://github.com/feimosi/)

This content is released under the [MIT License](http://opensource.org/licenses/MIT).
