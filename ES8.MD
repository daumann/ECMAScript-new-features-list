# ECMAScript 8 (ES2017)

See the [ES8 standard](http://www.ecma-international.org/ecma-262/8.0/) for full specification of the ECMAScript 8 language.

ES8 includes the following new features:

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Async functions](#async-function)
- [Object.entries](#objectentries)
- [Object.values](#objectvalues)
- [Object.getOwnPropertyDescriptors](#objectgetownpropertydescriptors)
- [Trailing commas in function syntax.](#trailing-commas-in-function-syntax)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

---


### `async function`

The asynchronous function returns an `AsyncFunction` object and operates asynchronously via the event loop. The syntax is 
very similar to synchronous functions

#### Syntax:

* async function name([param[, param[, ... param]]]) { statements }
* **@name**: the function name
* **@param**: param of the function
* **statements**: body of the function
* **returns**: Promise

```javascript
const resolveAfter3Seconds = function() {
  console.log('starting 3 second promsise')
  return new Promise(resolve => {
    setTimeout(function() {
      resolve(3)
      console.log('done in 3 seconds')  
    }, 3000)  
  })  
}

const resolveAfter1Second = function() {
  console.log('starting 1 second promise')
  return new Promise(resolve => {
      setTimeout(function() {
        resolve(1) 
        console.log('done, in 1 second') 
      }, 1000)
  })  
}

const sequentialStart = async function() {
  console.log('***SEQUENTIAL START***')
  const one = await resolveAfter1Second()
  const three = await resolveAfter3Seconds()

  console.log(one)
  console.log(three)
}

sequentialStart() // invoke async function
```

### `Object.entries()`

`Object.entries` gives us the ability to get an object's enurmerable property pairs by returning an array of any given
object's own eumberable properties. /ie: [key, value] pairs. Note that the order is the same as provided by the `for...in` loop.

#### Syntax:

* `Object.entries(obj)`
* **@params**: `obj`
* **returns**: Array

#### Examples:

> basic example

```javascript
const obj = { self: 'that', norf: 'quux' }
console.log(Object.entries(obj))

// => [ ['self', 'that'], ['norf', 'quux'] ]
```

> array like object with random key ordering
```javascript
const obj = { 50: 'a', 1: 'b', 5: 'c' }
console.log(Object.entries(obj)) 

// => [ ['1', 'b'], ['5', 'c'], ['50', 'a'] ]
```

### `Object.values()`

`Object.values` lets us return an array of a given object's own enumerable property values. Note that the order is the
same as provided by the `for...in` loop.

#### Syntax:

* `Object.values(obj)`
* **@params**: `obj`
* **returns**: Array

#### Examples:

> basic example

```javascript
const obj = { a: 100, b: 200 }
console.log(Object.values(obj))

// => [100, 200]
```

> mixed
```javascript
const obj = { foo: 'foo', bar: [100, 200], baz: 55 }
console.log(Object.values(obj)) 

// => ['foo', [100, 200], 55 ]
```

> string
```javascript
const myStr = 'Lufthansa'
console.log(Object.values(myStr))

// => ["L", "u", "f", "t", "h", "a", "n", "s", "a"]
```

### `String.prototype.padStart()`
This method, `padStart()` pads the current string (applied from the left) with another string till the
resulting string reaches the given optional length. 


#### Syntax:

* `str.padStart(targetLength [, padString])`
* **@targetLength**: the length of resulting string once padding occurs
* **@padString(Optional)**: the string to pad the current string with
* **returns**: String

#### Examples:

> basic examples

```javascript
'xyz'.padStart(5)                 // "  xyz"
'xyz'.padStart(10)                // "       xyz"
'xyz'.padStart(6, 'hij')          // "hijxyz"
'xyz'.padStart(8, '1')            // "11111xyz"

const myStr = 'xyz'.padStart(22)  // "                   xyz"
myStr.length                      // 22
```

### `String.prototype.padEnd()`
This method, `padEnd()` pads the current string (applied from the right) with another string till the
resulting string reaches the given optional length. 


#### Syntax:

* `str.padEnd(targetLength [, padString])`
* **@targetLength**: the length of resulting string once padding occurs
* **@padString(Optional)**: the string to pad the current string with
* **returns**: String

#### Examples:

> basic examples

```javascript
'abc'.padEnd(10)           // "abc       "
'abc'.padEnd(10, "foo")    // "abcfoofoof"
'abc'.padEnd(6, "123456")  // "abc123"
'abc'.padEnd(1)            // "abc"
```

### `Exponentiation`
A shorthand method to exponetiation has been introduced in JavaScript:

#### Syntax:

* `operand` ** `operand`

> basic examples
```javascript
Math.pow(5, 2)

// ...is now
5 ** 2
```

### `Object.getOwnPropertyDescriptors()`
`Object.getOwnPropertyDescriptors()` returns all own property descriptors of a given object. A property descriptor
is a record with one of the following attributes:

* value
* writable
* get
* set
* configurable
* enumerable

```javascript
let myObj = {
  property1: 'foo',
  property2: 'bar',
  property3: 42,
  property4: () => console.log('prop4')  
}

Object.getOwnPropertyDescriptors(myObj)

/*
{ property1: {…}, property2: {…}, property3: {…}, property4: {…} }
  property1: {value: "foo", writable: true, enumerable: true, configurable: true}
  property2: {value: "bar", writable: true, enumerable: true, configurable: true}
  property3: {value: 42, writable: true, enumerable: true, configurable: true}
  property4: {value: ƒ, writable: true, enumerable: true, configurable: true}
  __proto__: Object
*/
```


### `Trailing Commas`
Trailing commas are now allowed in JavaScript - they are now ignored

> trailing commas in array

```javascript
let arr = [
  10,
  20,
  30,
  40,
  50,  
]

arr // [10, 20, 30, 40,  50]
arr.length // 5 
```

> trailing commas in object
```javascript
const obj = {
  trailing: 'comma',
  is: 'allowed',
  in: 'JavaScript..', 
}
```
