# Phase 1 – C# Revision (Part 2)

## Topics Covered

1. Polymorphism
2. Abstraction
3. Interfaces
4. Collections (List<T> & Dictionary<TKey, TValue>)

---

# 1. Polymorphism

## Definition

**Polymorphism** means **"many forms."**

In C#, polymorphism allows the **same method name** to perform **different tasks** depending on how it is used.

> **Interview Definition:**
>
> Polymorphism is an OOP concept that allows the same method or object to behave differently in different situations.

---

# Why Do We Need Polymorphism?

Without polymorphism, we would need different method names for every operation.

Example:

```text
AddInt()
AddDouble()
AddString()
```

With polymorphism:

```text
Add()
```

The compiler or runtime decides which version to execute.

---

# Types of Polymorphism

There are **two types** in C#:

1. **Compile-Time Polymorphism (Static Binding)**

   * Method Overloading

2. **Run-Time Polymorphism (Dynamic Binding)**

   * Method Overriding

---

# Compile-Time Polymorphism (Method Overloading)

## Definition

Method Overloading means creating **multiple methods with the same name but different parameters**.

The compiler decides which method to call.

---

## Rules

The methods must differ by:

* Number of parameters
* Type of parameters
* Order of parameters

Changing only the return type is **not allowed**.

---

## Example

```csharp
using System;

class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }
}

class Program
{
    static void Main()
    {
        Calculator c = new Calculator();

        Console.WriteLine(c.Add(10,20));
        Console.WriteLine(c.Add(10,20,30));
        Console.WriteLine(c.Add(10.5,20.5));
    }
}
```

### Output

```text
30
60
31
```

---

# Run-Time Polymorphism (Method Overriding)

## Definition

Method Overriding allows a derived class to provide its own implementation of a method already defined in the base class.

This uses:

* `virtual`
* `override`

---

## Example

```csharp
using System;

class Animal
{
    public virtual void Sound()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog barks");
    }
}

class Program
{
    static void Main()
    {
        Animal a = new Dog();

        a.Sound();
    }
}
```

### Output

```text
Dog barks
```

---

# How Overriding Works

```text
Animal
│
└── virtual Sound()

        ▲

Dog
│
└── override Sound()

        │

Animal a = new Dog();

        │

Calls Dog.Sound()
```

---

# virtual Keyword

Marks a method so it can be overridden.

```csharp
public virtual void Display()
{
}
```

---

# override Keyword

Provides a new implementation in the derived class.

```csharp
public override void Display()
{
}
```

---

# Overloading vs Overriding

| Method Overloading      | Method Overriding    |
| ----------------------- | -------------------- |
| Compile Time            | Run Time             |
| Same class              | Base + Derived class |
| Different parameters    | Same parameters      |
| No inheritance required | Inheritance required |
| Faster                  | Slightly slower      |

---

# Advantages of Polymorphism

* Code Reusability
* Flexibility
* Extensibility
* Easier Maintenance
* Supports Dynamic Behavior

---

# 2. Abstraction

## Definition

Abstraction means **showing only essential information while hiding implementation details**.

Example:

When driving a car, you use the steering wheel and pedals without knowing how the engine works internally.

---

# Why Abstraction?

It hides unnecessary complexity.

Users focus only on what they need.

---

# How is Abstraction Achieved?

Using:

* Abstract Classes
* Interfaces

In this lesson, we'll focus on **Abstract Classes**.

---

# Abstract Class

## Definition

An abstract class is a class that **cannot be instantiated**.

It acts as a base class.

It may contain:

* Abstract methods
* Normal methods
* Fields
* Constructors

---

# Abstract Method

An abstract method:

* Has no body.
* Must be implemented by derived classes.

Syntax:

```csharp
public abstract void Display();
```

---

# Example

```csharp
using System;

abstract class Animal
{
    public abstract void Sound();

    public void Eat()
    {
        Console.WriteLine("Animal is Eating");
    }
}

class Dog : Animal
{
    public override void Sound()
    {
        Console.WriteLine("Dog Barks");
    }
}

class Program
{
    static void Main()
    {
        Dog d = new Dog();

        d.Sound();

        d.Eat();
    }
}
```

---

### Output

```text
Dog Barks
Animal is Eating
```

---

# How Abstract Class Works

```text
Abstract Class

Animal

│

├── Sound()   ← Abstract

└── Eat()     ← Normal

        ▲

Dog

│

Implements Sound()
```

---

# Rules of Abstract Classes

* Cannot create an object directly.
* Can contain abstract and non-abstract methods.
* Can contain constructors.
* Can contain fields and properties.
* Derived classes must implement all abstract methods.

---

# Abstract Class vs Normal Class

