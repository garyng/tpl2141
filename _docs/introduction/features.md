---
title: Unique features
category: Introduction
order: 3
---

There are some unique features of C# that make itself stand out from the sheer amount of programming languages in the wild.

Support for

1. [Property syntax](#property-syntax)
1. [Partial classes and methods](#partial-classes-and-methods)
1. [Extension methods](#extension-methods)
1. [Anonymous types](#anonymous-types)
1. [Language Integrated Query (LINQ)](#language-integrated-query-linq)

are some of the prominent ones.

## Property syntax

Property syntax allow classes to provide a flexible mechanism for getting, setting, or computing the value of a private field {% cite Docs2017 --prefix features %}.

```cs
public class SaleItem
{
   public string Name { get; set; }
   public decimal Price { get; set; }
}
```

## Partial classes and methods

Partial classes and methods allow a class’s members to be defined in multiple files {% cite Docs2015 --prefix features %} which provide the following benefits:

1. multiple programmers to work on the same class at the same time
1. provide a mechanism to extend a compiler generated code

```cs
// File1
public partial class Employee
{
    public void DoWork()
    {
    }

    // partial method
    partial void onNameChanged();
}

// File2
public partial class Employee
{
    public void GoToLunch()
    {
    }

    partial void onNameChanged()  
    {  
        // method body  
    }  
}
```

## Extension methods

Extension method is a statically-defined method that also allows programmers to extend the functionality of a class that cannot be modified, such as the built-in types.

```cs
public static class StringExtension
{
    // extend the built in string type
    public static int WordCount(this string str)
    {
        return str.Split(new char[] {' ', '.','?'}, StringSplitOptions.RemoveEmptyEntries).Length;
    }
}
```

## Anonymous types

Anonymous type provide a simpler way to encapsulate a set of read only property into a single object and it is not necessary to define a type first. The type name is generated by compiler {% cite Docs2015a --prefix features %}.

```cs
var v = new { Amount = 108, Message = "Hello" };
Console.WriteLine(v.Amount + v.Message);
```

## Language Integrated Query (LINQ)

Language Integrated Query (LINQ) provide a unified language for querying data from various data source including XML documents, SQL databases, ADO.NET datasets, .NET collections or any other format provided that a LINQ provider is available {% cite Docs2015b --prefix features %}

```cs
// Query syntax
var result = from student in students
                where student.Scores[0] > 90
                select student;

// Fluent syntax
var result = students.Where(student => student.Scores[0] > 90);
```

## References

{% bibliography --cited_in_order --prefix features %}