---
tags:
  - csharp/null
files & media: Albahari Joseph - C# 12
status: In progress
creation date: 2024-07-03 22:37
modification date: Wednesday 3rd July 2024 22:37:07
---

# <center> Null </center>
[[Reference types]] может быть присвоен литерал `[[null]]`, ***указывающий на то, что ссылка не указывает на объект***.

```csharp
Point p = null;
Console.WriteLine(p == null); // True
// The following line generates a runtime error 
// (a NullReferenceException is thrown): 
Console.WriteLine (p.X); 

class Point {...}
```

Обычно к [[Value types]] не может быть присвоен [[null]], примеры когда может быть присвоен [[null]], кратко описано в [[Value types#^e453e0]] и детально в [[Nullable Value Types]].