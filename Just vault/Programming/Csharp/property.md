---
tags: csharp/class/property
status: Not started
creation date: 2024-07-05 16:58
modification date: Friday 5th July 2024 16:58:59
---
##### Source:
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=164]]
* https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties#properties-overview

# Definition
Properties look like [fields](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField) from the outside, _but internally they contain logic_, like [methods](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Fmethod) do. 
A `property` is declared like a [field](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField) but with a get/set block added. Here’s how to implement `CurrentPrice` as a `property`:
```csharp
public class Stock
{
	decimal currentPrice;
	public decimal CurrentPrice
	{
		get { return currentPrice; }
		set { currentPrice = value; }
	}
}
```
[[get]] and [[set]] denote property accessors. The [[get]] accessor runs when the property is _read_. It must return a value of the property’s type. The [[set]] accessor runs when the property is _assigned_. It has an implicit parameter named value of the property’s type that you typically assign to a [[private]] [field](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField) (in this case, `currentPrice`).
>[!note] Auto-implemented properties
> In some cases, property [[get]] and [[set]] accessors just assign a value to or retrieve a value from a backing field **without including any extra logic**[^1]. It's called _auto-implemented properties_, and there is virtually no difference between [field](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField) and _*auto-implemented properties*_.

>[!note]
>Although properties are accessed in the same way as [fields](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField), they differ in that they give the implementer complete control over getting and setting its value.

### <center>Properties modifiers</center>

| Modifier | Name |
| :---: | :---: |
|Static modifier |[[static]]|
|Access modifiers | [[public]] [[internal]] [[private]] [[protected]] |
| Inheritance modifiers | [[new]] [[virtual]] [[abstract]] [[override]] [[sealed]] |
|Unmanaged code modifiers | [[unsafe]] [[extern]] |

### Read-only property
The [[readonly]] modifier cannot be applied to a property:
```csharp
public class Example  
{  
	// Property cannot be 'readonly'
    public readonly string Name { get; set; }  
}
```
A property is **read-only** if it specifies only a [[get]] accessor, and it is **write-only** if it specifies only a [[set]] accessor. Write-only properties are _rarely_ used.
### Expression-bodied properties
You can declare a **read-only** property, such as the one in the preceding example, more tersely as an expression-bodied property. A fat arrow replaces all the braces and the [[get]] and [[return]] keywords:
```csharp
public decimal Worth => currentPrice * sharesOwned;
```
With a little extra syntax, [[set]] accessors can also be expression-bodied:
```csharp
public decimal Worth
{
	get => currentPrice * sharesOwned;
	set => sharesOwned = value / currentPrice;
}
```

[^1]: https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties#auto-implemented-properties