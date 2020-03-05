# Node.js Dual Modules

The minimal amount of effort needed to publish modules, for both ESM and CJS, without ever needing to write an `.mjs`, or `.cjs` file.

## Test It !

You need node 13.10 or higher, and a test folder, such as `~/test/node-modules` to perform this test:

```sh
mkdir -p ~/test/node-modules
cd ~/test/node-modules
npm i dualmodule
# test CommonJS
node -e 'console.log(require("dualmodule"))'; # read "CJS"
# test ESM
node --input-type=module -e 'import $ from "dualmodule"; console.log($)';
```

If you are in node < 13.10 you'll see an _ExperimentalWarning_, but the output is `ESM`.

If you are in node >= 13.10 you won't see the warning, just the `ESM` output.

If you'd like to test through any `file.js` in that folder, and you want to test the _ESM_ version of the module:

```sh
echo '{"type":"module"}' > ~/test/node-modules/package.json
echo 'import $ from "dualmodule"; console.log($)' > test.js
node test.js # read "ESM"
```

And you are good to go 🎉
