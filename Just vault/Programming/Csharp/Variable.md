---
tags:
  - csharp/variable
files & media: https://developerhelp.microchip.com/xwiki/bin/view/software-tools/c-programming/variables/declarations-definitions/
status: Done
creation date: 2024-07-04 17:06
modification date: Thursday 4th July 2024 17:06:21
---
##### Sources:

^792646

* [C Programming Variable Declarations and Definitions](https://developerhelp.microchip.com/xwiki/bin/view/software-tools/c-programming/variables/declarations-definitions/);
* [Variables in C#(Medium)](https://medium.com/@praveen.rao.g.1990/variables-in-c-691ffeff3a1c).
* [# C# identifier naming rules and conventions(Microsoft Docs)](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names)
# Definition
Variables represent storage locations. Every variable has a type that determines what values can be stored in the variable. C# is a type-safe language, and the C# compiler guarantees that values stored in variables are always of the appropriate type. The value of a variable can be changed through assignment or through use of the ++ and -- operators.[^1]
> [!note] 
> C# is a statically-typed language, which means that the data type must be known at compile time.
# <center>Variable declaration</center>

^7d2901

### Definition
Declaration(объвление) - a variable declaration is when you specify a type and an identifier _**but have not yet assigned a value**_ to the variable.[^2] ^f4e596
### <center>Examples</center>
```csharp
int x; // variable are declared, but not assigned or initialized
string str; // same as above
long l; // same as first
bool b; // same as first
```
# <center>Variable initialization</center>
### Definition
Initialization(инициализация) - a variable initialization is when you assigning an initial value to variable.
### <center>Examples</center>
- Standard type of initialization:
```csharp
int myNumber = 42;
```
- Initialization after declaration(strictly speaking, not initialization, ***just assignment***[^3]):
```csharp
// Declaration
int myNumber;

// Initialization(assignment, to be precise)
myNumber = 42;
```
# <center>Naming rules</center>
Valid identifiers must follow these rules. The C# compiler produces an error for any identifier that doesn't follow these rules:
- Identifiers must start with a letter or underscore (`_`).
- Identifiers can contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters. For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).
- Case-sensitive (e.g., `myVar` and `myvar` are different).
- Cannot be a reserved C# keyword (e.g., `int`, `class`, `if`), if need to use C# keywords ![[_Reserved keywords#^446954]]
### Pascal case
* Use pascal casing ("PascalCasing") when naming a [[class]], [[interface]], [[struct]], [[record]] or [[delegate]] type.[^4]: ^2e5829
```csharp
public class DataService
{
}

public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);

public struct ValueCoordinate
{
}

public delegate void DelegateType(string message);
```
* When naming an [[interface]], use pascal casing in addition to prefixing the name with an `I`. This prefix clearly indicates to consumers that it's an [[interface]].
```csharp
public interface IWorkerQueue
{
}
```
* When naming [[public]] members of types, such as [[Field]]s, properties, [[event]]s, use pascal casing. Also, use pascal casing for all methods and local functions.
```csharp
public class ExampleEvents
{
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```
* When writing positional records, use pascal casing for parameters as they're the public properties of the [[record]].
```csharp
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```
### Camel case
Use camel casing ("camelCasing") when naming [[private]] or [[internal]] fields and prefix them with `_`. Use camel casing when naming local variables, including instances of a delegate type.
```csharp
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```
When working with [[static]] fields that are [[private]] or [[internal]], use the `s_` prefix and for thread static use `t_`.
```csharp
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```
When writing method parameters, use camel casing.
```csharp
public T SomeMethod<T>(int someNumber, bool isValid)
{
}
```
# <center>Variable scope</center>
Variables have a scope, which defines where they can be used.
A variable’s scope can be:
- **Local :** Declared inside a [[method]], constructor, or block, and only accessible within that scope. ^59a408
- **Class-Level ([[Field]]) :** Declared within a [[class]], accessible to all methods in the [[class]].
- **Static :** Class-level variables shared among all instances of a [[class]].
```csharp
class MyClass  
{  
	int classLevelVar; // Class-level variable  
  
	void MyMethod()  
	{  
		int localVar; // Local variable  
		classLevelVar = 10; // Access class-level variable  
	}  
}
```

[^1]: Переменные представляют собой места хранения данных. Каждая переменная имеет тип, который определяет, какие значения могут храниться в переменной. C# - язык с безопасным типом, и компилятор C# гарантирует, что значения, хранящиеся в переменных, всегда будут иметь соответствующий тип. Значение переменной может быть изменено путем присваивания или с помощью операторов ++ и --.
[^2]: https://developerhelp.microchip.com/xwiki/bin/view/software-tools/c-programming/variables/declarations-definitions/
[^3]: https://stackoverflow.com/questions/3779707/c-sharp-variable-initializations-vs-assignment
[^4]: https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/identifier-names#pascal-case