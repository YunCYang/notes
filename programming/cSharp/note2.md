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

## Class
Declare the class (or blueprint):
```
class Car
{
  public string Make { get; set; }
  public string Model { get; set; }
  public int Year { get; set; }

  public decimal DeterineMarketValue ()
  {
    decimal carValu;

    if (Year > 1990) // access properties inside the class
      carValue = 10000;
    else
      carValue = 2000;

    return carValue;
  }
}
```

Create an object based on the class:
```
Car myCar = new Car();
myCar.Make = "ABC";
...
```
or Object initializer syntax
`Car myCar = new Car() {Make = "BMW", Model = "750li"};`

`public` methods allow you to call it outside of the class, while `private` method doesn't.

Class is a reference type, same handle will point to the same data.
```
Car myCar = new Car();
Car myOtherCar;
myOtherCar = myCar;
```

Changing `myCar.Make` will also changes `myOtherCar.Make`.

### Constructor
```
class Car
{
  public string Make { get; set; }
  public string Model { get; set; }

  // the constructor inside the class
  // you could load from a configuration file, a database, etc.
  public Car()
  {
    Make = "Toyota";
  }

  // overload constructor
  public Car(string make, string model)
  {
    Make = make;
    Model = model;
  }
}

Car myCar = new Car(); // Car() <- indicates calling the constructor function
```

### `static`
The keyword `static` means that you do not have to create an instance of that class in order to utilize the method.

`static` can be used on classes or methods.

```
class Car
{
  public static void MyMethod()
  {
    ...
  }
}

Car.MyMethod(); // calling MyMethod does not require you to create an instance of Car.
```

## Assembly

Add reference to assemblies:
- Solution Explorer -> References, right click and choose "add reference".
- Use NuGet for external libraries.
- Add reference for libraries created by yourself:
  1. Create new project, choose "Class Library" as the template.
  2. Use previous method, browse and find the file.
- To make it easier to get custom library, select "solution" as the template and create library inside. Need to select start up project on one of the file.

## Collection
### ArrayList (old)
ArrayLists are dynamically sized, with features like sorting and removing items
The issue is you can add different data types into an ArrayList at the same time, not strongly typed.
```
ArrayList myArrayList = new ArrayList();
myArrayList.Add(car1);
```

### List<T>
```
List<Car> myList = new List<Car>();
myList.Add(car1);
foreach (Car car in myList)
{
  Console.WriteLine(car.Model);
}
```

Collection initializer:
```
List<Car> myList = new List<Car>() {
  new Car {Make = "...", Model = "..."},
  new Car {Make = "...", Model = "..."}
};
```

### Dictionary<TKey, TValue>
```
Dictionary<string, Car> myDictionary = new Dictionary<string, Car>();

myDictionary.Add(car1.VIN, car1);

Console.WriteLine(myDictionary["car1VIN"].Make);
```
