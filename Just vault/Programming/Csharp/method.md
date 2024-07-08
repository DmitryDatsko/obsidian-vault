---
tags:
  - csharp/method
status: Done
creation date: 2024-07-05 16:57
modification date: Friday 5th July 2024 16:57:54
---
##### Source:
* https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods
* https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/classes#156-methods
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=154]]
# Definition
A method is a code block that contains a series of statements. A program causes the statements to be executed by calling the method and specifying any required method arguments. In C#, every executed instruction is performed in the context of a method.
>[!note] Specification definition
>A method is a member that implements a computation or action that can be performed by an object or class.[^1]
### <center>Methods modifiers</center>

| Modifier | Name |
| :---: | :---: |
|Static modifier |[[static]]|
|Access modifiers | [[public]] [[internal]] [[private]] [[protected]] |
| Inheritance modifiers | [[new]] [[virtual]] [[abstract]] [[override]] [[sealed]] |
| Partial method modifier | [[partial]] |
|Unmanaged code modifiers | [[unsafe]] [[extern]] |
|Asynchronous code modifier | [[async]]| 

### Expression-bodied methods
A method that comprises a single expression, such as
```csharp
int Foo(int x){ return x * 2; }
```
can be written more tersely as an _*expression-bodied*_ method. A fat arrow replaces the braces and `return` keyword:
```csharp
int Foo(int x) => x * 2;
```
Expression-bodied functions can also have a void return type:
```csharp
void Foo(int x) => Console.WriteLine(x);
```

# Local method definition
_Local functions_ are methods of a type that are nested in another member. They can only be called from their containing member.[^2]
## Local methods
You can define a method within another method
```csharp
void WriteCubes() 
{ 
	Console.WriteLine(Cube (3));
	Console.WriteLine (Cube (4));
	Console.WriteLine (Cube (5));
	int Cube (int value) => value * value * value; 
}
```
The `local method` (`Cube`, in this case) is visible only to the enclosing method (`WriteCubes`).
Likewise local methods can access the _local variables_[^3] and parameters of the enclosing method, `local methods` can appear within other function kinds, such as property accessors, constructors, and so on.
Likewise its possible to put local methods inside other local methods.
>[!warning]
>Local methods cannot be overloaded. This means that methods declared in top-level statements (which are treated as local methods) cannot be overloaded.
### Static local methods
Adding the static modifier to a local method (from C# 8) prevents it from seeing the local variables and parameters of the enclosing method.
###### Example without `static`
```csharp
class Program
{
	static void Main(string[] args)
	{
		int variable = 10;

		void LocalMethod()
		{
			Console.WriteLine(variable);
		}

		LocalMethod();
	}
}
```
###### Example with `static`
```csharp
class Program
{
	static void Main(string[] args)
	{
		int variable = 10;

		void LocalMethod()
		{
			// Compilation error: variable is not accessible 
			// Console.WriteLine(variable);
		}

		LocalMethod();
	}
}
```
### Overloading methods
For overload methods, need to define multiple methods with the _**same name**_ and _**same return type**_.
```csharp
void Foo (int x) {...} 
void Foo (double x) {...} 
void Foo (int x, float y) {...} 
void Foo (float x, int y) {...}
```
However, the following pairs of methods cannot coexist in the same type, because the return type and the params modifier are not part of a method’s signature:
```csharp
void Foo (int x) {...} 
float Foo (int x) {...} // Compile-time error 

void Goo (int[] x) {...} 
void Goo (params int[] x) {...} // Compile-time error
```
Whether a parameter is pass-by-value or pass-by-reference is also part of the signature. For example, `Foo(int)` can coexist with either `Foo(ref int)` or `Foo(out int)`. However, `Foo(ref int)` and `Foo(out int)` cannot coexist:
```csharp
void Foo (int x) {...} 
void Foo (ref int x) {...} // OK so far 
void Foo (out int x) {...} // Compile-time error
```

[^1]: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/classes#156-methods
[^2]: https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/local-functions
[^3]: [[Variable#^59a408]]