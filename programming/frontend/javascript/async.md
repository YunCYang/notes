# Async

## Promise

Promise is an object with three states (pending, fullfill, reject).
Use methods `then` and `catch` (and also `finally`).

```
const p = new Promise ((resove, reject) => {});
p.then(value => newValue)
 .then(newValue => anotherValue);
```

Promise always returns another promise object.
In a `then` method chain, previously returned value goes to the next `then` method.


```
const p = Promise.resolve(value);
```

Calling resolve from Promise class directly. Creates a new Promise with value inside.


```
p.then(value => {
  const p1 = Promise.resolve('promiseValue');
  return p1;
})
 .then(newValue => someAction());
```
Even though the first `then` returns a promise itself (`p1`), because `resolve` returns a promise value, the second `then` will receive the value (`promiseValue`) instead of the promise (`p1`) itself.

The is the same case for `response.json()` in a promise chain when dealing with APIs.



## Async and Await

An optional choice for asynchronous function.

## Generator

Define a generator using the the keyword `function*` instead of the normal `function`. When a generator is called, it will only run until it hits a *yield* expression, which pauses it and causes the yielded value to become the next value produced by the iterator.

```
function* powers(n) {
  for (let current = n;; current *= n) {
    yield current;
  }
}

for (let power of powers(3)) {
  if (power > 50) break;
  console.log(power);
}
// → 3
// → 9
// → 27
```

Can be useful when you need to generate something like an infinite array of index.


[Back](../../../README.md)
