# trim-margin
[![Build Status](https://travis-ci.org/tee-talog/trim-margin.svg?branch=master)](https://travis-ci.org/tee-talog/trim-margin)

`trimMargin` like Kotlin and `stripMargin` like Scala.

[![NPM](https://nodei.co/npm/trim-margin.png)](https://nodei.co/npm/trim-margin/)

## Features
* Indent in a string literal.
* Selectable APIs: `trimMargin` or `stripMargin`.
* Use as tagged template literals.
* Inject to string type.

## install
```
$ npm i -S trim-margin
```

## Usage
```js
const {
    trimMargin,
    tm,
    inject,
} = require("trim-margin");

console.log(trimMargin(`
	|trim
    | indent
        | spaces`));
// => "\ntrim\n indent\n spaces"

console.log(trimMargin(`
    #other
    # delimiter`, "#"));
// => "\nother\n delimiter"

const template = `    | template`;
const literal  = `    | literal`;
console.log(tm`\
    |tagged
    ${template}
    |${literal}`);
// => "tagged\n template\n    | literal"

inject();
console.log(`\
    |inject
 to | string`.trimMargin());
// => "inject\n to | string"
```

## API

### trimMargin(str: string, [delimiter: string]): string

Trim indent spaces.

More detail "spaces":

> Matches a single character other than white space. Equivalent to `[^ \f\n\r\t\v\u00a0\u1680\u180e\u2000-\u200a\u2028\u2029\u202f\u205f\u3000\ufeff]`.

From: [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

Expect, `/\r?\n/`

#### str: string

Indented string.

#### delimiter: string

Indent delimiter.
This is used as an argument to a `RegExp` object.
defalut: `"\\|"`

### stripMargin(str: string, [delimiter :string]): string

Same `trimMargin`.

### tm

Use as Tagged template literals.
Same `trimMargin(literal)`.

### sm

Same `tm`.

### inject: void

Inject to `String`: `trimMargin` and `stripMargin`.
You can use it like method of string type.

### injectTrimMargin: void

Inject to `String`: `trimMargin`.
You can use it like method of string type.

### injectStripMargin: void

Inject to `String`: `stripMargin`.
You can use it like method of string type.

### injectAt(methodName: string): void

Inject to `String`.
You can use it like method of string type.

#### methodName: string

Method name injected into string type.

## License
MIT © tee-talog


