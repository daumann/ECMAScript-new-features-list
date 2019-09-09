# ES NEXT (ES2019) <sup>[credit](https://github.com/hemanth/es-next)</sup>

See the [ES11 standard](http://www.ecma-international.org/ecma-262/7.0/) for full specification of the ECMAScript 7 language.

ES11 includes the following new feature proposals:

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Async functions](#async-functions)
- [Object rest properties](#object-rest-properties)
- [Object spread properties](#object-spread-properties)
- [Regexp.escape](#regexpescape)
- [Bind Operator](#bind-operator)
- [Reflect.Realm](#reflectrealm)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Async functions
> Deferred Functions

> Stage: Proposal.

```js
function wait(t){
  return new Promise((r) => setTimeout(r, t));
}

async function asyncMania(){
  console.log("1");
  await wait(1000);
  console.log("2");
}

asyncMania()
.then(() => console.log("3"));

// logs: 1 2 3
```

# Async generators
> Deferred generators.

> Stage: Proposal.

```js
// provider
async function* nums() {
  yield 1;
  yield 2;
  yield 3;
}

// consumer
async function printData() {
  for(var x on nums()) {
    console.log(x);
  }
}
```

# Object.getOwnPropertyDescriptors
> Returns a property descriptor for an own property.

> Stage: Strawman.

```js
// Creating a shallow copy.
var shallowCopy = Object.create(
  Object.getPrototypeOf(originalObject),
  Object.getOwnPropertyDescriptors(originalObject)
);
```

# Object.values
> Get all the values of the object as an array.

> Stage: Shall reach Strawman

```js
var person = { fname: "Hemanth", lname: "HM", location: "Earth", type: "Human" };

Object.values(person);

//^ ["Hemanth","HM","Earth","Human"]
```

# Object.entries
> Returns a Array of arrays of key,value pairs.

> Stage: Shall reach Strawman

```js
var person = { fname: "Hemanth", lname: "HM", location: "Earth", type: "Human" };

Object.entries(person);

//^ [["fname","Hemanth"],["lname","HM"],["location","Earth"],["type","Human"]]

```

# Array.prototype.includes
> Determines whether an array includes a certain element or not.

> Stage: Draft.

```js
[1, 2, 3].includes(3, 0, 7); // true
[1, 2, NaN].includes(NaN); // true
[0,+1,-1].includes(42); // false
```

# Typed Objects
> Portable, memory-safe, efficient, and structured access to contiguously allocated data.

> Stage: Proposal.

```js
var Point = new StructType({
  x: int32,
  y: int32
});

var point = new Point({
  x: 42,
  y: 420
});
```

# Trailing commas in function syntax.
> Trailing commas in parameter and argument lists.

> Stage: Proposal

```js
var meow = function (cat1, cat2,) {}

Math.max(4,2,0,);
```

# Class decorators.
> Annotate and modify classes and properties at design time.

> Stage: Proposal.

```js
class Person {
  @cantEnum
  get kidCount() { return this.children.length; }
}

function cantEnum(target, name, descriptor) {
  descriptor.enumerable = false;
  return descriptor;
}
```

# Object rest properties
> Rest properties for object destructuring assignment.

> Stage: Strawman.

```js
let { fname, lname, ...rest } = { fname: "Hemanth", lname: "HM", location: "Earth", type: "Human" };
fname; //"Hemanth"
lname; //"HM"
rest; // {location: "Earth", type: "Human"}
```

# Object spread properties
> Spread properties for object destructuring assignment.

> Stage: Strawman.

```js
let info = {fname, lname, ...rest};

info; // { fname: "Hemanth", lname: "HM", location: "Earth", type: "Human" }

```

# Regexp.escape
> Escapes any characters that would have special meaning in a regular expression.

> Stage: Strawaman

```js
RegExp.escape("(*.*)"); // "\(\*\.\*\)"
RegExp.escape("｡^･ｪ･^｡") // "｡\^･ｪ･\^｡"
RegExp.escape("😊 *_* +_+ ... 👍"); // "😊 \*_\* \+_\+ \.\.\. 👍"
```

# Bind Operator
> `::` Function binding and method extraction

> Stage: Shall reach Strawman.

```js
let log = (level, msg) => ::console[level](msg);

import { map, takeWhile, forEach } from "iterlib";

getPlayers()
  ::map(x => x.character())
  ::takeWhile(x => x.strength > 100)
  ::forEach(x => console.log(x));
```
