# Interview

## Programming
### JavaScript
#### Code Exercise
- Click counter
#### Questions
- Paradigm
  JavaScript supports both OOP with prototypal inheritance and functional gaming.

  A programming paradigm is a way or method in which we write code to solve different types of problems. JavaScript is a multi-paradigm language.

  - Declarative (functional) programming
    Characteristic:
    - You declare what you want to happen, not how it’s done. Simplify application and optimize performance.
    - No loops or conditional statements.
    - Data is often considered immutable values.
    - Similar to SQL language.
  - Imperative (procedral / OOP) programming
    Characteristic:
    - You specify exactly how to do something, not just the desired outcome. More straight-forward to understand.
    - Data is often considered mutable variables.
    - Inheritance is commonplace and typically used as an example of reusable code.

  Note: functional programming has mostly won over class inheritance in JavaScript.

- Closure
  A closure is a function inside another function, that is returned or passed to another function. It is a  combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment).

  The inner function has access to the outer function’s scope.

  Use:
    - Data privacy: the enclosed variables are only in scope within the containing (outer) function.
    - Partial application: fixes (partially applies the function to) one or more arguments inside the returned function, and the returned function takes the remaining parameters as arguments in order to complete the function application.

- Promise
  An object that may produce a single value some time in the future: either a resolved value, or a reason that it’s not resolved.

  3 possible states:
    - Fulfilled
    - Rejected
    - Pending

- Asynchronous programming
  - Synchronous programming
    Code is executed sequentially from top-to-bottom, blocking on long-running tasks such as network requests and disk I/O.

  - Asynchronous programming
    The engine runs in an event loop. When a blocking operation is needed, the request is started, and the code keeps running without blocking for the result. When the response is ready, an interrupt is fired, which causes an event handler to be run, where the control flow continues. In this way, a single program thread can handle many concurrent operations.

    User interfaces are asynchronous by nature, and spend most of their time waiting for user input to interrupt the event loop and trigger event handlers.

- OOP - object oriented programming
  - Object
  - Class
  - Prototype
    Have objects as a programmer-provided data structure that can be manipulated with functions. Write classes and frequently a constructor function to create objects.

    Prototypal inheritance - objects without classes, and prototype delegation. It creates a link when creating the object. For objects and class inheritance, it does not copy but only links properties and behavior.

- Functional programming
  You declare what you want to happen, not how it’s done. Separates mutable variables from non-mutable constants.

  Pure function, simple function composition.

  - Closure
  - First class function
    First class functions can be stored in an array, variable, or object; passed as an arguments to another function; returned from another function.
  - Lambda
    Fat-arrow functions, remove the `function` and `return` keywords.

- Two-way data binding vs. one-way data flow
  Two way data binding means that UI fields are bound to model data dynamically such that when a UI field changes, the model data changes with it and vice-versa.

  One way data flow means that the model is the single source of truth. Changes in the UI trigger messages that signal user intent to the model (or “store” in React). Only the model has the access to change the app’s state. The effect is that data always flows in a single direction, which makes it easier to understand.

  One way data flows are deterministic, whereas two-way binding can cause side-effects which are harder to follow and understand.

- React Hook
  A functional programming approach for abstracting away complexity from managing the state (i.e. mutable variables) of an app.

- Classical inheritance vs. prototypal inheritance
  - Class inheritance
    Instances inherit from classes. Instances are typically instantiated via constructor functions with the `new` keyword.
  - Prototypal inheritance
    Instances inherit directly from other objects. Instances are typically instantiated via factory functions or `Object.create()`.

  In JavaScript, prototypal inheritance is simpler & more flexible than class inheritance.

- SaaS - Software as a Service
  A software distribution model in which a third-party provider hosts applications and makes them available to customers over the Internet.

## General

[Back](../README.md)
