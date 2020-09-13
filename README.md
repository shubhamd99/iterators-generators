## iterators and Generators in Javascript

#### ES6 Iterators and Generators
* Arrays, Strings, Maps, Sets, NodeLists - built-in iterators
* {Object} => Iterator => Generator

* In JavaScript an iterator is an object which defines a sequence and potentially a return value upon its termination.

* Specifically, an iterator is any object which implements the Iterator protocol by having a next() method that returns an object with two properties
1. value: The next value in the iteration sequence.
2. done: This is true if the last value in the sequence has already been consumed. If value is present alongside done, it is the iterator's return value.

* A generator is a function that can stop midway and then continue from where it stopped. In short, a generator appears to be a function but it behaves like an iterator.

* Generator functions provide a powerful alternative: they allow you to define an iterative algorithm by writing a single function whose execution is not continuous. Generator functions are written using the `function*` syntax

* The yield keyword is used to pause and resume a generator function

* The well-known Symbol.iterator symbol specifies the default iterator for an object. Used by for...of. For making an object iteratable by making one of our own.


##### Example: 
```
function* fibonacci() {
  let current = 0;
  let next = 1;
  while (true) {
    let reset = yield current;
    [current, next] = [next, next + current];
    if (reset) {
        current = 0;
        next = 1;
    }
  }
}

const sequence = fibonacci();
console.log(sequence.next().value);     // 0
console.log(sequence.next().value);     // 1
console.log(sequence.next().value);     // 1
console.log(sequence.next().value);     // 2
console.log(sequence.next().value);     // 3
console.log(sequence.next().value);     // 5
console.log(sequence.next().value);     // 8
console.log(sequence.next(true).value); // 0
console.log(sequence.next().value);     // 1
console.log(sequence.next().value);     // 1
console.log(sequence.next().value);     // 2
```