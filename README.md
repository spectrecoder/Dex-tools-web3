<p align="center">
  <img src="assets/logo/web3js.jpg" width="200" alt="web3.js" />
</p>

# web3.js - Ethereum JavaScript API

[![Gitter][gitter-image]][gitter-url] [![StackExchange][stackexchange-image]][stackexchange-url] [![NPM Package Version][npm-image-version]][npm-url] [![NPM Package Downloads][npm-image-downloads]][npm-url] [![Build Status][actions-image]][actions-url] [![Dev Dependency Status][deps-dev-image]][deps-dev-url] [![Coverage Status][coveralls-image]][coveralls-url] [![Lerna][lerna-image]][lerna-url] [![Netlify Status][netlify-image]][netlify-url]

This is the Ethereum [JavaScript API][docs]
which connects to the [Generic JSON-RPC](https://github.com/ethereum/wiki/wiki/JSON-RPC) spec.

You need to run a local or remote [Ethereum](https://www.ethereum.org/) node to use this library.

Please read the [documentation][docs] for more.

## Installation

### Node

```bash
npm install web3
```

### Yarn

```bash
yarn add web3
```

### In the Browser

Use the prebuilt `dist/web3.min.js`, or
build using the [web3.js][repo] repository:

```bash
npm run build
```

Then include `dist/web3.min.js` in your html file.
This will expose `Web3` on the window object.

Or via jsDelivr CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>
```

UNPKG:

```html
<script src="https://unpkg.com/web3@latest/dist/web3.min.js"></script>
```

## Usage

```js
// In Node.js
const Web3 = require('web3');

let web3 = new Web3('ws://localhost:8546');
console.log(web3);
> {
    eth: ... ,
    shh: ... ,
    utils: ...,
    ...
}
```

Additionally you can set a provider using `web3.setProvider()` (e.g. WebsocketProvider):

```js
web3.setProvider('ws://localhost:8546');
// or
web3.setProvider(new Web3.providers.WebsocketProvider('ws://localhost:8546'));
```

There you go, now you can use it:

```js
web3.eth.getAccounts().then(console.log);
```

### Usage with TypeScript

We support types within the repo itself. Please open an issue here if you find any wrong types.

You can use `web3.js` as follows:

```typescript
import Web3 from 'web3';
const web3 = new Web3('ws://localhost:8546');
```

If you are using the types in a `commonjs` module, like in a Node app, you just have to enable `esModuleInterop` and `allowSyntheticDefaultImports` in your `tsconfig` for typesystem compatibility:

```js
"compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    ....
```

## Trouble shooting and known issues.

### Web3 and Angular
If you are using Ionic/Angular at a version >5 you may run into a build error in which modules `crypto` and `stream` are `undefined`

a work around for this is to go into your node-modules and at `/angular-cli-files/models/webpack-configs/browser.js` change  the `node: false` to `node: {crypto: true, stream: true}` as mentioned [here](https://github.com/ethereum/web3.js/issues/2260#issuecomment-458519127)

Another variation of this problem was an issue opned on angular-cli: https://github.com/angular/angular-cli/issues/1548

## Documentation

Documentation can be found at [ReadTheDocs][docs].

## Building

### Requirements

-   [Node.js](https://nodejs.org)
-   [npm](https://www.npmjs.com/)

```bash
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
```

### Building (webpack)

Build the web3.js package:

```bash
npm run build
```

### Testing (mocha)

```bash
npm test
```

### Contributing

Please follow the [Contribution Guidelines](./CONTRIBUTIONS.md) and [Review Guidelines](./REVIEW.md).

This project adheres to the [Release Guidelines](./REVIEW.md).

### Community

-   [Gitter][gitter-url]
-   [StackExchange][stackexchange-url]

### Similar libraries in other languages

-   Haskell: [hs-web3](https://github.com/airalab/hs-web3)
-   Java: [web3j](https://github.com/web3j/web3j)
-   PHP: [web3.php](https://github.com/sc0Vu/web3.php)
-   Purescript: [purescript-web3](https://github.com/f-o-a-m/purescript-web3)
-   Python: [Web3.py](https://github.com/ethereum/web3.py)
-   Ruby: [ethereum.rb](https://github.com/EthWorks/ethereum.rb)
-   Scala: [web3j-scala](https://github.com/mslinn/web3j-scala)

[repo]: https://github.com/ethereum/web3.js
[docs]: http://web3js.readthedocs.io/
[npm-image-version]: https://img.shields.io/npm/v/web3.svg
[npm-image-downloads]: https://img.shields.io/npm/dm/web3.svg
[npm-url]: https://npmjs.org/package/web3
[actions-image]: https://github.com/ethereum/web3.js/workflows/Build/badge.svg
[actions-url]: https://github.com/ethereum/web3.js/actions
[deps-dev-image]: https://david-dm.org/ethereum/web3.js/1.x/dev-status.svg
[deps-dev-url]: https://david-dm.org/ethereum/web3.js/1.x?type=dev
[dep-dev-image]: https://david-dm.org/ethereum/web3.js/dev-status.svg
[dep-dev-url]: https://david-dm.org/ethereum/web3.js#info=devDependencies
[coveralls-image]: https://coveralls.io/repos/ethereum/web3.js/badge.svg?branch=1.x
[coveralls-url]: https://coveralls.io/r/ethereum/web3.js?branch=1.x
[waffle-image]: https://badge.waffle.io/ethereum/web3.js.svg?label=ready&title=Ready
[waffle-url]: https://waffle.io/ethereum/web3.js
[gitter-image]: https://badges.gitter.im/Join%20Chat.svg
[gitter-url]:  https://gitter.im/ethereum/web3.js
[lerna-image]: https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg
[lerna-url]: https://lerna.js.org/
[netlify-image]: https://api.netlify.com/api/v1/badges/1fc64933-d170-4939-8bdb-508ecd205519/deploy-status
[netlify-url]: https://app.netlify.com/sites/web3-staging/deploys
[stackexchange-image]: https://img.shields.io/badge/web3js-stackexchange-brightgreen
[stackexchange-url]: https://ethereum.stackexchange.com/questions/tagged/web3js

## Semantic versioning

This project follows [semver](https://semver.org/) as closely as possible **from version 1.3.0 onwards**. Earlier minor version bumps [might](https://github.com/ethereum/web3.js/issues/3758) have included breaking behavior changes.
