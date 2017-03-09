# @avaly/flow-bin-linux

[![Build Status](https://travis-ci.org/avaly/flow-bin.svg?branch=master)](https://travis-ci.org/avaly/flow-bin)

> Linux binary wrapper for [Flow](http://flowtype.org) - A static type checker for JavaScript

NOTE: **Only Linux (64-bit) binaries** are currently with this package.

For other binaries, please use the official [`flow-bin`](https://github.com/flowtype/flow-bin).


## CLI

```
$ npm install --global @avaly/flow-bin-linux
```

```
$ flow --help
```


## API

```
$ npm install --save @avaly/flow-bin-linux
```

```js
const execFile = require('child_process').execFile;
const flow = require('@avaly/flow-bin-linux');

execFile(flow, ['check'], (err, stdout) => {
	console.log(stdout);
});
```


## License

flow-bin is BSD-licensed. We also provide an additional patent grant.


## Releases

### New Release

1. Update the "version" in `package.json` to reflect the flow version to publish. (For now, `flow-bin`'s version is also the version of the `flow` binary).
2. Run `make`.
  * There should be 2 uncommitted changes at this point: `SHASUM256.txt` and `package.json`.
3. Commit the changes with the message `Updated binary to v0.30.0`, with the correct version.
4. Push/merge to `master`.
5. Tag the update:

  ```sh
  git checkout master &&
  git pull &&
  make test &&
  git tag v$(node -p 'require("./package.json").version') &&
  git push v$(node -p 'require("./package.json").version')
  ```

6. Publish to npm.

### Inspect a Release Before Publishing

```sh
npm pack
tar xf "flow-bin-$(node -p 'require("./package.json").version').tgz"
cd package
npm run verify
```
