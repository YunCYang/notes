# Data Structure

## Hash Table
Hash table is an unordered list. The table itself is an array, each element in the array is an index pointing to the address of another array consisting of the data itself.

Each data has key of string type. The key is run through a hashing function, which converts the key into a number. The number points to the index of the array (hash table), and an address can be found at the index pointing to the actual array storing the data. Inside the array which store the data, the data is stored as the form of an array with a key-value pair. Multiple data could be stored at the same array in a index of the hash table.

Example: storing a key of 'hello' and value of 'world'
- run the key through a hash function to get the index
  `hash['hello']` -> 912
- find the address in the hash table
  [(addr1), (add2), (addr3), ... (addr912), ...]
- find the array at the address
  [
    ['someKey', 'someValue'],
    ['hello', 'world']
  ]
- check if the key is the same, and retrieve the data
  'world'

- Read
  - Next / Prev value      O(N)
  - Get value by key       O(1)
  - Search by value        O(N)
- Insert
  - Arbitrary insert value O(1)
- Delete
  - Arbitrary delete value O(1)
- Update
  - Replace value          O(1)
  - Change key             O(1)
- Bulk Operations

Hash table is often used when the data has a key of arbitrary strings. The down side is the amout of overhead and memory it takes. Hash table is good when we have the key, but bad when we have to search of operate base on the value.

The hash table has to have a big size (often 10 times more than the data) to avoid collision, which is having 2 or more data at an array of a same of address. Normal hash table often only have 1 or 2 data at an array.

## String

Most languages stores a string as an array of characters with a length overhead.

length = 5; `['h', 'e', 'l', 'l', 'o']`

The machine checks the length to know when to stop reading the array.

C language stores the array as a continuous data of charaters with a null character \0 marking the end.

### Difference between UTF8/UTF16 and UTF32
UTF32 is fixed size, each character takes 4 bytes.

UTF8 and UTF16 are dynamically sized.

For UTF8, if the character is original ASCII (1 to 127), it takes only 1 byte, otherwise it takes between 2 to 4 bytes (like unicode).

ASCII character: ASCII character always start with a 0

Example: 'e' is `01100101`

The machine reads the initial 0 will know the following character only takes 1 byte.

If the character is outside of the ASCII range, it will start with a `110`. To determine how much bytes the character takes, the machine checks how many starts with `110` continously.

Because UTF8 is dymamic, to find a character inside the string takes O(N) since characters don't have a fixed size, and we have to go through the whole table 1 by 1 to check the character size.

In JavaScript, the string is stored as UTF16, but looking up a character inside a string is O(1). This is because JS stores the address for each character inside an array, and the user look up the address inside the array.

[Back](../../README.md)
