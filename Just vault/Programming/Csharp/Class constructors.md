---
tags:
  - csharp/class/constructor
status: Done
creation date: 2024-07-05 22:05
modification date: Friday 5th July 2024 22:05:58
---
##### Source:
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=156]]
* https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/instance-constructors
# Definition
_*Instance constructors*_ - code that is executed when you create a new instance of a type with the [[new]] expression.
```csharp
Panda p = new Panda("Petey"); // Call constructor

public class Panda
{
	string name;
	public Panda(string n)
	{
		name = n;
	}
}
```
Single-statement constructors can also be written as expression-bodied members:
```csharp 
public Panda(string n) => name = n;
```
>[!note]
>If a parameter name (or any variable name, for that matter) conflicts with a field name, you can disambiguate by prefixing the field with a [[this]] reference:
```csharp
public Panda(string name) => this.name = name;
```
### <center>Instance constructors modifiers</center>

| Modifier | Name |
| :---: | :---: |
|Access modifiers | [[public]] [[internal]] [[private]] [[protected]] |
|Unmanaged code modifiers | [[unsafe]] [[extern]] |

### Overloading constructors
A [[class]] or [[struct]] may overload constructors. To avoid code duplication, one constructor can call another, using the [[this]] keyword:
```csharp
public class Wine
{
	public decimal Price;
	public int Year;
	public Wine(decimal price) => Price = price;
	public Wine(decimal price, int year) : this(price) => Year = year;
}
```
>[!note]
>When one constructor calls another, the _*called constructor*_ executes first.

You can pass an expression into another constructor, as follows:
```csharp
public Wine (decimal price, DateTime year) : this(price, year.Year) { }
```
### Implicit parameterless constructors
For classes, the C# compiler automatically generates a parameterless [[public]] constructor if and _*only if you do not define any constructors*_. However, as soon as you define at least one constructor, the parameterless constructor is no longer automatically generated.
### Constructor and field initialization order
We previously saw that fields can be initialized with default values in their declaration:
```csharp
class Player
{
	int shields = 50; // Initialized first
	int health = 100; // Initialized second
}
```
Field initializations occur _before_ the constructor is executed, and in the declaration order of the fields.
### Optional parameters 
^de01b6
#### Definition
In C#, optional parameters in [[class constructors]] are defined using default values. This means that when you declare a constructor parameter, you can specify a default value that will be used if an argument for that parameter is not passed when the constructor is called.
>[!note]
>1) Optional parameters can also be used in [[method]] and [[indexers]], not just `constructors`.
>2) When you use optional parameters, it is recommended that you place them _*after*_ the mandatory parameters.
#### <center>Example</center>
```csharp
public class Bunny
{
	public string Name;
	public bool LikesCarrots, LikesHumans;
	public Bunny(){}
	public Bunny(string name, 
				bool likesCarrots = false, 
				bool likesHumans = false)
	{
		Name = name;
		LikesCarrots = likesCarrots;
		LikesHumans = likesHumans;
	}
}
```
This would allow us to construct a `Bunny` as follows:
```csharp
Bunny b1 = new Bunny(name: "Bo", likesCarrots: true);
```
##### Drawbacks
Optional parameters have two drawbacks:
- The first is that while their use in constructors allows for *read-only types*[^1], they don’t (easily) allow for nondestructive mutation.
- The second drawback of optional parameters is that when used in public libraries, they hinder backward compatibility. This is because the act of adding an optional parameter at a later date breaks the assembly’s binary compatibility with existing consumers. (This is particularly important when a library is published on NuGet: the problem becomes intractable when a consumer references packages A and B, if A and B each depend on incompatible versions of L.) The difficulty is that each optional parameter value is baked into the calling site. In other words, C# translates our constructor call into this[^2]:
	```csharp
	Bunny b1 = new Bunny ("Bo", true, false);
	```


[^1]: read-only types mean types, values of which cannot be changed after the instance is created: [read-only properties](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FReserved%20keywords%2Freadonly), [read-only properties](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FReserved%20keywords%2Freadonly), [[const]]
[^2]: More about [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=163]]