| Abstract Class               | Normal Class                    |
| ---------------------------- | ------------------------------- |
| Cannot create object         | Can create object               |
| Can contain abstract methods | Cannot contain abstract methods |
| Used as a base class         | Used directly                   |

---

# Advantages of Abstraction

* Hides implementation details.
* Improves security.
* Reduces complexity.
* Makes code easier to maintain.

---

# Polymorphism vs Abstraction

| Polymorphism                            | Abstraction                                  |
| --------------------------------------- | -------------------------------------------- |
| Many forms                              | Hides implementation                         |
| Same method, different behavior         | Shows only essential details                 |
| Achieved using Overloading & Overriding | Achieved using Abstract Classes & Interfaces |

---

# Interview Questions

### Q1. What is Polymorphism?

Polymorphism is an OOP concept that allows the same method or object to behave differently in different situations.

---

### Q2. Name the two types of polymorphism.

* Compile-Time Polymorphism
* Run-Time Polymorphism

---

### Q3. What is Method Overloading?

Creating multiple methods with the same name but different parameters.

---

### Q4. What is Method Overriding?

Providing a new implementation of a base class method in a derived class using `virtual` and `override`.

---

### Q5. What is Abstraction?

Showing only essential details while hiding implementation.

---

### Q6. Can we create an object of an abstract class?

No.

---

### Q7. Can an abstract class have a constructor?

Yes.

---

### Q8. Which keyword is used for method overriding?

`override`

---

### Q9. Which keyword allows a method to be overridden?

`virtual`

---

# Flashcards

**Q:** What does polymorphism mean?
**A:** Many forms.

**Q:** How many types of polymorphism are there?
**A:** Two.

**Q:** Which keyword enables overriding?
**A:** `virtual`

**Q:** Which keyword performs overriding?
**A:** `override`

**Q:** Can an abstract class be instantiated?
**A:** No.

**Q:** Can an abstract class contain normal methods?
**A:** Yes.

---

# Mini Practice

1. Define polymorphism.
2. Explain the difference between overloading and overriding.
3. What is compile-time polymorphism?
4. What is run-time polymorphism?
5. What is the purpose of the `virtual` keyword?
6. What is the purpose of the `override` keyword?
7. Define abstraction.
8. Can an abstract class have constructors?
9. Can an abstract class contain both abstract and normal methods?
10. Why do we use abstraction in real-world applications?

# Phase 1 – C# Revision (Part 2)

## Topics Covered



---

# 3. Interfaces

## Definition

An **Interface** is a contract that defines **what a class must do**, but **not how it does it**.

An interface contains only method, property, event, or indexer declarations. The implementing class provides the actual implementation.

> **Interview Definition:**
>
> An interface is a contract that specifies a set of members that a class must implement.

---

# Why Do We Need Interfaces?

Interfaces are used to:

* Achieve abstraction
* Achieve multiple inheritance
* Reduce coupling
* Increase flexibility
* Support dependency injection (commonly used in enterprise applications)

---

# Real-Life Analogy

Think of a **mobile charger**.

```text
Wall Socket (Interface)
        │
        ├── Samsung Charger
        ├── Motorola Charger
        └── OnePlus Charger
```

The wall socket defines the standard. Different chargers implement it in their own way.

---

# Syntax

```csharp
interface IAnimal
{
    void Sound();
}
```

**Note:**

* Interface names usually begin with **I** (e.g., `IAnimal`, `ILogger`, `IRepository`).

---

# Implementing an Interface

```csharp
using System;

interface IAnimal
{
    void Sound();
}

class Dog : IAnimal
{
    public void Sound()
    {
        Console.WriteLine("Dog Barks");
    }
}

class Program
{
    static void Main()
    {
        IAnimal animal = new Dog();

        animal.Sound();
    }
}
```

### Output

```text
Dog Barks
```

---

# Multiple Inheritance Using Interfaces

C# **does not support multiple inheritance through classes**, but it **does support multiple inheritance through interfaces**.

```csharp
interface IPrinter
{
    void Print();
}

interface IScanner
{
    void Scan();
}

class MultiFunctionMachine : IPrinter, IScanner
{
    public void Print()
    {
        Console.WriteLine("Printing...");
    }

    public void Scan()
    {
        Console.WriteLine("Scanning...");
    }
}
```

### Output

```text
Printing...
Scanning...
```

---

# Interface vs Abstract Class

| Interface                                         | Abstract Class                        |
| ------------------------------------------------- | ------------------------------------- |
| Contract                                          | Base class                            |
| Supports multiple inheritance                     | Does not support multiple inheritance |
| No object creation                                | No object creation                    |
| Used for common behavior across unrelated classes | Used for related classes              |
| Members must be implemented                       | Can contain implemented methods       |

---

# When to Use an Interface?

Use an interface when:

* Multiple unrelated classes should follow the same contract.
* You need multiple inheritance.
* You want loosely coupled code.

