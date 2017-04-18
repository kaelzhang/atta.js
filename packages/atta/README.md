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

<!-- description -->

## Install

```sh
$ npm install atta --save
```

## Usage

```js
const fsp = require('fs-promise')
const atta = require('atta')
const {
  Image,
  Curve
} = atta

const layer1 = atta().createLayer()
// `layer2` is upon `layer1`
const layer2 = atta().createLayer()

const img = new Image(await fsp.readFile(filename))
.rotate(.2)
.crop([10, 10, 100, 100])

layer2.paste(img) // or img.pasteTo(layer2)

const [r,,] = layer1.channel('rgb') // or 'lab'
r.applyCurve(new Curve(formula))

layer1.fillText('atta')

// Brings layer1 up
layer1.insertUpon(layer2)

// Example with Koa2
ctx.body = atta().createStream('jpg')
```

## License

MIT
