# ES9 (ES2018)

See the [ES9 standard](http://www.ecma-international.org/ecma-262/9.0/) for full specification of the ECMAScript 9 language.

ES11 includes the following new feature proposals:

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Async functions](#async-functions)
- [Object rest properties](#object-rest-properties)
- [Object spread properties](#object-spread-properties)
- [Regexp.escape](#regexpescape)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Async functions
> Deferred Functions


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

# Object rest properties
> Rest properties for object destructuring assignment.

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


```js
RegExp.escape("(*.*)"); // "\(\*\.\*\)"
RegExp.escape("｡^･ｪ･^｡") // "｡\^･ｪ･\^｡"
RegExp.escape("😊 *_* +_+ ... 👍"); // "😊 \*_\* \+_\+ \.\.\. 👍"
```
