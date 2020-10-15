# C#

## Debugging
Click on the left of the line numbers to set a breakpoint.

Use the gear icon of the breakpoint to set up Conditions or Actions.

## Array
Declaration:
`int[] numbers = new int[5];` Declare an array called 'numbers' of type `int` with a length of 5.
`int[] numbers = new int[] {4, 8, 15, 16};` Declare an array and initialize it at the same time.

`numbers[0] = 4;`

`numbers.Length` - the length of the array.

### Loop through an array
for loop:
`for (int i = 0; i < arrayName.Length; i++) {...}`

foreach:
`foreach (var item in collection) {...}`

## Methods
### Overloading
Overloading is what happens when you have two methods with the same name but different signatures. Different signatures means different data type, different number of parameters, etc.
