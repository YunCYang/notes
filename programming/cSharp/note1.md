# C#

## Hello World - `string`
`Console.WriteLine("Hello World!");`

Console: represents the console window.

### With `string` variable
```
string aFriend = "Yun";
Console.WriteLine("Hello " + aFriend);
```

### With string interpolation
`Console.WriteLine($"Hello {aFriend}");`

Add a `$` before the opening quote of the string, put variables in between curly braces {}.

#### Replacement message
Similar to string interpolation.
`Console.WriteLine("Hello {0}", aFriend);`

### `string` properties - `Length`
Console.WriteLine($"The name {aFriend} has {aFriend.Length} letters.");

### `string` methods - `Trim`, `TrimStart`, `TrimEnd`, `Replace`, `ToUpper`, `ToLower`, `Substring`
```
string greeting = "      Hello World!       ";
string alteredGreeting = greeting.TrimStart();
Console.WriteLine($"{alteredGreeting}");

alteredGreeting = greeting.TrimEnd();
alteredGreeting = greeting.Trim();

alteredGreeting = greeting.Replace("Hello", "Greetings");

alteredGreeting = greeting.ToUpper();
alteredGreeting = greeting.ToLower();

alteredGreeting = greeting.Substring(2, 4); // grab 4 chars after position 2
```

### Search strings - `Contains`, `StartsWoth`, `EndsWith`
```
string songLyrics = "You say goodbye, and I say hello";
Console.WriteLine(songLyrics.Contains("goodbye"));
Console.WriteLine(songLyrics.Contains("greetings"));

Console.WriteLine(songLyrics.StartsWith("You"));
Console.WriteLine(songLyrics.EndsWith("You"));
```

Returns a bollean value `true` or `false`.

### `ToString()`
`variableName.ToString();` - converts variable type to string.

### Backslash '\'
Backslash is used to escape characters. `"\""`
To show backslash, either escape it `"\\"`, or add a '@' in front of the string `@"..\.."`.

### `String.Format()`
`string myString = String.Format("{0} and {1}", "first", "second");`
Latter texts are insert into the template. {0} and {1} (and so on) can be reused or switched.

Format the data: e.g. display as currency `String.Format("{0:C}", 123.45);`.
Custom format: `String.Format("Phone number: {0: (###) ###-####}", 1234567890);`

`String.Format()` and `string.Format()` ?

### `StringBuilder`
Strings are immutable, when "altering" a string, you are actually creating a new string and discarding the old one, which might causes performance issue. Use `StringBuilder` in this case.

`StringBuilder myString = new StringBuilder();`

Check for `StringBuilder` methods.

## Console
`Console.WriteLine("...");` - outputs to console with a newline in the end.
`Console.Write();` - outputs to console, stays in the same line.
`Console.ReadLine();` - gets input from user, can also be used to pause the program.
`Console.Clear();` - clears the screen.

`string userValue = Console.ReadLine();` - example of saving user input.

## Number
### Integer
`int a = 18;`

Note that integer division always produces an integer result, e.g. 11 / 3 = 3.

```
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

#### Integer limits
```
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");

int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Use `MaxValue` and `MinValue` to find the limits.
If a calculation produces a value that exceeds those limits, you have an underflow or overflow condition. `max + 3` = `min + 2`.

### Double
Double-precision floating point number. Double precision number have twice the number of binary digits as single-precision, which is declared using `float`. It is more common to use double precision than single precision numbers.

`double a = 19;`

### Decimal
`decimal` type has a smaller range but greater precision than `double`.

`decimal a = 1.0M;`

`M` suffix is needed when declaring a `decimal` type with actual number.

### Others
`int.Parse();` - similar to `parseInt()` in JavaScript.

```
Random myRandom = new Random();
int randomNumber = myRandom.Next(1, 11);
```
Creates a random number with a minimum of 1 and a maximum of 10.

## Branches and loops
### `if` statement
```
int a = 5;
int b = 3;
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

`string message = (userValue == "1") ? "boat" : "strand of lint";`

Equality symbol here is `==`.

### `while` and `do` ... `while` loop
```
int counter = 0;
while (counter < 10)
{
  Console.WriteLine($"Hello World! The counter is {counter}");
  counter++;
}
```
```
int counter = 0;
do
{
  Console.WriteLine($"Hello World! The counter is {counter}");
  counter++;
} while (counter < 10);
```
`while` loop tests the condition before executing the code following the `while`. `do` ... `while` loop executes the code first, and then checks the condition.

### `for` loop
```
for(int counter = 0; counter < 10; counter++)
{
  Console.WriteLine($"Hello World! The counter is {counter}");
}
```

for (for initializer; for condition; for iterator) {}

### `foreach` loop
Check `list`.

### do-while loop
```
do {
...
} while ()
```

## `list`
```
var names = new List<string> { "Yun", "Ana", "Felipe" };
foreach (var name in names)
{
  Console.WriteLine($"Hello {name.ToUpper()}!");
}

names.Add("Maria");
names.Remove("Ana");
foreach (var name in names)
{
  Console.WriteLine($"Hello {name.ToUpper()}!");
}

Console.WriteLine($"My name is {names[0]}.");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list.");

Console.WriteLine($"The list has {names.Count} people in it");
```

Use `Add` and `Remove` methods to edit the list, use `Count` to find the length of the list. Reference individual items by index.

### Searching and sorting the list
Use `IndexOf` to search and return the index of the item. If the item isn't in the list, `IndexOf` returns `-1`.

```
var index = names.IndexOf("Felipe");
if (index != -1)
  Console.WriteLine($"The name {names[index]} is at index {index}");

var notFound = names.IndexOf("Not Found");
Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

names.Sort();
foreach (var name in names)
{
  Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

The `Sort` method sorts all the items in the list in their normal order (alphabetically for strings).

### Example: fibonacci numbers
```
var fibonacciNumbers = new List<int> {1, 1};

while (fibonacciNumbers.Count < 20)
{
    var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
    var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

    fibonacciNumbers.Add(previous + previous2);
}
foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```
