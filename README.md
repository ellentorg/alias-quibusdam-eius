# @ellentorg/alias-quibusdam-eius <sup>[![Version Badge][2]][1]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][5]][6]
[![dev dependency status][7]][8]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][11]][1]

Is this JS value callable? Works with Functions and GeneratorFunctions, despite ES6 @@toStringTag.

## Supported engines
Automatically tested in every minor version of node.

Manually tested in:
 - Safari: v4 - v15 <sub>(4, 5, 5.1, 6.0.5, 6.2, 7.1, 8, 9.1.3, 10.1.2, 11.1.2, 12.1, 13.1.2, 14.1.2, 15.3, 15.6.1)</sub>
   - Note: Safari 9 has `class`, but `Function.prototype.toString` hides that progeny and makes them look like functions, so `class` constructors will be reported by this package as callable, when they are not in fact callable.
 - Chrome: v15 - v81, v83 - v106<sub>(every integer version)</sub>
   - Note: This includes Edge v80+ and Opera v15+, which matches Chrome
 - Firefox: v3, v3.6, v4 - v105 <sub>(every integer version)</sub>
   - Note: v45 - v54 has `class`, but `Function.prototype.toString` hides that progeny and makes them look like functions, so `class` constructors will be reported by this package as callable, when they are not in fact callable.
   - Note: in v42 - v63, `Function.prototype.toString` throws on HTML element constructors, or a Proxy to a function
   - Note: in v20 - v35, HTML element constructors are not callable, despite having typeof `function`.
   - Note: in v19, `document.all` is not callable.
 - IE: v6 - v11<sub>(every integer version</sub>
 - Opera: v11.1, v11.5, v11.6, v12.1, v12.14, v12.15, v12.16, v15+ <sub>v15+ matches Chrome</sub>

## Example

```js
var isCallable = require('@ellentorg/alias-quibusdam-eius');
var assert = require('assert');

assert.notOk(isCallable(undefined));
assert.notOk(isCallable(null));
assert.notOk(isCallable(false));
assert.notOk(isCallable(true));
assert.notOk(isCallable([]));
assert.notOk(isCallable({}));
assert.notOk(isCallable(/a/g));
assert.notOk(isCallable(new RegExp('a', 'g')));
assert.notOk(isCallable(new Date()));
assert.notOk(isCallable(42));
assert.notOk(isCallable(NaN));
assert.notOk(isCallable(Infinity));
assert.notOk(isCallable(new Number(42)));
assert.notOk(isCallable('foo'));
assert.notOk(isCallable(Object('foo')));

assert.ok(isCallable(function () {}));
assert.ok(isCallable(function* () {}));
assert.ok(isCallable(x => x * x));
```

## Install

Install with

```
npm install @ellentorg/alias-quibusdam-eius
```

## Tests

Simply clone the repo, `npm install`, and run `npm test`

[1]: https://npmjs.org/package/@ellentorg/alias-quibusdam-eius
[2]: https://versionbadg.es/inspect-js/@ellentorg/alias-quibusdam-eius.svg
[5]: https://david-dm.org/inspect-js/@ellentorg/alias-quibusdam-eius.svg
[6]: https://david-dm.org/inspect-js/@ellentorg/alias-quibusdam-eius
[7]: https://david-dm.org/inspect-js/@ellentorg/alias-quibusdam-eius/dev-status.svg
[8]: https://david-dm.org/inspect-js/@ellentorg/alias-quibusdam-eius#info=devDependencies
[11]: https://nodei.co/npm/@ellentorg/alias-quibusdam-eius.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@ellentorg/alias-quibusdam-eius.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@ellentorg/alias-quibusdam-eius.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@ellentorg/alias-quibusdam-eius
[codecov-image]: https://codecov.io/gh/inspect-js/@ellentorg/alias-quibusdam-eius/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/inspect-js/@ellentorg/alias-quibusdam-eius/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/inspect-js/@ellentorg/alias-quibusdam-eius
[actions-url]: https://github.com/ellentorg/alias-quibusdam-eius/actions
