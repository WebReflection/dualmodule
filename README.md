# Node.js Dual Modules

The minimal amount of effort needed to publish modules, for both ESM and CJS, without ever needing to write an `.mjs` file.


## How

Simply have `./cjs/` and `./esm/` folders, in your module, with an `index.js` that represents it.

Add these fields in your `package.json`, and that's it:

```
{
  "type": "module",
  "main": "esm/index.js",
}

```

Everyone can now `require('module/cjs')` or `import * from 'module'`, as legacy CJS resolution would ignore the `package.json`, and any modern bundlers, or even node.js, would work with native ESM modules 🎉


## Example

Following an example for both ESM and CJS, if you `npm i dualmodule` first in any folder:

#### ESM

```sh
node --experimental-modules --input-type=module -e \
  'import $ from "dualmodule"; console.log($)'
```

That will log the string _ESM_, while the following one ...

#### CJS

```sh
node -e 'const $ = require("dualmodule/cjs"); console.log($);'
```

It will log the string _CJS_.