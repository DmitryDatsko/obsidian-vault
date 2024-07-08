---
tags: csharp/class-deconstructor
status: Not started
creation date: 2024-07-06 16:17
modification date: Saturday 6th July 2024 16:17:08
---
##### Source:
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=159]]

# Definition
A `deconstructor` (also called a deconstructing method) acts as an approximate opposite to a [constructor](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Fconstructors): whereas a [constructor](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2Fconstructors) typically takes a set of values (as parameters) and assigns them to [fields](obsidian://open?vault=Just%20vault&file=Programming%2FCsharp%2FField), a `deconstructor` does the reverse and assigns fields back to a set of variables. 
A deconstruction method must be called `Deconstruct` and must have one or more [[out]] parameters, such as in the following [[class]]:
```csharp
class Rectangle 
{ 
	public readonly float Width, Height;
	
	public Rectangle (float width, float height) 
	{ 
		Width = width; Height = height; 
	} 
	
	public void Deconstruct (out float width, out float height) 
	{ 
		width = Width; height = Height;
	}
}
```
The following special syntax calls the `deconstructor`:
```csharp
var rect = new Rectangle(3, 4);
(float width, float height) = rect; // Deconstruction
Console.WriteLine(width + " " + height); // 3 4
```

>[!warning]
>Class deconstructor is not as useful as [[tuple deconstructor]]!