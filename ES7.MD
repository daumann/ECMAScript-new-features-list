# ECMAScript 7 (ES2016) <sup>[credit](https://github.com/hemanth/es-next)</sup>

See the [ES7 standard](http://www.ecma-international.org/ecma-262/7.0/) for full specification of the ECMAScript 7 language.

ES7 includes the following new features:

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Exponentiation Operator](#exponentiation-operator)
- [Async functions](#async-functions)
- [Async generators](#async-generators)
- [Object.getOwnPropertyDescriptors](#objectgetownpropertydescriptors)
- [Object.values](#objectvalues)
- [Object.entries](#objectentries)
- [Array.prototype.includes](#arrayprototypeincludes)
- [Typed Objects](#typed-objects)
- [Trailing commas in function syntax.](#trailing-commas-in-function-syntax)
- [Class decorators.](#class-decorators)
- [Class properties](#class-properties)
- [Map.prototype.toJSON](#mapprototypetojson)
- [Set.prototype.toJSON](#setprototypetojson)
- [String.prototype.at](#stringprototypeat)
- [Object rest properties](#object-rest-properties)
- [Object spread properties](#object-spread-properties)
- [String.prototype.padLeft](#stringprototypepadleft)
- [String.prototype.padRight](#stringprototypepadright)
- [String.prototype.trimLeft](#stringprototypetrimleft)
- [String.prototype.trimRight](#stringprototypetrimright)
- [Regexp.escape](#regexpescape)
- [Bind Operator](#bind-operator)
- [Reflect.Realm](#reflectrealm)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# Exponentiation Operator
> Performs exponential calculation on operands. Same algorithm as `Math.pow(x, y)`

> Stage: Draft.

```js

let cubed = x => x ** 3;

cubed(2) // 8;
```

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

# Class properties
> Properties of class.

> Stage: Strawman.

```js
class Cat {
  name = 'Garfield';
  static says = 'meow';
}
new Cat().name; // Garfield
Cat.says; // meow
```

# Map.prototype.toJSON
> `toJSON` for Maps.

> Stage: Strawman.

```js
var myMap = new Map();
myMap.set(NaN, "not a number");

console.log(myMap.toJSON()); // {"NaN":"not a number"}
```

# Set.prototype.toJSON
> `toJSON` for Sets.

> Stage: Strawman.

```js
var mySet = new Set();
mySet.add(NaN);
mySet.add(1);
console.log(mySet.toJSON()) // {"1":1,"NaN":null}
```
# String.prototype.at
> String containing the code point at the given position

> Stage: Strawman.

```js
'abc\uD834\uDF06def'.at(1) // 'b'
'abc\uD834\uDF06def'.at(3) // '\uD834\uDF06'
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

# String.prototype.padLeft
> left justify and pad strings.

> Stage: Strawman.

```js
"hello".padLeft(4)            #=> "hello"
"hello".padLeft(20)           #=> "hello               "
"hello".padLeft(20, '1234')   #=> "hello123412341234123"
```

# String.prototype.padRight
> right justify and pad strings.

> Stage: Strawman.

```js
"hello".padRight(4)            #=> "hello"
"hello".padRight(20)           #=> "               hello"
"hello".padRight(20, '1234')   #=> "123412341234123hello"
```

# String.prototype.trimLeft
> left trims the string.

> Stage: Candidate.

```js
' \t \n LeftTrim   \t\n'.trimLeft(); // 'LeftTrim   \t\n';
```

# String.prototype.trimRight
> right trims the string.

> Stage: Candidate.

```js
' \t \n RightTrim   \t\n'.trimRight(); // ' \t \n RightTrim';
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
