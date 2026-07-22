# Phase 1 – C# Revision (Part 4)

## Topics Covered

1. LINQ Basics
2. Generics
3. Phase 1 Quick Revision
4. Top Interview Questions
5. One-Page Cheat Sheet

---

# 1. LINQ (Language Integrated Query)

## Definition

**LINQ (Language Integrated Query)** is a feature of C# that allows you to query and manipulate data from different sources (collections, arrays, databases, XML, etc.) using a consistent syntax.

> **Interview Definition:**
>
> LINQ is a C# feature that provides a unified way to query data from collections, databases, XML, and other data sources.

---

# Why Do We Need LINQ?

Without LINQ:

```csharp
foreach(var item in students)
{
    if(item.Marks > 60)
    {
        Console.WriteLine(item.Name);
    }
}
```

With LINQ:

```csharp
var result = students.Where(s => s.Marks > 60);
```

LINQ makes code:

* Shorter
* More readable
* Easier to maintain

---

# LINQ Namespace

```csharp
using System.Linq;
```

---

# LINQ Query Syntax

```csharp
using System;
using System.Linq;

class Program
{
    static void Main()
    {
        int[] numbers = {10,20,30,40,50};

        var result =
            from n in numbers
            where n > 20
            select n;

        foreach(var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

### Output

```text
30
40
50
```

---

# LINQ Method Syntax

```csharp
using System.Linq;

var result = numbers.Where(n => n > 20);
```

---

# Common LINQ Methods

| Method              | Purpose               |
| ------------------- | --------------------- |
| Where()             | Filter data           |
| Select()            | Choose columns/values |
| OrderBy()           | Sort ascending        |
| OrderByDescending() | Sort descending       |
| First()             | First item            |
| FirstOrDefault()    | First item or default |
| Count()             | Count items           |
| Any()               | Check if data exists  |
| Max()               | Maximum value         |
| Min()               | Minimum value         |

---

# Example

```csharp
List<string> names =
    new List<string>()
{
    "Nick",
    "John",
    "Alice"
};

var result =
    names.Where(n => n.StartsWith("N"));

foreach(var item in result)
{
    Console.WriteLine(item);
}
```

### Output

```text
Nick
```

---

# Advantages of LINQ

* Less code
* Easy filtering
* Easy sorting
* Easy searching
* Strongly typed
* Readable

---

# 2. Generics

## Definition

Generics allow us to create **classes, methods, interfaces, and collections that work with different data types while maintaining type safety**.

> **Interview Definition:**
>
> Generics enable code reusability and type safety by allowing a single implementation to work with different data types.

---

# Why Generics?

Without Generics:

```csharp
ArrayList list = new ArrayList();

list.Add(10);

list.Add("Nick");
```

Different data types can be mixed, increasing the chance of runtime errors.

With Generics:

```csharp
List<int> numbers =
    new List<int>();
```

Only integers can be added.

---

# Generic Class Example

```csharp
using System;

class Demo<T>
{
    public T Value;

    public void Display()
    {
        Console.WriteLine(Value);
    }
}

class Program
{
    static void Main()
    {
        Demo<int> d1 = new Demo<int>();

        d1.Value = 100;

        d1.Display();

        Demo<string> d2 = new Demo<string>();

        d2.Value = "Nick";

        d2.Display();
    }
}
```

### Output

```text
100
Nick
```

---

# Generic Method

```csharp
class Demo
{
    public void Show<T>(T value)
    {
        Console.WriteLine(value);
    }
}
```

Usage:

```csharp
Demo d = new Demo();

d.Show(100);

d.Show("Nick");

