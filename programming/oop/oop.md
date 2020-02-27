# Object Oriented Programming

## Interface

In object-oriented programming, an interface allows you to specify a set of function signatures and hide the implementation of those functions in an "implementing" class. Interfaces form a contract between the class and the outside world.

An interface generally defines the set of methods (or messages) that an instance of a class that has that interface could respond to.

Some languages such as Java, PHP, and C# have actual interface with its language specific semantics.

## Polymorphism

Polymorphism is the practice of designing objects to share behaviors and to be able to override shared behaviors with specific ones. Polymorphism takes advantage of inheritance in order to make this happen.

Example:
When you call the String function (which converts a value to a string) on an object, it will call the toString method on that object to try to create a meaningful string from it. Some of the standard prototypes define their own version of toString so they can create a string that contains more useful information than `[object Object]`.

```
Rabbit.prototype.toString = function() {
  return `a ${this.type} rabbit`;
};

console.log(String(blackRabbit));
// → a black rabbit
```

When a piece of code is written to work with objects that have a certain interface — in this case, a toString method — any kind of object that happens to support this interface can be plugged into the code, and it will just work.

A for/of loop can loop over several kinds of data structures. This is another case of polymorphism — such loops expect the data structure to expose a specific interface, which arrays and strings do.

[Back](../../README.md)
