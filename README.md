# web-font-loading-recipes

A bunch of demos for different web font loading strategies. Companion to https://www.zachleat.com/web/comprehensive-webfonts/


## Recommended Methods

As web fonts are a progressive enhancement and with increasing support for the CSS Font Loading API, we can look forward to a time in which we won’t need to inline a polyfill into the header (for even faster font loading). The simplified CSS Font Loading API recipes are the defaults, but polyfilled versions may also be included for broader browser support for your web fonts.

* [`font-display`](./font-display.html) (4 web fonts): FOUT using a single CSS descriptor.
* [`preload`](./preload.html) (4 web fonts, 1 preloaded)
* [FOUT with a Class](./fout-with-class.html), or [using a polyfill](./fout-with-class-polyfill.html) (4 web fonts)
* [FOFT, or FOUT with Two Stage Render](./foft.html), or [using a polyfill](./foft-polyfill.html) (4 web fonts)

## Paired Approaches (Advanced font loading)

Combining one or more font loading methods for improved results.

* Critical FOFT
* Critical FOFT with Data URI
* Critical FOFT with `preload`

## Included for Posterity

* [System fonts (no Web Fonts)](./dont.html) (0 web fonts)
* [Unceremonious Web Fonts](./unceremonious-font-face.html) (4 web fonts)
* [Unceremonious Faux Web Fonts](./unceremonious-faux-font-face.html) (1 web font): Bold and italic variants are rendered using [font-synthesis](https://www.zachleat.com/web/webfont-glossary/#font-synthesis)

## Deprecated Methods

* Inline Data URI
* Asynchronous Data URI

## Failed Experiments

Things I’ve tried that I wish had worked but didn’t.

