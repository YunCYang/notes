# Unit Test

## General Concept

### Purposes
1. Demonstrate that your code is *presently* working.
2. Demonstrate that your code continues to work when new code is added or existing code is changed.
3. Give you peace of mind when you refactor your code to improve its design.
  Note for #3. If refactoring the code requires you to change your tests, you are doing something wrong. Tests should not be fragile. Refactoring here means improving the internal design without changing external behavior.

### What unit test is not
Unit tests do not deal with with environment and external systems to the codebase. Unit test do not generate random data and pepper the application with it in unpredictalbe sequences (which would be a smoke test). Unit tests also do not exercise multiple components of the system and how they act.

### What unit test is
Unit tests isolate and exercise specific *units* of your code. One school of thought is that a unit is not a unit of code, but a unit of *behavior*. The smallest unit of code is the smallest unit of public behavior (public meaning code that exposes an API to another layer or part of your application).

### Best practices
1. Arrange, Act, Assert
  Arrange everything needed to run the experiment. (Example: instantiate an object.) Act, and invoke the method. Assert the result and see if it is true.

2. One assert per test method

3. Avoid test interdependence
  Each test should handle its own setup and tear down. Test should not depend on other tests.

4. Tests should be short, sweet, and visible
  Try not to abstract test setup to other classes.

5. If setting up tests is difficult, you might have a design problem

6. Add tests to the build
  If units tests fails, the build should fail.

7. Be careful of mocking
  The more you mock, the more your tests become tightly coupled to the implementation details of the dependencies of the system under test. Mock when:
  - External dependency will make your tests run egregiously slow (e.g. massively complex query, heavy computation, etc.).
  - When there's a randomized element to the execution path. Use fixed value to test.
  - When providing extenal dependencies requires more setup.

[Back](../../README.md)
