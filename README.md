# React Whammy: A React Component for Real Time JavaScript WebM Encoder

This is a React Component for the original JS Library > [Whammy](https://github.com/antimatter15/whammy).

For detail explanation, please visit original library. Essentially, this is a library to convert Canvases into a .webm using JS with easy to use API and adjustable FPS.

All the credit goes to the original creator, this library just fixed some critical [bugs](https://github.com/antimatter15/whammy/issues/43) and convert to React Component.

## Demo (Using Chrome)

http://antimatter15.github.com/whammy/clock.html

http://www.sysord.fr/Sysord/ressource_whammy.jsf

## Basic Usage

Install and import it into the react project

	npm -i s react-whammy
	import Whammy from 'react-whammy'

Initialise the Encoder

	var encoder = new Whammy.Video(15)

That `15` over there is the frame rate.

Add Canvas

	encoder.add(context or canvas or dataURL);

Here, you can add a frame, this happens fairly quickly because basically all it's doing is running `.toDataURL()` on the canvas (which isn't exactly a speed-demon either, but it's acceptable enough most of the time) and plopping the result onto an array (no computation or anything). The actual encoding only happens when you call `.compile()`

	encoder.compile(false, (output) => {
		const video = URL.createObjectURL(output)
	})

And you're done. Awesome.
