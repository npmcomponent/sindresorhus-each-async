*This repository is a mirror of the [component](http://component.io) module [sindresorhus/each-async](http://github.com/sindresorhus/each-async). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/sindresorhus-each-async`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# each-async [![Build Status](https://travis-ci.org/sindresorhus/each-async.svg?branch=master)](https://travis-ci.org/sindresorhus/each-async)

> Async concurrent iterator (async forEach)

Like [async.each()](https://github.com/caolan/async#eacharr-iterator-callback), but tiny.

I often use `async.each()` for doing async operations when iterating, but I almost never use the other gadzillion methods in `async`.

Async iteration is one of the most used async control flow patterns.


## Install

Download [manually](https://github.com/sindresorhus/each-async/releases) or with a package-manager.

```bash
$ npm install --save each-async
```

```bash
$ bower install --save each-async
```

```bash
$ component install sindresorhus/each-async
```


## Usage

### Node.js

```js
eachAsync(['foo','bar','baz'], function (item, index, done) {
	console.log(item, index);
	done();
}, function (error) {
	console.log('finished');
});
//=> foo 0
//=> bar 1
//=> baz 2
//=> finished
```


## API

### eachAsync(array, callback, finishedCallback)

#### array

The array you want to iterate.

#### callback(item, index, done)

A function which is called for each item in the array with the following arguments:

- `item`: the current item in the array
- `index`: the current index
- `done([error])`: call this when you're done with an optional error. Supplying anything other than `undefined`/`null` will stop the iteration.

Note that order is not guaranteed since each item is handled concurrently.

#### finishedCallback(error)

A function which is called when the iteration is finished or on the first error. First argument is the error passed from `done()` in the `callback`.


## License

[MIT](http://opensource.org/licenses/MIT) © [Sindre Sorhus](http://sindresorhus.com)
