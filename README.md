# zx-css

Commonly used css styles

<p align="left">
  <a href="https://npmcharts.com/compare/zx-css?minimal=true"><img src="https://img.shields.io/npm/dm/zx-css.svg?sanitize=true" alt="Downloads"></a>
  <a href="https://www.npmjs.com/package/zx-css"><img src="https://img.shields.io/npm/v/zx-css.svg?sanitize=true" alt="Version"></a>
  <a href="https://www.npmjs.com/package/zx-css"><img src="https://img.shields.io/npm/l/zx-css.svg?sanitize=true" alt="License"></a>
</p>

```shell script
npm i zx-css
# or
yarn add zx-css
```

## Usage

### scss

scss/vars/index.scss

```scss
@import "/node_modules/zx-css/src/vars";
// Override the _calc method (重写_calc方法)
@function _calc($val) {
  @return calc(1rem / 16 * #{$val});
}
```

scss/common/index.scss

```scss
@import "/node_modules/zx-css/src/reset";
@import "/node_modules/zx-css/src/common";
// ...
```

### js / ts

```js
// css
import 'zx-css'
// scss
import 'zx-css/src/index.scss'
// Import only common scss
import 'zx-css/src/common/index.scss'
```

## Register global variables

### vite

vite.config.js

```js
import { defineConfig } from 'vite'

export default defineConfig({
  // ...,
  css:{
    preprocessorOptions: {
      // Register global variables
      scss: {
        // additionalData: `@import "zx-css/src/vars/index.scss";`
        additionalData: `@import "scss/vars/index.scss";`
      }
    }
  }
})
```

### webpack

webpack.config.js

```js
module.exports = {
  // ...,
  module: {
    rules: [
      {
        test: /\.s(c|a)ss$/,
        use: [
          'style-loader',
          'css-loader',
          'sass-loader',
          {
            loader: 'style-resources-loader',
            options: {
              // patterns: ['zx-css/src/vars/index.scss'],
              patterns: ['scss/vars/index.scss'],
            },
          }
        ],
      },
    ],
  },
}
```

## scss @mixin

### clamp($line)

The clamp CSS property allows limiting of the contents of a block container to the specified number of lines.

```scss
// https://developer.mozilla.org/en-US/docs/Web/CSS/-webkit-line-clamp
.line-clamp {
  @include clamp(3);
}
```

### border($position, $color, $size)

```scss
.border-top {
  // border-top: 2px solid #ccc;
  @include border(top, #ccc, 2);
}
```

## scss @function

### _calc($input)

```scss
width: _calc(100);

// use rem, calc(1rem / 16 * #{$val});
// width: calc(1rem / 16 * 100);

// use vw, calc(100vw / 750 * #{$val});
// width: calc(100vw / 750 * 100);
```

## Common CSS

### m/p[n] (margin and padding)

`.m-40`, `.m-35`, `.m-30`, `.m-25`, `.m-20`, `.m-19`, `.m-18`, `.m-17`, `....`, `.m0`, `.m1`, `.m2`, `.m3`, `.m4`, `....`, `.m19`, `.m20`, `.m25`, `.m30`, `.m35`, `.m40`, `.m45`, `.m50`

`.p-40`, `.p-35`, `.p-30`, `.p-25`, `.p-20`, `.p-19`, `.p-18`, `.p-17`, `....`, `.p0`, `.p1`, `.p2`, `.p3`, `.p4`, `....`, `.p19`, `.p20`, `.p25`, `.p30`, `.m35`, `.p40`, `.p45`, `.p50`

> m margin, p padding

> mt margin-top, mr margin-right, mb margin-bottom, ml margin-left

> pt padding-top, pr padding-right, pb padding-bottom, pl padding-left

> mh/ph: margin/padding horizontal(ml and mr), mv/pv: margin/padding vertical(mt and mb)

```html
<div class="m20 pv20">
  margin: 20px; padding-top: 20px; padding-bottom: 20px;
</div>

<div class="mt-20">
  margin-top: -20px;
</div>
```

### fs[n] (font-size)

`.fs10`, `.fs12`, `.fs14`, `.fs16`, `....`, `.fs38`, `.fs40`

```html
<div class="fs20">
  font-size: 20px;
</div>
```

### ell

```html
<div class="ell" style="width: 200px">
  The text-overflow CSS property sets how hidden overflow content is signaled to users. It can be clipped, display an ellipsis ('…'), or display a custom string.
</div>
```

### break

```html
<div class="break" style="width: 200px">
  breakwordbreakwordbreakwordbreakwordbreakwordbreakwordbreakwordbreakwordbreakwordbreakword.
</div>
```

### wrap

```html
<div class="wrap">
  white-space: initial !important;
</div>
```

### nowrap

```html
<div class="nowrap">
  white-space: nowrap !important;
</div>
```

### bold

```html
<div class="bold">
  font-weight: bolder !important;
</div>
```

### justify

```html
<div class="justify">
  text-align: justify;
</div>
```

### pointer

```html
<div class="pointer">
  cursor: pointer;
</div>
```

### block

```html
<div class="block">
  display: block !important;
</div>
```

### center

```html
<div class="center">
  text-align: center;
</div>
```

flex center

```html
<div class="flex center">
  display: flex;
  align-items: center;
  justify-content: center;
</div>
```

### left

```html
<div class="left">
  text-align: left;
</div>
```

### right

```html
<div class="right">
  text-align: right;
</div>
```

flex right

```html
<div class="flex right">
  display: flex;
  align-items: center;
  justify-content: flex-end;
</div>
```

### flex

```html
<div class="flex">
  display: flex;
  align-items: center;
</div>
```

### inline

```html
<div class="inline">
  display: inline;
</div>
```

flex inline

```html
<div class="flex inline">
  display: inline-flex;
  align-items: center;
</div>
```

### flex-column

```html
<div class="flex-column">
  display: flex;
  flex-direction: column;
</div>
```
### space-between

```html
<div class="space-between">
  display: flex;
  align-items: center;
  justify-content: space-between;
</div>
```

### flex-wrap

```html
<div class="flex-wrap">
  display: flex;
  flex-wrap: wrap;
</div>
```

## Other

https://github.com/sass/dart-sass

https://wikimass.com/sass/compressed
