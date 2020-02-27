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
`Object.assign` function copies all properties from one object into another.
```
let objectA = {a: 1, b: 2};
Object.assign(objectA, {b: 3, c: 4});
console.log(objectA);
// → {a: 1, b: 3, c: 4}
```

## `Object.getPrototypeOf`
`Object.getPrototypeOf` function returns the prototype of an object.

## `Object.create`
`Object.create` creates an object with a specific prototype.
```
let protoRabbit = {
  speak(line) {
    console.log(`The ${this.type} rabbit says '${line}'`);
  }
};
let killerRabbit = Object.create(protoRabbit);
killerRabbit.type = "killer";
killerRabbit.speak("SKREEEE!");
// → The killer rabbit says 'SKREEEE!'
```

## `Constructor` and `new` (pre 2015)
A class defines what method and properties a type of object has, such is called an instance of the class.

To create an instance of a given class, you have to make an object that derives from the proper prototype, but you also have to make sure it has the properties that instance of this class are supposed to have. This is what a constructor function does.

If you put the keyword `new` in front of a function call, the function is treated as a constructor. This means that an object with the right prototype is automatically created, bound to `this` in the function, and returned at the end of the function.

The prototype object used when constructing objects is found by taking the `prototype` property of the constructor function.

```
function Rabbit(type) {
  this.type = type;
}
Rabbit.prototype.speak = function(line) {
  console.log(`The ${this.type} rabbit says '${line}'`);
};

let weirdRabbit = new Rabbit("weird");
```

## Map

A map is a data structure that associates values (keys) with other values. JavaScript comes with a class called `Map` that stores a mapping and allows any type of keys.

```
let ages = new Map();
ages.set("Boris", 39);
ages.set("Liang", 22);
ages.set("Júlia", 62);

console.log(`Júlia is ${ages.get("Júlia")}`);
// → Júlia is 62
console.log("Is Jack's age known?", ages.has("Jack"));
// → Is Jack's age known? false
console.log(ages.has("toString"));
// → false
```

The methods `set`, `get`, and `has` are part of the interface of the Map object.

## Symbol

Symbol is a primary variable. Newly created symbols are unique, meaning you cannot create the same symbol twice.

Property name can be either strings or symbols. Symbol is often used as a property name to avoid collision - accidentally overwrites another property using the same string as their key.

The string inside the parenthesis is optional.

```
let sym = Symbol("name");
console.log(sym == Symbol("name"));
// → false
Rabbit.prototype[sym] = 55;
console.log(blackRabbit[sym]);
// → 55
```

## Symbol iterator

Use `Symbol.iterator` when iterating an object using ex. for/of loop is desired. It works like a generator.

Using a generator as opposed to using a while loop, the advantage is while loop will block out every other operation before the loop is finished. Generator only runs when `next()` is called.

## Getter and Setter

Use a getter to read from a property and setter to write data to a property.

The below class only stores temperature in Celsius, but can convert to and from Celsius in the Farenheit getter and setter.

```
class Temperature {
  constructor(celsius) {
    this.celsius = celsius;
  }
  get fahrenheit() {
    return this.celsius * 1.8 + 32;
  }
  set fahrenheit(value) {
    this.celsius = (value - 32) / 1.8;
  }

  static fromFahrenheit(value) {
    return new Temperature((value - 32) / 1.8);
  }
}

let temp = new Temperature(22);
console.log(temp.fahrenheit);
// → 71.6
temp.fahrenheit = 86;
console.log(temp.celsius);
// → 30
```

[Back](../../../README.md)
