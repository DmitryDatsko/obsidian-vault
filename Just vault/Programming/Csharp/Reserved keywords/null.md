---
tags: csharp/reserved-keywords
status: Not started
creation date: 2024-07-06 19:12
modification date: Saturday 6th July 2024 19:12:47
---
##### Source:
* 

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