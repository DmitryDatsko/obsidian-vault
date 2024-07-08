---
tags:
  - csharp/reserved-keywords
status: Done
creation date: 2024-07-04 19:59
modification date: Thursday 4th July 2024 19:59:32
---
##### Source:
* [Microsoft Docs](https://learn.microsoft.com/uk-ua/dotnet/csharp/language-reference/keywords/const)
* [Medium](https://medium.com/@comp87/c-constants-versus-read-only-variables-d79100eeac9)

# Definition

^d59a8a

A constant is an immutable [[Variable]] or [[Field]] declared with the `const` keyword, _*whose value must be initialized at the time it is declared*_[^1]. Constants are implicitly [[static]] and cannot be changed after their declaration.
You use the `const` keyword to declare a constant [[field]] or a local constant[^2]. ^87357e
### <center>Example</center>
```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```
## Interpolated strings
Beginning with C# 10, [[interpolated strings]] may be constants, if _all expressions used are also constant strings_. This feature can improve the code that builds constant strings:
### <center>Example</center>
```csharp
const string Language = "C#";
const string Platform = ".NET";
const string FullProductName = $"{Platform} - Language: {Language}";
```
# Remarks
The type of a constant declaration specifies the type of the members that the declaration introduces. The initializer of a local constant or a constant field must be a constant expression that can be implicitly converted to the target type.

A constant expression is an expression that can be fully evaluated at compile time. Therefore, the only possible values for constants of [[Reference types]] are [[string]] and a null reference.

The constant declaration can declare multiple constants, such as:
```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```
The [[static]] modifier *_is not allowed_* in a constant declaration.
A constant can participate in a constant expression, as follows:
```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```
>[!note]
>The [[readonly]] keyword differs from the `const` keyword. A `const` field can only be initialized at the declaration of the field. A `readonly` [[Field]] can be initialized either at the declaration or in a constructor. Therefore, `readonly` fields can have different values depending on the constructor used. Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`
### Constants in method
* Constants can also be declared[^3] local to a method:
```csharp
void Test()
{
	const double twoPI = 2 * Math.PI;
}
```
### Nonlocal constants modifiers
| Modifier | Name |
| :---: | :---: |
| Access modifiers | [[public]], [[internal]], [[private]], [[protected]] |
| Inheritance modifier | [[new]] |
# Examples
```csharp 
public class ConstTest
{
    class SampleClass
    {
        public int x;
        public int y;
        public const int C1 = 5;
        public const int C2 = C1 + 5;

        public SampleClass(int p1, int p2)
        {
            x = p1;
            y = p2;
        }
    }

    static void Main()
    {
        var mC = new SampleClass(11, 22);
        Console.WriteLine($"x = {mC.x}, y = {mC.y}");
        Console.WriteLine($"C1 = {SampleClass.C1}, C2 = {SampleClass.C2}");
    }
}
/* Output
    x = 11, y = 22
    C1 = 5, C2 = 10
*/
```
The following example demonstrates how to declare a local constant:
```csharp
public class SealedTest
{
    static void Main()
    {
        const int C = 707;
        Console.WriteLine($"My local constant = {C}");
    }
}
// Output: My local constant = 707
```

[^1]: [[Variable#^7d2901]]
[^2]: [[Variable#^59a408]]
[^3]: ![[Variable#^f4e596]]