---
tags:
  - csharp/value-types
files & media: https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/types#83-value-types
status: Done
creation date: 2024-07-03 22:29
modification date: Wednesday 3rd July 2024 22:29:31
---
# <center> Value types</center>
A value type is either a struct type or an enumeration type. C# provides a set of predefined struct types called the _**simple types**_. The simple types are identified through keywords.

Unlike a variable of a reference type, a variable of a value type can contain the value `null` only if the value type is a nullable value type ([§8.3.12](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/types#8312-nullable-value-types)). For every non-nullable value type there is a corresponding nullable value type denoting the same set of values 
plus the value `null`. ^e453e0

Assignment to a variable of a value type creates a _copy_ of the value being assigned. This differs from assignment to a variable of a reference type, which copies the reference but not the object identified by the reference.