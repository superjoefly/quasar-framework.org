title: DOM Utils
---

### Helping Tree-Shake
You will notice all examples import different parts of Quasar. However, if you need only one specific util method, then you can use ES6 destructuring to help Tree Shaking embed only that method and not all around it.

Example with `dom` utils:
```js
import { dom } from 'quasar'
const { offset } = dom

// Offset on screen
console.log(offset(DomElement))
// { top: 10, left: 100 }
```

You can also import all of dom utils and use whatever you need like this (but note that your bundle will contain unused methods too):
```js
import { dom } from 'quasar'

// Offset on screen
console.log(dom.offset(DomElement))
// { top: 10, left: 100 }
```

## Offset on screen viewport
``` js
import { dom } from 'quasar'
const { offset } = dom

// Offset on screen
console.log(offset(DomElement))
// { top: 10, left: 100 }
```

## Get Computed Style
This applies only when DomElement is visible! It returns the **computed** browser style, so the property you are asking for doesn't necessary has to be applied within a `style` attribute.

``` js
import { dom } from 'quasar'
const { style } = dom

// Get COMPUTED style (when DomElement is visible!)
// Computed means a DomElement might not have "height" CSS property set,
// but that does not mean it doesn't have a height when it's displayed.
// The following method accesses the computed CSS provided by the browser:
console.log(style(DomElement, 'height'))
// '10px' <<< notice it returns a String ending in 'px'
```

## Get Height / Width
``` js
import { dom } from 'quasar'
const { height, width } = dom


// Some aliases of the previous method for "width" and "height" which
// returns Numbers instead of Strings:
console.log(
  height(DomElement),
  width(DomElement)
)
// 10 100
```

## Apply CSS Properties in Batch
```js
import { dom } from 'quasar'
const { css } = dom

// Apply a list of CSS properties to a DomNode
css(DomElement, {
  height: '10px',
  display: 'flex'
})
```

## Get Viewport Dimensions
```js
import { dom } from 'quasar'
const { viewport } = dom

// Get Window height and width
let {height, width} = viewport()
console.log(height, width)
// 800 600
```

## Execute when DOM is ready
```js
import { dom } from 'quasar'
const { ready } = dom

// Execute a Function when DOM is ready:
ready(function () {
  // ....
})
```

## Get Crossbrowser CSS Transform Property
``` js
import { dom } from 'quasar'
const { cssTransform } = dom

let props = cssTransform('rotateX(30deg)')
// props = {
//   transform: 'rotateX(30deg)',
//   '-webkit-transform': 'rotateX(30deg)',
//   '-ms-transform': 'rotateX(30deg)',
//   '-o-transform': 'rotateX(30deg)',
//   '-moz-transform': 'rotateX(30deg)'
// }

// Then you can apply it with css(el, props)
```
