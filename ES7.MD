# ECMAScript 7 (ES2016) <sup>[credit](https://www.ecma-international.org/ecma-262/7.0)</sup>

See the [ES7 standard](http://www.ecma-international.org/ecma-262/7.0/) for full specification of the ECMAScript 7 language.

ES7 includes the following new features:

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Exponentiation Operator](#exponentiation-operator)
- [Async functions](#async-functions)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


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
