# Data Structure

## Code Structure
Designing the structure for code has two aspects:
- Machine: Runtime -> number of steps, memory usage, I/O, hardware limitations...
- Human: Ease of understanding (readability), speed to write the code...

## Note
32 bit vs. 64 bit: difference is in memory address.
When comparing different data structure, we often compares the speed to perform CRUD operations.
Whether deallocation of unneeded data is needed depends on if the language has a garbage collector that automatically does the deallocation. Manual deallocation is not required for languages like JavaScript, but necessary for languages like C / C++.

### Example CRUD Operation
- Read
  - Next / Prev value
  - Get value by key
  - Search by value
- Insert
  - Append / Prepend
  - Arbitrary insert by key
- Delete
  - Delete first / last value
  - Arbitrary delete by key
- Update
  - Replace value at key
  - Swap
- Bulk Operations

### Simple Static Array Structure
Note: not a JavaScript array, but an ordinary array.

Overhead for a static array: start location, length and data type length.

For a 32 bit system, each item in an array takes up 32 bits, or 4 bytes.

[5, 18, 207, 3005, ...]

If integer 5 (index 0) starts at memory location 0x37, then 18 (index 1) starts at memory location 0x41, which is :

The start (0x37) + index (1) * size (4) = 0x41

Getting value by key is a simple O(1) operation.
To append a value, because the array size is set and cannot be changed, a new array will be created with a size of (original size + 1) in place of the old array, so it is a O(N) operation. Same for similar type that would alter the array size.

Creating a new array in place of the old one is called reallocating.

Memory leak happens when you allocate memory but not deallocate it after it is not needed.

To swap two values in an array, a temporary memory the size of the integer is allocated to temporary store one of the data and deallocated when the operation if finished.

- Read
  - Next / Prev value         O(1)
  - Get value by key          O(1)
  - Search by value           O(N)
- Insert
  - Append / Prepend          O(N)
  - Arbitrary insert by key   O(N)
- Delete
  - Delete first / last value O(N)
  - Arbitrary delete by key   O(N)
- Update
  - Replace value at key      O(1)
  - Swap                      O(1)
- Bulk Operations

Arrays are good when there's a constant need to read the data.

### Dynamic Array Structure
The dynamic array would have an actual array length and an effectice array length.
Overhead for a dynamic array: start, length, capacity.

The array will be allocated memory of the size of the capacity, but the data inside will only occupy the size of the length. The length changes everytime new data is added or deleted in the array. Array will only be reallocated when it reaches the capacity.

Because there is no reallocation, the O(N) for prepending or deleting the first data here is a faster O(N) compared to operations in a static array.

Deleting the last value would be just changing the length to (original length - 1) and left the old value in there.

Vector is a wrapper around dynamic array that handles the resizing for the user.

- Read
  - Next / Prev value         O(1)
  - Get value by key          O(1)
  - Search by value           O(N)
- Insert
  - Append / Prepend          O(1) / O(N)
  - Arbitrary insert by key   O(N)
- Delete
  - Delete first / last value O(N) / O(1)
  - Arbitrary delete by key   O(N)
- Update
  - Replace value at key      O(1)
  - Swap                      O(1)
- Bulk Operations

### Stack
Stack is a LIFO dynamic array / vector combination.

- Read
  - Next / Prev value         X
  - Get value by key          Last value only
  - Search by value           X
- Insert
  - Append / Prepend          O(1) / X
  - Arbitrary insert by key   X
- Delete
  - Delete first / last value X / O(1)
  - Arbitrary delete by key   X
- Update
  - Replace value at key      X
  - Swap                      X
- Bulk Operations

### Queue

Queue is FIFO structure similar to stack.

Overhead for a queue contains: start, end, start of capacity.

To remove a value from a queue, just move the start of capacity backwards one location.

When all the value are removed from a queue, the start of capacity will go all the way back to the start again.

- Read
  - Next / Prev value         X
  - Get value by key          First value only
  - Search by value           X
- Insert
  - Append / Prepend          X / O(1)
  - Arbitrary insert by key   X
- Delete
  - Delete first / last value O(1) / X
  - Arbitrary delete by key   X
- Update
  - Replace value at key      X
  - Swap                      X
- Bulk Operations

### Tuple

Tuple is a static array with different types (boolean, integer, string, ...) stored inside.

When storing a string inside a tuple, the size of the string is often stored at the space in front of the string itself. When data of the string is changed, the size will also be changed to mark the end of the string, so as to avoid reallocation because of the size change. The string will always take up the same amount of memory.

Databases of store data in tuples.

For PostgreSQL (and other SQL databases?), text datatype is stored as a memory location and the text size. The data size inside the tuple is more flexible, but because the actual data is not stored in the tuple, it runs slower since the database will have to look up in another memory location to retrieve the text. For small amount of text, it is easier and makes the operation faster to store the data as varchar(data size).

[Back](../../README.md)
