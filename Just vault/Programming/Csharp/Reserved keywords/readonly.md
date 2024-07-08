---
tags:
  - csharp/fields-modifier
  - csharp/reserved-keywords
status: Not started
creation date: 2024-07-04 22:12
modification date: Thursday 4th July 2024 22:12:27
---
##### Source:
* https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/readonly
* [[Albahari Joseph-Csharp 12 in a Nutshell2024.pdf#page=151]]
# <center>Definition</center>

^a17b29

The `readonly` modifier prevents a [[Field]] from being modified after construction. A read-only [[Field]] can be assigned only in its declaration or within the enclosing type’s constructor. A `readonly` field can be assigned and reassigned multiple times within the field declaration and constructor.
A `readonly` field can't be assigned after the constructor exits. This rule has different implications for [[Value types]] and [[Reference types]]: ^70027e
* Because [[Value types]] directly contain their data, a field that is a `readonly` value type is immutable.
* Because [[Reference types]] contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object. That object _*might not be immutable*_. The `readonly` modifier prevents replacing the field value with a different instance of the [[Value types]]. However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.
* In a [[readonly struct]] type definition, `readonly` indicates that the structure type is immutable.