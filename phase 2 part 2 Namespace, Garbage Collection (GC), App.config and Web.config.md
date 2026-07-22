# Phase 2 – .NET Fundamentals (Part 2)

## Topics Covered

1. Namespace
2. Garbage Collection (GC)
3. App.config & Web.config

---

# 1. Namespace

## Definition

A **Namespace** is a logical container that groups related classes, interfaces, structures, delegates, and enums together.

It helps organize code and prevents naming conflicts.

> **Interview Definition:**
>
> A namespace is a logical grouping of related types used to organize code and avoid name collisions.

---

# Why Do We Need Namespaces?

Imagine a large project with hundreds of classes.

Without namespaces:

```text
Student
Employee
Customer
Order
Invoice
```

Different developers might create classes with the same name.

Example:

```text
Project A

Student

Project B

Student
```

This causes naming conflicts.

Namespaces solve this problem.

---

# Real-Life Analogy

Think of a **library**.

```text
Library

│

├── Science

├── History

├── Computer

└── Mathematics
```

The library is like a project.

Each section is like a namespace.

Books are like classes.

---

# Syntax

```csharp
namespace SchoolManagement
{
    class Student
    {
    }
}
```

---

# Using a Namespace

```csharp
using SchoolManagement;

class Program
{
    static void Main()
    {
        Student s = new Student();
    }
}
```

Without `using`, you must write:

```csharp
SchoolManagement.Student s =
new SchoolManagement.Student();
```

---

# Common .NET Namespaces

| Namespace                  | Purpose             |
| -------------------------- | ------------------- |
| System                     | Basic classes       |
| System.IO                  | File handling       |
| System.Collections.Generic | Collections         |
| System.Linq                | LINQ                |
| System.Data                | Database            |
| System.Web                 | ASP.NET Web Forms   |
| System.Configuration       | Configuration files |

---

# Company Example

```text
Company.Project.UI

Company.Project.BLL

Company.Project.DAL

Company.Project.Models

Company.Project.Utilities
```

Each layer has its own namespace to keep the code organized.

---

# Advantages

* Organizes code
* Avoids naming conflicts
* Improves readability
* Easier maintenance

---

# Namespace vs Assembly

| Namespace             | Assembly               |
| --------------------- | ---------------------- |
| Logical grouping      | Physical compiled file |
| Organizes code        | Contains compiled code |
| Exists in source code | Exists as DLL/EXE      |

---

# 2. Garbage Collection (GC)

## Definition

**Garbage Collection (GC)** is an automatic memory management feature of the CLR that removes objects from memory when they are no longer in use.

> **Interview Definition:**
>
> Garbage Collection is the automatic process of reclaiming memory occupied by unused managed objects.

---

# Why Garbage Collection?

Without GC:

```text
Program

↓

Creates Objects

↓

Memory Keeps Filling

↓

Application Crashes
```

With GC:

```text
Program

↓

Creates Objects

↓

Unused Objects

↓

Garbage Collector Removes Them

↓

Memory Becomes Available
```

---

# Managed Heap

Objects created with `new` are stored in the **Managed Heap**.

Example:

```csharp
Student s = new Student();
```

The object is created in the Managed Heap.

The reference (`s`) is stored on the Stack.

---

# Stack vs Heap

| Stack                  | Heap           |
| ---------------------- | -------------- |
| Stores local variables | Stores objects |
| Faster                 | Larger memory  |
| Automatically managed  | Managed by CLR |

---

# Garbage Collection Process

```text
Object Created

↓

Object Used

↓

Reference Lost

↓

Eligible for GC

↓

Memory Reclaimed
```

---

# Example

```csharp
Student s = new Student();

s = null;
```

Setting `s = null` does **not** immediately destroy the object.

It only makes the object **eligible for garbage collection**.

---

# Generations in GC

The CLR divides objects into three generations.

```text
Generation 0

↓

Generation 1

↓

Generation 2
```

### Generation 0

* Newly created objects
* Collected most frequently

### Generation 1

* Objects that survive Generation 0

### Generation 2

* Long-lived objects

Examples:

* Cache
* Static objects
* Application-level objects

---

# Dispose() vs Garbage Collection

| Garbage Collector    | Dispose()                    |
| -------------------- | ---------------------------- |
| Automatic            | Manual                       |
| Frees managed memory | Releases unmanaged resources |
| Controlled by CLR    | Called by programmer         |

---

# Using Statement

```csharp
using(FileStream fs =
new FileStream("a.txt", FileMode.Open))
{
}
```

When the block ends:

* `Dispose()` is called automatically.

---

# Advantages

* Prevents memory leaks
* Automatic memory management
* Improves application stability
* Reduces programmer effort

---

# 3. App.config & Web.config

## Why Configuration Files?

Hardcoding values is not a good practice.

Bad Example:

```csharp
string connection =
"Server=.;Database=StudentDB;...";
```

