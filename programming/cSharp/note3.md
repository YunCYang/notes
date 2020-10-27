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

[Back](../../README.md)
