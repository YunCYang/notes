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

Calling resolve from Promise class directly.


## Async and Await

An optional choice for asynchronous function.
