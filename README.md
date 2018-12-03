# web-font-loading-recipes

A bunch of demos for different web font loading strategies. Some of these are included on [A Comprehensive Guide to Font Loading Strategies](https://www.zachleat.com/web/comprehensive-webfonts/), some of them are more _experimental_.

Demos are hosted at https://www.zachleat.com/web-fonts/demos/

## Table of Contents

* [Recommended Methods](#recommended-methods)
* [Further Enhancements](#further-enhancements)
* [Experiments in Progress](#experiments-in-progress)
* [Not Recommended but included for Posterity](#not-recommended-but-included-for-posterity)
* [Anti-patterns and Deprecated Methods](#anti-patterns-and-deprecated-methods)
* [Failed Experiments](#failed-experiments)

## Recommended Methods

As web fonts are a progressive enhancement and with increasing support for the CSS Font Loading API, we can look forward to a time in which we won’t need to inline a polyfill into the header (for even faster font loading). The simplified CSS Font Loading API recipes are the defaults, but polyfilled versions are included for broader browser support—notably only the polyfilled versions will show web fonts in Internet Explorer and Edge web browsers (which do not have support for the CSS Font Loading API).

### `font-display: swap`

* _CSS_: `@font-face` descriptor
* [Code](./font-display.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#font-display)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-display.html)** _(4 web fonts)_

### `preload`

* _HTML_: `<link>` tag
* [Code](./preload.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#preload)
* [Demo](https://www.zachleat.com/web-fonts/demos/preload.html)** _(4 web fonts—1 preloaded)_

### `font-display: swap` with `preload`

* _HTML_: `<link>` tag and _CSS_: `@font-face` descriptor
* [Code](./font-display-preload.html)
* Read more about [`font-display`](https://www.zachleat.com/web/comprehensive-webfonts/#font-display) and [`preload`](https://www.zachleat.com/web/comprehensive-webfonts/#preload)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-display-preload.html)** _(4 web fonts—1 preloaded)_

### FOUT with a Class

* _JavaScript_: CSS Font Loading API
* [Code](./fout-with-class.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#fout-class)
* [Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class.html) _(4 web fonts)_
* or [using a polyfill](./fout-with-class-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/fout-with-class-polyfill.html) _(4 web fonts)_

### FOUT

Similar to the above, but without using a class—using only the CSS Font Loading API. This doesn’t require any modification of the CSS, injects the web fonts using JS programmatically. I first saw this method in the [Webfont Handbook from @bramstein](https://abookapart.com/products/webfont-handbook).

* _JavaScript_: CSS Font Loading API
* [Code](./fout.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/fout.html) _(4 web fonts)_
* Related: `.style.fontFamily` method (only works well with one family per page), first saw this in a [tweet from @simevidas](https://twitter.com/simevidas/status/829016037366566912)

### FOFT

Two stage load, using one Roman font file in the first stage (with font-synthesis).

* _JavaScript_: CSS Font Loading API
* [Code](./foft.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#foft)
* [Demo](https://www.zachleat.com/web-fonts/demos/foft.html) _(5 web fonts, two are the same—but only loaded once)_
* or [using a polyfill](./foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/foft-polyfill.html) _(4 web fonts)_

### Critical FOFT

* _JavaScript_: CSS Font Loading API
* [Code](./critical-foft.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft)
* [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft.html) _(5 web fonts—1 subset)_
* or [using a polyfill](./critical-foft-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-polyfill.html) _(5 web fonts—1 subset)_

### Critical FOFT with Data URI

* _JavaScript_: CSS Font Loading API
* [Code](./critical-foft-data-uri.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft-data-uri)
* [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri.html) _(5 web fonts—1 subset inline Data URI)_
* or [using a polyfill](./critical-foft-data-uri-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-data-uri-polyfill.html) _(5 web fonts—1 subset inline Data URI)_

### Critical FOFT with `preload`

* _HTML_: `<link>` tag and _JavaScript_: CSS Font Loading API
* [Code](./critical-foft-preload.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#critical-foft-preload)
* [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload.html) _(5 web fonts—1 subset)_
* or [using a polyfill](./critical-foft-preload-polyfill.html)—[Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload-polyfill.html) _(5 web fonts—1 subset)_

### The eBay Method

* _JavaScript_: CSS Font Loading API and [FontFaceObserver polyfill](https://github.com/bramstein/fontfaceobserver)
* Code: [HTML](./ebay-method.html) and [Lazy-loaded JavaScript](./ebay-method.js)
* Emulate `font-display: optional` with JavaScript.
  * Notable that it lazy loads the font loading polyfill only if CSS Font Loading API is not supported
* Read more at [eBay’s Font Loading Strategy](http://www.ebaytechblog.com/2017/09/21/ebays-font-loading-strategy/).
* [Demo](https://www.zachleat.com/web-fonts/demos/ebay-method.html) _(4 web fonts)_ (polyfill is lazy loaded when CSS Font Loading API is not supported)

### “The Compromise”: Critical FOFT with `preload`, with a polyfill fallback emulating `font-display: optional`

* _HTML_: `<link>` tag and _JavaScript_: CSS Font Loading API and [FontFaceObserver polyfill](https://github.com/bramstein/fontfaceobserver)
* Code: [HTML](./critical-foft-preload-fallback-optional.html) and [Lazy-loaded JavaScript](./critical-foft-preload-fallback-optional.js)
* [Read more](https://www.zachleat.com/web/the-compromise/)
  * Inspired by the eBay method above.
* [Demo](https://www.zachleat.com/web-fonts/demos/critical-foft-preload-fallback-optional.html) _(5 web fonts—1 subset)_ (polyfill is lazy loaded when CSS Font Loading API is not supported)
* Currently in use on [zachleat.com](https://www.zachleat.com/web/) and [smashingmagazine.com](https://www.smashingmagazine.com/)

## Further Enhancements

These aren’t necessarily font loading strategies on their own but they are extra enhancements you can layer on top of and pair with existing strategies.

### Network Information API

Opt out of web fonts on slow connection speeds.

* [Code](./network-information-api.html) (shown with FOUT approach)
* [Demo](https://www.zachleat.com/web-fonts/demos/network-information-api.html)
* Related blog post: [Should I Use JavaScript to Load My Web Fonts?](https://www.filamentgroup.com/lab/js-web-fonts.html)

### `prefers-reduced-motion` User Preference

Opt out of web fonts when user has enabled `Reduce Motion` accessibility preference.

* [Code](./prefers-reduced-motion.html) (shown with FOUT approach)
* [Demo](https://www.zachleat.com/web-fonts/demos/prefers-reduced-motion.html)
* Related blog post: [Should I Use JavaScript to Load My Web Fonts?](https://www.filamentgroup.com/lab/js-web-fonts.html)

### `save-data` User Preference

Opt out of web fonts when user has enabled `Data Saver` mode.

* [Code](./save-data.html) (shown with FOUT approach)
* [Demo](https://www.zachleat.com/web-fonts/demos/save-data.html)
* Related blog post: [Should I Use JavaScript to Load My Web Fonts?](https://www.filamentgroup.com/lab/js-web-fonts.html)

## Experiments in Progress

You’ll probably see blog posts on these at some point.

* Metric compatible web fonts
  * Show how fonts can look without FOUT reflow if they are metric compatible.
* [FOUT metric matching with a Variable Font](./variablefont-fout-test.html)
  * Reduction in FOUT reflow (reduce text movement on web font render)
  * Related: [Font style matcher](https://meowni.ca/font-style-matcher/) from @notwaldorf

## Not Recommended but included for Posterity

### `font-display: optional`

* A little harsh to put this in the Not Recommended section but I like my web fonts on an empty-cache visit 😎
* [Code](./font-display-optional.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-display-optional.html)** _(4 web fonts)_

### System fonts

C’mon. 😇

* [Code](./dont.html)
* [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#abstain)
* [Demo](https://www.zachleat.com/web-fonts/demos/dont.html) _(0 web fonts)_

### Unceremonious Web Fonts

* [Code](./unceremonious-font-face.html)
* [Documentation](https://www.zachleat.com/web/comprehensive-webfonts/#font-face)
* [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-font-face.html)** _(4 web fonts)_

### Unceremonious Web Fonts, WOFF2 Only (Cutting the Mustard)

Old browsers [used to render FOIT without a timeout](https://www.zachleat.com/web/fout-foit-history/), which in practice made web fonts a single point of failure. Using WOFF2 only cuts the mustard to modern browsers that have a three second FOIT timeout for web fonts. We’re anti-invisible text here, but this approach is worth mentioning.

* [Code](./unceremonious-font-face-woff2-only.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-font-face-woff2-only.html)** _(4 web fonts)_

### Unceremonious Faux Web Fonts

`font-synthesis` is not a good end-product.

* [Code](./unceremonious-faux-font-face.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/unceremonious-faux-font-face.html)** _(1 web font)_: Bold and italic variants are rendered using [font-synthesis](https://www.zachleat.com/web/webfont-glossary/#font-synthesis)

## Anti-patterns and Deprecated Methods

### ⚠️ Inline Data URI

* [Code](./inline-data-uri.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#inline-data-uri)
* [Demo](https://www.zachleat.com/web-fonts/demos/inline-data-uri.html) _(4 web fonts)_

### ⚠️ Asynchronous Data URI

* [Code](./async-data-uri.html)
* [Read more](https://www.zachleat.com/web/comprehensive-webfonts/#async-data-uri)
* [Demo](https://www.zachleat.com/web-fonts/demos/async-data-uri.html) _(4 web fonts)_

### ⚠️ `<style>` Injection

Anything that uses JavaScript to inject a new `<style>` with `@font-face` blocks inside. Really bad repaint cost—avoid this. This is used in the Asynchronous Data URI method above but is also common in worse-performing methods too.

### ⚠️ `font-display: optional` and `preload`

* [Code](./font-display-optional-preload.html)
* [Read more: `preload` with `font-display: optional` is an Anti-pattern](https://www.zachleat.com/web/preload-font-display-optional/)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-display-optional-preload.html)** _(4 web fonts)_

### ⚠️ FOFT using only `font-display` (mixing `font-display` values across a `font-family`)

This method does not currently have cross-browser support. I’m hoping this will change—[learn more](https://twitter.com/zachleat/status/964173100001656832).

* [Code](./font-display-mix.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-display-mix.html)** _(4 web fonts—1 `swap` / 3 `optional`)_

## Failed Experiments

### 🚫 Asynchronous CSS

This is a common thing people try—they asynchronously load the CSS (and only the CSS). Heck, I used this behavior before I started studying web font loading.

* **Failed**: lazy loading the CSS only delays the start of the FOIT. It does not prevent it.
* [Read more at Lazy Loading Web Fonts is Probably Not What You Want](https://www.zachleat.com/web/lazy-loading-webfonts/)
* [Code](./asynchronous-css.html) (learn more about [asynchronous CSS](https://github.com/zachleat/async-css-loading))
* [Demo](https://www.zachleat.com/web-fonts/demos/asynchronous-css.html) _(4 web fonts)_

### 🚫 `@supports` and `font-display`

* Reasons for trying:
  * might be nice to only use web fonts if you can FOUT with `font-display`
  * might be nice to have FOUT with a class if `font-display` not supported (and work well without JS dependencies)
* **Failed**: `@supports` doesn’t work with font-face descriptors.
* [Code](failed-supports.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/failed-supports.html)

### 🚫 `font-family` Stack

* Put two or more `font-family` web fonts in a single `font-family` stack.
* **Failed**: The font matching algorithm selects the first web font that matches and attempts to load it (ignoring subsequent web font families). Even if you `preload` the subset first stage, it’ll swap over due to `font-family` order priority.
* [Code](font-family-stack.html)
* [Demo](https://www.zachleat.com/web-fonts/demos/font-family-stack.html)

* **Update**: While you can mitigate the above problem with `font-display`, perhaps modifying the order of the `font-family` stack and `@font-face` block ordering, there are still problems with removing the unnecessary subset web font from the page after the larger version has loaded. Font features that occur with glyphs that cross these font file boundaries will be broken (kerning, ligatures, et cetera). Relatedly, you cannot remove a CSS-paired `FontFace` object using the CSS Font Loading API (per the specification).

---

** Take note that these methods will FOUT in Internet Explorer and Edge by taking advantage of their default font loading behavior.
