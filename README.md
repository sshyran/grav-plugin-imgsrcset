# [Grav](http://getgrav.org/) Image Srcset Plugin

Adds a `srcset`-attribute to `img`-elements to allow for responsive images in Markdown. This allows [modern browsers](http://caniuse.com/#feat=srcset) to load the image which best fits within the viewport, based on available images and sizes, essentially choosing the best image to reduce loading times (see [RespImg](https://responsiveimages.org/)).

Thus, on a small mobile screen this would load a much smaller image than on a large desktop. From this:

	<img title="Street view from the east" alt="Street view" src="street.jpg">
	
To this:

	<img title="Street view from the east" alt="Street view" src="street.jpg" srcset="street-320.jpg 320w, street-480.jpg 480w, street-640.jpg 640w, street-960.jpg 960w, street-1280.jpg 1280w, street-1600.jpg 1600w, street-1920.jpg 1920w, street-2240.jpg 2240w" sizes="100vw">

This is only applied to image-elements generated from Markdown. Depends on [PHP Html Parser v1.7.0](https://github.com/paquettg/php-html-parser/) for DOM parsing and manipulation of `srcset` `sizes`.

# Installation and Configuration

1. Download the zip version of [this repository](https://github.com/OleVik/grav-plugin-imgsrcset) and unzip it under `/your/site/grav/user/plugins`.
2. Rename the folder to `imgsrcset`.

You should now have all the plugin files under

    /your/site/grav/user/plugins/imgsrcset

The plugin is enabled by default, and can be disabled by copying `user/plugins/imgcaptions/imgsrcset.yaml` into `user/config/plugins/imgsrcset.yaml` and setting `enabled: false`. For a simple Twig-integration see [this gist](https://gist.github.com/OleVik/a7604215f127763b71bd8b8788d45cfd), and for an example of generating responsive images with Gulp see [this gist](https://gist.github.com/OleVik/f2c8b51a7153743b13607072c27cf8d2).

## Widths

The `widths` setting is a YAML sequence wherein each integer represents the width of the image, defaulting to:

	 - 320
	 - 480
	 - 640
	 - 960
	 - 1280
	 - 1600
	 - 1920
	 - 2240
	 
## Sizes

The `widths` setting is a YAML string defining the [sizes](https://html.spec.whatwg.org/multipage/embedded-content.html#attr-img-sizes)-attribute, defaulting to:

	sizes: "100vw"

## Images

The plugin expects the images to be in the same folder as the source image. So, for the case of `street.jpg`, the page folder should contain:

	street.jpg
	street-320.jpg
	street-480.jpg
	street-640.jpg
	street-960.jpg
	street-1280.jpg
	street-1600.jpg
	street-1920.jpg
	street-2240.jpg

MIT License 2016 by [Ole Vik](http://github.com/olevik).