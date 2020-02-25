# Object

## Binary `in` Operator
The binary in operator, when applied to a string and an object, tells you whether that object has a property with that name.
```
let anObject = {left: 1, right: 2};
delete anObject.left;
console.log("left" in anObject);
// → false
console.log("right" in anObject);
// → true
```

## `Object.assign` Function
Object.assign function copies all properties from one object into another.
```
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```

[Back](../../../README.md)
