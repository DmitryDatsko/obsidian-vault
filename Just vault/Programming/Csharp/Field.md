---
tags:
  - csharp/class/field
files & media: Albahari Joseph - C# 12
status: Done
creation date: 2024-07-04 17:05
modification date: Thursday 4th July 2024 17:05:06
---
##### Source:
* https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/fields
# Definition
A _field_ is a variable of any type that is declared directly in a [[class]] or [[struct]][^1].
```csharp
class Octopus{
	string name;
	public int Age = 10;
}
```

>[!warning]
>If access modifier doesnt specified explicit, field access modifier by default be [[private]].
>For example above, field `string name` are implicit [[private]].

#### The readonly modifier
![[readonly#^70027e]]

Fields allow the following modifiers:

| Modifier | Name |
| :---: | :---: |
| Static modifier | [[static]] |
| Access modifiers | [[public]] [[internal]] [[private]] [[protected]] |
| Inheritance modifier | [[new]] |
| Unsafe code modifier | [[unsafe]] |
| Read-only modifier | [[readonly]] |
| Threading modifier | [[volatile]] |

### Field initialization
Field initialization is optional. An uninitialized field has a default value (0, '\0', null, false). Field initializers run before constructors:
```csharp
public int Age = 10;
```
A field initializer can contain expressions and call methods:
```csharp
static readonly string TempFolder = System.IO.Path.GetTempPath();
```
For convenience, you can declare multiple fields of the same type in a comma separated list. This is a convenient way for all the fields to share the same attributes and field modifiers:
```csharp
static readonly int legs = 8, eyes = 2;
```
### Constants
![[const#^87357e]]
###### Example[^2]:
```csharp
public class Test
{
	public const string Message = "Hello World;
}
```
**[More about const](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Fconst)**.
#### Differs from `static readonly` field
A constant can serve a similar role to a static [[readonly]] field, but it is much more restrictive—both in the types you can use and in field initialization semantics. A [constant](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Fconst) also differs from a [[static]] [[readonly]] field **in that the evaluation of the constant occurs at compile time**; thus
```csharp
public static double Circumference (double radius) 
{
	return 2 * System.Math.PI * radius; 
}
```
is compiled to:
```csharp
public static double Circumference (double radius) 
{ 
	return 6.2831853071795862 * radius; 
}
```
It makes sense for PI to be a constant because its value is predetermined at compile time. In contrast, a static readonly field’s value can potentially differ each time the program is run:
```csharp
static readonly DateTime StartupTime = DateTime.Now;
```
>[!warning]
>Использование `static readonly` полей вместо `const` позволяет избежать проблемы, при которой изменение значения константы в одной сборке не отражается в других сборках, которые её используют. В отличие от `const`, значение `static readonly` поля обновляется во всех частях кода при повторной компиляции, обеспечивая актуальность данных.

**[More about readonly fields](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Freadonly).**

[^1]: https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/fields
[^2]: [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=152]]