d.Show(true);
```

### Output

```text
100
Nick
True
```

---

# Advantages of Generics

* Type Safety
* Code Reusability
* Better Performance
* Compile-time Checking
* No Boxing/Unboxing (for value types)

---

# Generic Collections

Common Generic Collections:

* List<T>
* Dictionary<TKey,TValue>
* Queue<T>
* Stack<T>
* HashSet<T>

---

# Generics vs Collections

| Non-Generic             | Generic                    |
| ----------------------- | -------------------------- |
| ArrayList               | List<T>                    |
| Hashtable               | Dictionary<TKey,TValue>    |
| Object Type             | Strongly Typed             |
| Runtime Errors Possible | Compile-time Type Checking |

---

# LINQ vs SQL

| LINQ               | SQL               |
| ------------------ | ----------------- |
| Used in C#         | Used in Database  |
| Queries Objects    | Queries Tables    |
| Uses `System.Linq` | Uses SQL Engine   |
| Strongly Typed     | Database Language |

---

# Phase 1 Quick Revision

## OOP

* Encapsulation
* Inheritance
* Polymorphism
* Abstraction

---

## Class

Blueprint for creating objects.

---

## Object

Instance of a class.

---

## Constructor

Special method called automatically when an object is created.

---

## Inheritance

Acquire members from another class.

---

## Polymorphism

One method, many behaviors.

* Method Overloading
* Method Overriding

---

## Abstraction

Hide implementation details.

---

## Interface

A contract that implementing classes must follow.

---

## Collections

Dynamic data structures.

Examples:

* List<T>
* Dictionary<TKey,TValue>

---

## Exception Handling

Keywords:

* try
* catch
* finally
* throw

---

## File Handling

Namespace:

```csharp
System.IO
```

Methods:

* WriteAllText()
* ReadAllText()
* AppendAllText()

---

## Delegate

A type-safe function pointer.

---

## Event

Notification mechanism built using delegates.

---

## LINQ

Language Integrated Query.

Namespace:

```csharp
System.Linq
```

---

## Generics

Reusable code with type safety.

---

# Top Interview Questions

### Q1. What are the four pillars of OOP?

* Encapsulation
* Inheritance
* Polymorphism
* Abstraction

---

### Q2. Difference between Overloading and Overriding?

| Overloading          | Overriding           |
| -------------------- | -------------------- |
| Compile Time         | Run Time             |
| Same Class           | Base & Derived Class |
| Different Parameters | Same Parameters      |

---

### Q3. Interface vs Abstract Class?

| Interface            | Abstract Class          |
| -------------------- | ----------------------- |
| Contract             | Base Class              |
| Multiple Inheritance | No Multiple Inheritance |
| No Object            | No Object               |

---

### Q4. What is a Delegate?

A type-safe function pointer.

---

### Q5. What is an Event?

A notification mechanism built using delegates.

---

### Q6. What is LINQ?

A feature that allows querying data using C#.

---

### Q7. Why Generics?

To provide type safety and code reusability.

---

### Q8. Which namespace is used for LINQ?

```csharp
System.Linq
```

---

### Q9. Which namespace is used for File Handling?

```csharp
System.IO
```

---

### Q10. Which collection stores key-value pairs?

```csharp
Dictionary<TKey,TValue>
```

---

# One-Page Cheat Sheet

## OOP

* Encapsulation → Hide Data
* Inheritance → Reuse Code
* Polymorphism → Many Forms
* Abstraction → Hide Implementation

---

## Class

Blueprint

---

## Object

Instance

---

## Constructor

Auto-called on object creation

---

## Interface

Contract

---

## Abstract Class

Cannot create object

---

## List<T>

Dynamic List

---

## Dictionary<TKey,TValue>

Key-Value Collection

---

## Exception Handling

* try
* catch
* finally
* throw

---

## File Handling

Namespace:

```csharp
System.IO
```

---

## Delegate

Method Reference

---

## Event

Notification

---

## LINQ

Namespace:

```csharp
System.Linq
```

Methods:

* Where()
* Select()
* OrderBy()
* Count()
* First()

---

## Generics

Reusable + Type Safe

Examples:

```csharp
List<int>

Dictionary<int,string>

Demo<T>
```

---

# Company-Specific Notes (Legacy ASP.NET Web Forms)

These concepts are used daily in legacy enterprise projects:

* **Inheritance** → Web Forms pages inherit from `System.Web.UI.Page`.
* **Interfaces** → Common in repositories, logging, and service contracts.
* **Collections** → Used to hold data retrieved from SQL Server.
* **Exception Handling** → Essential for robust web applications.
* **File Handling** → Used for uploads, downloads, reports, and logs.
* **Delegates & Events** → Power server-side events such as `Button_Click`, `Page_Load`, and `SelectedIndexChanged`.
* **LINQ** → Frequently used to filter and transform collections returned from databases or services.
* **Generics** → Widely used in `List<T>`, `Dictionary<TKey,TValue>`, repositories, and helper classes.

Mastering these topics gives you a strong foundation for understanding and maintaining a legacy **ASP.NET Web Forms + WCF + SQL Server** codebase.
