---
tags:
  - csharp/valueType_and_referenceType
files & media: Albahari Joseph - C# 12
status: In progress
creation date: 2024-07-01 13:46
modification date: Monday 1st July 2024 13:46:32
---

> [!tip] Value types
> *[[Value types]]* включают в себя большинство встроенных типов (в частности, все числовые типы, тип [[char]] и [[bool]]), а также пользовательские типы [[struct]] и [[enum]].

[](Value%20types.md)nce types
> К *[[Reference types]]* относятся все типы [[class]], [[array]], [[delegate]] и [[interface]]. (Сюда входит предопределенный тип string).

# <center>Value types</center>
Содержимое переменной или константы *[[Value types]]* - это просто значение. Например, содержимое встроенного типа значения [[int]] - это 32 бита данных. Вы можете определить собственный тип значения с помощью ключевого слова struct (Рисунок 1):
![[value-type instance in memory.png|center]]
<center>Figure 1. A value-type instance in memory</center>

### <center>Example</center>

```csharp
Point p1 = new Point();
p1.X = 7;
Point p2 = p1; // Assignment causes copy
Console.WriteLine (p1.X); // 7
Console.WriteLine (p2.X); // 7
p1.X = 9; // Change p1.X
Console.WriteLine (p1.X); // 9 
Console.WriteLine (p2.X); // 7

public struct Point { int X, Y; }
```
# <center>Reference types</center>
*[[Reference types]]* сложнее *[[Value types]]*, он состоит из двух частей: объекта и ссылки на этот объект. Содержимое переменной или константы ссылочного типа - это ссылка на объект, который содержит значение. Вот тип Point из нашего предыдущего примера, переписанный как [[class]], а не как [[struct]] (показано на рисунке 2):
### <center>Example</center>

```csharp
Point p1 = new Point();
p1.X = 7;
Point p2 = p1; // Copies p1 reference 
Console.WriteLine (p1.X); // 7 
Console.WriteLine (p2.X); // 7 
p1.X = 9; // Change p1.X 
Console.WriteLine (p1.X); // 9 
Console.WriteLine (p2.X); // 9

public class Point { int X, Y; }
```
![[Pasted image 20240703221747.png|center]]
