# web-font-loading-recipes

A bunch of demos for different web font loading strategies. Companion to https://www.zachleat.com/web/comprehensive-webfonts/


## Recommended Methods

As web fonts are a progressive enhancement and with increasing support for the CSS Font Loading API, we can look forward to a time in which we won’t need to inline a polyfill into the header (for even faster font loading). The simplified CSS Font Loading API recipes are the defaults, but polyfilled versions may also be included for broader browser support for your web fonts.

* [`font-display`](./font-display.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/font-display.html) _(4 web fonts)_: FOUT using a single CSS descriptor.
* [`preload`](./preload.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/preload.html) _(4 web fonts—1 preloaded)_
* [FOUT with a Class](./fout-with-class.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class.html) _(4 web fonts)_
  * or [using a polyfill](./fout-with-class-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class-polyfill.html) _(4 web fonts)_
* [FOFT](./foft.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/foft.html) _(5 web fonts, two are the same—but only loaded once)_
  * or [using a polyfill](./foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/foft-polyfill.html) _(4 web fonts)_
* [FOFT using only `font-display`](./font-display-mix.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/font-display-mix.html) _(4 web fonts—1 `swap` / 3 `optional`)_
* [Critical FOFT](./critical-foft.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft.html) _(5 web fonts—1 subset)_
  * or [using a polyfill](./critical-foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-polyfill.html) _(4 web fonts)_
* [Critical FOFT with Data URI](critical-foft-data-uri.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri.html) _(5 web fonts—1 subset inline Data URI)_
  * or [using a polyfill](./critical-foft-data-uri-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri-polyfill.html) _(5 web fonts—1 subset inline Data URI)_
* [Critical FOFT with `preload`](./critical-foft-preload.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload.html) _(5 web fonts—1 subset)_
  * or [using a polyfill](./critical-foft-preload-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload-polyfill.html) _(5 web fonts—1 subset)_

## Not Recommended but included for Posterity

* [System fonts](./dont.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/dont.html) _(0 web fonts)_
* [Unceremonious Web Fonts](./unceremonious-font-face.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-font-face.html) _(4 web fonts)_
* [Unceremonious Faux Web Fonts](./unceremonious-faux-font-face.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-faux-font-face.html) _(1 web font)_: Bold and italic variants are rendered using [font-synthesis](https://www.zachleat.com/web/webfont-glossary/#font-synthesis)

### Deprecated Methods

* [Inline Data URI](./inline-data-uri.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/inline-data-uri.html) _(4 web fonts)_
* [Asynchronous Data URI](./async-data-uri.html)
  * [Demo](https://www.zachleat.com/web-fonts/demos/async-data-uri.html) _(4 web fonts)_

### Failed Experiments

* [`@supports` and `font-display`](failed-supports.html)
  * **Failed** because you can’t use @supports on font-face descriptors.
  * [Demo](https://www.zachleat.com/web-fonts/demos/failed-supports.html)
