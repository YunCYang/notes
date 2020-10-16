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

## Date and Time
Create a DateTime object that represents the current time:
```
DateTime myValue = DateTime.Now;
Console.WriteLine(myValue.ToString());
```

Create a DateTime object of a certain date:
`DateTime myValue = new DateTime(1990, 1, 1);`
`DateTime myValue = DateTime.Parse("1/1/1990");`

### Display
`myValue.ToString()` - default.
`myValue.ToShortDateString()` - displays date only in short format.
`myValue.ToShortTimeString()` - displays time only in short format.
`myValue.ToLongDateString()` - displays date only in long format.
`myValue.ToLongTimeString()` - displays time only in long format.
...etc
`myValue.Month()` - displays month only.

### Manipulate
`myValue.AddDays(3)` - adds 3 day time to the DateTime object.
Similar methods includes `AddHours()`, etc.
Add negative number to subtract time.

Find time span:
```
TimeSpan age = DateTime.Now.Subtract(myBirthday);
Console.WriteLine(age.TotalDays);
```
