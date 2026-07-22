# Phase 1 – C# Revision (Part 1)

## Topics Covered

1. OOP Concepts
2. Classes and Objects
3. Constructors
4. Inheritance

---

# 1. OOP (Object-Oriented Programming)

## Definition

Object-Oriented Programming (OOP) is a programming paradigm that organizes software using **objects** instead of only functions. Objects contain **data (fields/properties)** and **behavior (methods)**.

---

## Why OOP?

* Reusable code
* Easy maintenance
* Better organization
* Real-world modeling
* Easier debugging
* Secure code through encapsulation

---

## Four Pillars of OOP

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

These are the foundation of C# programming.

---

## Real-World Analogy

Imagine a **Car**.

### Data (Properties)

* Brand
* Model
* Color
* Speed

### Behaviour (Methods)

* Start()
* Stop()
* Accelerate()

A car is an **object**.

The blueprint used to manufacture cars is called a **class**.

---

# Class vs Object

| Class                             | Object          |
| --------------------------------- | --------------- |
| Blueprint                         | Real instance   |
| Logical                           | Physical        |
| No memory until object is created | Occupies memory |

Example:

```text
Blueprint → House Plan

Object → Actual House
```

---

# 2. Classes and Objects

## What is a Class?

### Definition

A class is a blueprint or template used to create objects.

It defines:

* Data (Fields/Properties)
* Behaviour (Methods)

---

## Syntax

```csharp
class Student
{
    public string Name;
    public int Age;

    public void Display()
    {
        Console.WriteLine(Name + " " + Age);
    }
}
```

### Explanation

* `class Student` → Creates a class.
* `Name`, `Age` → Fields.
* `Display()` → Method.

---

## What is an Object?

### Definition

An object is an instance of a class.

Objects occupy memory and can access the members of the class.

---

## Creating an Object

```csharp
Student s = new Student();
```

### Explanation

* `Student` → Class
* `s` → Reference variable
* `new` → Allocates memory
* `Student()` → Constructor

---

## Complete Example

```csharp
using System;

class Student
{
    public string Name;
    public int Age;

    public void Display()
    {
        Console.WriteLine("Name : " + Name);
        Console.WriteLine("Age  : " + Age);
    }
}

class Program
{
    static void Main()
    {
        Student s = new Student();

        s.Name = "Nick";
        s.Age = 24;

        s.Display();
    }
}
```

### Output

```text
Name : Nick
Age  : 24
```

---

# Memory Representation

```text
Class (Blueprint)

Student
│
├── Name
├── Age
└── Display()

        │

new Student()

        │

Object in Heap

Name = Nick

Age = 24
```

---

# 3. Constructors

## Definition

A constructor is a special method that is automatically called when an object is created.

It is used to initialize objects.

---

## Rules

* Name must be the same as the class.
* No return type.
* Called automatically.
* Can be overloaded.

---

## Default Constructor

```csharp
class Student
{
    public Student()
    {
        Console.WriteLine("Constructor Called");
    }
}
```

```csharp
Student s = new Student();
```

### Output

```text
Constructor Called
```

---

## Parameterized Constructor

```csharp
class Student
{
    public string Name;

    public Student(string name)
    {
        Name = name;
    }

    public void Display()
    {
        Console.WriteLine(Name);
    }
}
```

```csharp
Student s = new Student("Nick");

s.Display();
```

### Output

```text
Nick
```

---

## Constructor Overloading

```csharp
class Student
{
    public Student()
    {
        Console.WriteLine("Default");
    }

    public Student(string name)
    {
        Console.WriteLine(name);
    }
}
```

```csharp
Student s1 = new Student();

Student s2 = new Student("Nick");
```

### Output

```text
Default
Nick
```

---

## Types of Constructors

* Default Constructor
* Parameterized Constructor
* Copy Constructor (custom implementation in C#)
* Static Constructor
* Private Constructor

---

# Constructor vs Method

| Constructor          | Method              |
| -------------------- | ------------------- |
| Same name as class   | Any valid name      |
| No return type       | Can return values   |
| Called automatically | Called manually     |
| Initializes objects  | Performs operations |

---

# 4. Inheritance

## Definition

Inheritance allows one class to acquire the properties and methods of another class.

It promotes **code reusability**.

---

## Real-Life Example

```text
Animal

↓

Dog
```

Dog inherits common properties from Animal.

---

## Syntax

```csharp
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking");
    }
}
```

---

## Example

```csharp
using System;

class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is Eating");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is Barking");
    }
}

class Program
{
    static void Main()
    {
        Dog d = new Dog();

        d.Eat();

        d.Bark();
    }
}
```

### Output

```text
Animal is Eating
Dog is Barking
```

---

## Types of Inheritance in C#

| Type                          | Supported |
| ----------------------------- | --------- |
| Single                        | ✅ Yes     |
| Multilevel                    | ✅ Yes     |
| Hierarchical                  | ✅ Yes     |
| Multiple (through classes)    | ❌ No      |
| Multiple (through interfaces) | ✅ Yes     |

---

# Advantages of Inheritance

* Code Reusability
* Easy Maintenance
* Extensibility
* Reduces Duplicate Code
* Supports Polymorphism

---

# Quick Revision

### OOP

* Object-Oriented Programming
* Based on Objects

### Class

* Blueprint

### Object

* Instance of Class

### Constructor

* Initializes Objects

### Inheritance

* Acquires members of another class

---

# Interview Questions

### Q1. What is OOP?

**Answer:**
Object-Oriented Programming is a programming paradigm based on objects that contain data and behavior.

---

### Q2. What are the four pillars of OOP?

* Encapsulation
* Inheritance
* Polymorphism
* Abstraction

---

### Q3. What is a class?

A blueprint used to create objects.

---

### Q4. What is an object?

An instance of a class.

---

### Q5. What is a constructor?

A special method automatically called when an object is created.

---

### Q6. Can constructors have a return type?

No.

---

### Q7. Why is inheritance used?

To reuse code and establish relationships between classes.

---

### Q8. Does C# support multiple inheritance through classes?

No.

It supports multiple inheritance through interfaces.

---

# Flashcards

**Q:** What is OOP?
**A:** Object-Oriented Programming.

**Q:** What is a class?
**A:** A blueprint.

**Q:** What is an object?
**A:** An instance of a class.

**Q:** What keyword creates an object?
**A:** `new`

**Q:** When is a constructor called?
**A:** Automatically when an object is created.

**Q:** What is inheritance?
**A:** Acquiring properties and methods from another class.

---

# Mini Practice

1. Define OOP.
2. Name the four pillars of OOP.
3. What is the difference between a class and an object?
4. What is a constructor?
5. What is constructor overloading?
6. What is inheritance?
7. Name the types of inheritance supported in C#.
8. Can C# support multiple inheritance using classes? Explain.