**Company Example**

```text
ILogger

│

├── FileLogger
├── DatabaseLogger
└── EmailLogger
```

Each class logs data differently but follows the same interface.

---

# 4. Collections

## What is a Collection?

A **Collection** is a class used to store and manage a group of objects dynamically.

Collections are preferred over arrays because they can grow or shrink during runtime.

---

# Why Not Arrays?

Array:

```csharp
int[] numbers = new int[3];
```

Problems:

* Fixed size
* Cannot increase or decrease length

Collections solve this problem.

---

# Generic Collections

The most commonly used collections are:

* `List<T>`
* `Dictionary<TKey, TValue>`

---

# List<T>

## Definition

A `List<T>` is a generic collection that stores elements of the **same type** in order.

---

## Example

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> students = new List<string>();

        students.Add("Nick");
        students.Add("John");
        students.Add("Alice");

        foreach (string student in students)
        {
            Console.WriteLine(student);
        }
    }
}
```

### Output

```text
Nick
John
Alice
```

---

# Common List Methods

| Method     | Purpose            |
| ---------- | ------------------ |
| Add()      | Add item           |
| Remove()   | Remove item        |
| RemoveAt() | Remove by index    |
| Insert()   | Insert at position |
| Contains() | Check existence    |
| Count      | Total items        |
| Clear()    | Remove all items   |

---

# Dictionary<TKey, TValue>

## Definition

A `Dictionary<TKey, TValue>` stores data as **key-value pairs**.

Each key must be unique.

---

## Example

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Dictionary<int, string> students =
            new Dictionary<int, string>();

        students.Add(101, "Nick");
        students.Add(102, "John");
        students.Add(103, "Alice");

        foreach (var item in students)
        {
            Console.WriteLine(item.Key + " : " + item.Value);
        }
    }
}
```

### Output

```text
101 : Nick
102 : John
103 : Alice
```

---

# Common Dictionary Methods

| Method          | Purpose            |
| --------------- | ------------------ |
| Add()           | Add key-value pair |
| Remove()        | Remove item        |
| ContainsKey()   | Check key          |
| ContainsValue() | Check value        |
| Count           | Total items        |
| Clear()         | Remove all items   |

---

# List vs Dictionary

| List                     | Dictionary                 |
| ------------------------ | -------------------------- |
| Stores values only       | Stores key-value pairs     |
| Access by index          | Access by key              |
| Duplicate values allowed | Duplicate keys not allowed |
| Ordered                  | Based on keys              |

---

# Company Usage

### List<T>

Used when retrieving records from the database.

Example:

```text
List<Employee>
List<Student>
List<Customer>
```

---

### Dictionary<TKey, TValue>

Used when fast lookup is required.

Example:

```text
EmployeeID → Employee

CountryCode → CountryName

RoleID → RoleName
```

---

# Advantages of Collections

* Dynamic size
* Faster than manual array handling
* Built-in methods
* Easy to use
* Strongly typed (Generic Collections)

---

# Interview Questions

### Q1. What is an Interface?

An interface is a contract that defines the members a class must implement.

---

### Q2. Why do we use interfaces?

To achieve abstraction, multiple inheritance, and loose coupling.

---

### Q3. Can we create an object of an interface?

No.

---

### Q4. Does C# support multiple inheritance?

Not through classes.

Yes, through interfaces.

---

### Q5. What is a Collection?

A collection is a class used to store and manage groups of objects dynamically.

---

### Q6. Why is List<T> better than an array?

Because it can grow and shrink dynamically and provides many built-in methods.

---

### Q7. What is Dictionary<TKey, TValue>?

A generic collection that stores data as key-value pairs.

---

### Q8. Can duplicate keys exist in a Dictionary?

No.

Keys must be unique.

---

# Flashcards

**Q:** What is an interface?
**A:** A contract that classes must implement.

**Q:** Can an interface have an object?
**A:** No.

**Q:** Which collection stores key-value pairs?
**A:** `Dictionary<TKey, TValue>`.

**Q:** Which collection stores ordered values?
**A:** `List<T>`.

**Q:** Can a Dictionary contain duplicate keys?
**A:** No.

**Q:** Which namespace contains generic collections?
**A:** `System.Collections.Generic`.

---

# Mini Practice

1. Define an interface.
2. Why do we use interfaces?
3. Can C# support multiple inheritance through classes?
4. What is a `List<T>`?
5. What is a `Dictionary<TKey, TValue>`?
6. Name five methods of `List<T>`.
7. Name four methods of `Dictionary<TKey, TValue>`.
8. What is the difference between `List<T>` and `Dictionary<TKey, TValue>`?
9. Which namespace contains generic collections?
10. Give one real-world example where a `Dictionary<TKey, TValue>` is more suitable than a `List<T>`.

