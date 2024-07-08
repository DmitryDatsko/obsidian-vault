---
tags:
  - csharp/reserved-keywords
status: Done
creation date: 2024-07-06 21:44
modification date: Saturday 6th July 2024 21:44:43
---
##### Source:
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=164]]
* https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/this
# Definition
The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.
The following are common uses of `this`:
- To qualify members hidden by similar names, for example:
	```csharp
	public class Employee
	{
		private string alias;
		private string name;
		public Employee(string name, string alias)
		{
			this.name = name;
			this.alias = alias;
		}
	}
	```
- To pass an object as a parameter to other methods, for example:
	```csharp
	CalcTax(this);
	```
- To declare [[indexers]], for example:
	```csharp
	public int this[int param]
	{
		get { return array[param]; }
		set { array[param] = value; }
	}
	```
Static member functions, because they exist at the [[class]] level and not as part of an [[object]], do not have a `this` pointer. _*It is an error to refer to this in a static method*_.