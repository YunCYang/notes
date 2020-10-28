# C#

## Enum
A special data type that enables for a variable to be a set of predefined constants. The variable are also by default, associated with incrementing int starting with 0.
```
enum Season
{
  Spring, // 0
  Summer, // 1
  Autumn, // 2
  Winter  // 3
}
```

## switch
```
switch (Season)
{
  case Spring:
    ...
    break;
  default:
    ...
    break;
}
```

When using enum as the argument for the switch, hit the tab key will automatically create respective cases.

## Handling exceptions - try catch
```
try
{
  ...
}
catch (FileNotFoundException Fex) // check specific exceptions first
{
  ...
}
catch (Exception ex) // Exception is the most general type of exception
{
  Console.WriteLine(ex.Message);
}
finally
{
  // Code to finalize
  // Ex: setting objects to null, closing database connection
}
```

Use it when you are dealing with things that are out of your control, e.g. reading files, user input.

## namespace and using
Use the `using ...` to avoid typing the whole namespace every time.
`System.Timers.Timer myTimer = new Timer(2000);`
is the same as
```
using System.Timers;

// ...

Timer myTimer = new Timer(2000);
```

use Ctrl + '.' to add namespace to using statement on libraries without references.

## Event
### Timer
```
using System.Timers;

...
{
  Timer myTimer = new Timer(2000); // 2 seconds
  myTimer.Elapsed += MyTimerElapsed; // attached the function MyTimerElasped to Elapsed method
  // Elapsed will run according to the argument provided to Timer() (2s in this case)
  myTimer.Start(); // start the timer

  ...
  myTimer.Elapsed -= MyTimerElapsed; // remove the timer function
}
...
private static void MyTimer_Elapsed(object sender, ElapsedEventArgs e)
{
  Console.WriteLine("Elapsed: {0:HH:mm:ss:fff}", e.SignalTime);
}
```

[Back](../../README.md)
