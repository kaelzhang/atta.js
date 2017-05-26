[![Build Status](https://travis-ci.org/kaelzhang/atta.svg?branch=master)](https://travis-ci.org/kaelzhang/atta)
<!-- optional appveyor tst
[![Windows Build Status](https://ci.appveyor.com/api/projects/status/github/kaelzhang/atta?branch=master&svg=true)](https://ci.appveyor.com/project/kaelzhang/atta)
-->
<!-- optional npm version
[![NPM version](https://badge.fury.io/js/atta.svg)](http://badge.fury.io/js/atta)
-->
<!-- optional npm downloads
[![npm module downloads per month](http://img.shields.io/npm/dm/atta.svg)](https://www.npmjs.org/package/atta)
-->
<!-- optional dependency status
[![Dependency Status](https://david-dm.org/kaelzhang/atta.svg)](https://david-dm.org/kaelzhang/atta)
-->

# atta

The node imaging library which is heavily inspired by [PIL](http://www.pythonware.com/products/pil/).

## Install

```sh
$ npm install atta --save
```

## Usage

```js
const fsp = require('fs-promise')
// Creates a 100x100 stage
const atta = require('atta')
const playground = atta(100, 100)
const {
  Image,
  Curve
} = atta

const layer1 = playground.createLayer()
// `layer2` is upon `layer1`
const layer2 = playground.createLayer()

const img = new Image(await fsp.readFile(filename))
.rotate(.2)
.resize()
.crop([10, 10, 100, 100])

layer2.paste(img) // or img.pasteTo(layer2)

// Split RGB channel
const [r,,] = layer1.channel('rgb') // or 'lab'
r.applyCurve(new Curve(formula))

layer1.fillText('atta')

// Brings layer1 up
layer1.insertUpon(layer2)

// Example with Koa2
ctx.body = playground.createStream('jpg')
```

## new Image(imageBuffer)

- **imageBuffer** `Buffer`

## License

MIT
