# Data Structure

## Code Structure
Designing the structure for code has two aspects:
- Machine: Runtime -> number of steps, memory usage, I/O, hardware limitations...
- Human: Ease of understanding (readability), speed to write the code...

## O Notation
Three types of O notation:
- o(N) (small o): best case of runtime grow rates -> often not important and ignored
- Ω(N) (omega): average runtime grow rates
- O(N) (big O): worst case of runtime grow rates -> often the most important one

### Calculate O Notation
Example:
```
const sumArray = array => {
  let sum = 0;
  for (let i = 0; i < array.length; i++) {
    sum += array[i];
  }
  return sum;
}
```
To calculate O notation, create a table for possible notations, and mark each process under each notation. calculate the sum for each notations at the end.

`let sum = 0;`                        -> only run once per program => 1
`let i = 0` in for loop               -> run only once             => 1
`i < array.length` check in for loop  -> run n times for each item => n
`sum += array[i];`                    -> run n times for each item => n
`i++` incrementor in for loop         -> run n times               => n
`return sum`                          -> run only once             => 1

1       n       n^2
_       _       ___
3       3       0

The O Notaion in the end is 3n + 3 => O(n)

Note that array methods are often not O(1), but O(n) by themselves.
While object methods might differ. checking keys in object doesn't have to loop through all the keys, so it's O(1).

[Back](../../README.md)
