---
tags:
  - csharp/object-initializers
status: In progress
creation date: 2024-07-06 16:54
modification date: Saturday 6th July 2024 16:54:49
---
##### Source:
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=161]]

# Definition
Object initializers let you assign values to any accessible fields or properties of an object at creation time _*without having to invoke a constructor*_ followed by lines of assignment statements.
```csharp
public class Bunny 
{ 
	public string Name;
	public bool LikesCarrots, LikesHumans;
	public Bunny () {} 
	public Bunny (string n) => Name = n; 
}
```
Using object initializers, you can instantiate Bunny objects as follows:
```csharp
Bunny b1 = new Bunny { Name="Bo", LikesCarrots=true, LikesHumans=false }; 
Bunny b2 = new Bunny ("Bo") { LikesCarrots=true, LikesHumans=false };
```