If the server changes, the application must be recompiled.

Instead, store configuration in a configuration file.

---

# App.config

## Definition

`App.config` is the configuration file used by **Console Applications**, **Windows Forms**, and **WPF** applications.

---

## Example

```xml
<?xml version="1.0" encoding="utf-8"?>

<configuration>

  <appSettings>

    <add key="Company"
         value="ABC Pvt Ltd"/>

  </appSettings>

</configuration>
```

---

# Reading AppSettings

```csharp
using System.Configuration;

string company =
ConfigurationManager.AppSettings["Company"];

Console.WriteLine(company);
```

### Output

```text
ABC Pvt Ltd
```

---

# Web.config

## Definition

`Web.config` is the configuration file used by **ASP.NET Web Forms** and **ASP.NET MVC** applications.

---

# Common Sections

```xml
<configuration>

 <connectionStrings>

 </connectionStrings>

 <appSettings>

 </appSettings>

 <system.web>

 </system.web>

</configuration>
```

---

# Connection String Example

```xml
<connectionStrings>

 <add
 name="StudentDB"

 connectionString="Server=.;
 Database=StudentDB;
 Integrated Security=True"/>

</connectionStrings>
```

---

# Reading Connection String

```csharp
using System.Configuration;

string cs =
ConfigurationManager
.ConnectionStrings["StudentDB"]
.ConnectionString;
```

---

# App.config vs Web.config

| App.config               | Web.config                                                       |
| ------------------------ | ---------------------------------------------------------------- |
| Console/Desktop Apps     | ASP.NET Apps                                                     |
| One file per application | Can exist at application and folder levels                       |
| Stores app settings      | Stores web settings, authentication, session, connection strings |

---

# Why Configuration Files?

* Easy maintenance
* No recompilation for configuration changes
* Better security
* Centralized settings

---

# Company Example

```text
Web.config

│

├── Connection String

├── Authentication

├── Session Timeout

├── Custom Errors

└── App Settings
```

Almost every ASP.NET Web Forms project contains a `Web.config` file.

---

# Interview Questions

### Q1. What is a Namespace?

A logical grouping of related types used to organize code and avoid naming conflicts.

---

### Q2. Why do we use namespaces?

To organize code and prevent name collisions.

---

### Q3. What is Garbage Collection?

Automatic memory management performed by the CLR.

---

### Q4. Who performs Garbage Collection?

The CLR.

---

### Q5. Where are objects stored?

In the **Managed Heap**.

---

### Q6. Does setting an object to `null` immediately destroy it?

No.

It only makes the object eligible for garbage collection.

---

### Q7. What are the three generations of the Garbage Collector?

* Generation 0
* Generation 1
* Generation 2

---

### Q8. What is the difference between `Dispose()` and Garbage Collection?

Garbage Collection frees managed memory automatically.

`Dispose()` releases unmanaged resources manually.

---

### Q9. Which applications use App.config?

Console, Windows Forms, and WPF applications.

---

### Q10. Which applications use Web.config?

ASP.NET Web Forms and ASP.NET MVC applications.

---

### Q11. Which namespace is used to read configuration values?

`System.Configuration`

---

# Flashcards

**Q:** What is a namespace?
**A:** A logical grouping of related types.

**Q:** Which namespace contains `List<T>`?
**A:** `System.Collections.Generic`.

**Q:** Who performs Garbage Collection?
**A:** CLR.

**Q:** Where are objects stored?
**A:** Managed Heap.

**Q:** How many GC generations are there?
**A:** Three (0, 1, and 2).

**Q:** Does `null` destroy an object?
**A:** No.

**Q:** Which file is used by Console applications?
**A:** App.config.

**Q:** Which file is used by ASP.NET Web Forms?
**A:** Web.config.

**Q:** Which namespace reads configuration values?
**A:** `System.Configuration`.

---

# Mini Practice

1. Define a namespace.
2. Why are namespaces important?
3. What is Garbage Collection?
4. Who performs Garbage Collection?
5. What is the Managed Heap?
6. Differentiate between Stack and Heap.
7. What are the three generations of the Garbage Collector?
8. Explain the difference between Garbage Collection and `Dispose()`.
9. What is App.config?
10. What is Web.config?
11. How do you read an AppSetting in C#?
12. Why should connection strings be stored in configuration files?

---

# Quick Revision

## Namespace

* Organizes code logically.
* Prevents naming conflicts.
* Imported using the `using` keyword.

## Garbage Collection

* Automatic memory management.
* Performed by the CLR.
* Objects are stored in the Managed Heap.
* Generations: 0 → 1 → 2.
* `Dispose()` is used for unmanaged resources.

## App.config

* Used by Console, Windows Forms, and WPF applications.
* Stores application settings and connection strings.

## Web.config

* Used by ASP.NET Web Forms and MVC applications.
* Stores connection strings, authentication, session settings, custom errors, and application settings.
