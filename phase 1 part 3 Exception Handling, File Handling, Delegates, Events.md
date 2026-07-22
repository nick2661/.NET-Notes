# Phase 1 – C# Revision (Part 3)

## Topics Covered

1. Exception Handling
2. File Handling
3. Delegates
4. Events

---

# 1. Exception Handling

## Definition

**Exception Handling** is a mechanism used to handle runtime errors so that the application does not terminate unexpectedly.

> **Interview Definition:**
>
> Exception handling is the process of detecting, handling, and recovering from runtime errors using `try`, `catch`, `finally`, and `throw`.

---

# Why Do We Need Exception Handling?

Without exception handling:

```text
Application Starts
       │
Runtime Error
       │
Application Crashes
```

With exception handling:

```text
Application Starts
       │
Runtime Error
       │
catch Block Handles Error
       │
Application Continues
```

---

# Common Exceptions

| Exception                | Cause                |
| ------------------------ | -------------------- |
| DivideByZeroException    | Dividing by zero     |
| NullReferenceException   | Using a null object  |
| FormatException          | Invalid input format |
| IndexOutOfRangeException | Invalid array index  |
| FileNotFoundException    | File does not exist  |

---

# try-catch Example

```csharp
using System;

class Program
{
    static void Main()
    {
        try
        {
            int result = 10 / 0;
            Console.WriteLine(result);
        }
        catch (DivideByZeroException)
        {
            Console.WriteLine("Cannot divide by zero.");
        }
    }
}
```

### Output

```text
Cannot divide by zero.
```

---

# finally Block

The `finally` block executes **whether an exception occurs or not**.

```csharp
try
{
    Console.WriteLine("Inside Try");
}
catch
{
    Console.WriteLine("Inside Catch");
}
finally
{
    Console.WriteLine("Inside Finally");
}
```

### Output

```text
Inside Try
Inside Finally
```

---

# throw Keyword

Used to manually raise an exception.

```csharp
if(age < 18)
{
    throw new Exception("Age must be 18 or above.");
}
```

---

# Exception Handling Flow

```text
try
 │
 ├── No Exception → finally
 │
 └── Exception
        │
        ▼
      catch
        │
        ▼
     finally
```

---

# Best Practices

* Catch specific exceptions.
* Avoid empty catch blocks.
* Use `finally` to release resources.
* Log exceptions in enterprise applications.

---

# 2. File Handling

## Definition

File Handling is used to **create, read, write, append, copy, move, and delete files**.

Namespace:

```csharp
using System.IO;
```

---

# File Class

Common methods:

| Method          | Purpose           |
| --------------- | ----------------- |
| Create()        | Create a file     |
| Exists()        | Check file        |
| Copy()          | Copy file         |
| Move()          | Move file         |
| Delete()        | Delete file       |
| ReadAllText()   | Read entire file  |
| WriteAllText()  | Write entire file |
| AppendAllText() | Append data       |

---

# Write to File

```csharp
using System.IO;

File.WriteAllText("Student.txt", "Hello Nick");
```

---

# Read File

```csharp
string text = File.ReadAllText("Student.txt");

Console.WriteLine(text);
```

### Output

```text
Hello Nick
```

---

# Append Data

```csharp
File.AppendAllText("Student.txt",
Environment.NewLine + "Welcome");
```

---

# File Handling Flow

```text
Application

      │

      ▼

System.IO

      │

      ▼

File

      │

      ▼

Hard Disk
```

---

# Real Company Usage

* Export reports
* Generate log files
* Upload/download documents
* Store configuration backups

---

# 3. Delegates

## Definition

A **Delegate** is a type-safe function pointer.

It stores the reference of one or more methods having the same signature.

> **Interview Definition:**
>
> A delegate is a type that holds references to methods and allows methods to be passed as parameters.

---

# Why Delegates?

Without delegates:

```text
Method A calls Method B directly.
```

With delegates:

```text
Delegate

↓

Calls Method A

↓

Calls Method B
```

This provides flexibility and loose coupling.

---

# Syntax

```csharp
public delegate void DisplayDelegate();
```

---

# Example

```csharp
using System;

public delegate void DisplayDelegate();

class Program
{
    static void Show()
    {
        Console.WriteLine("Hello Delegate");
    }

    static void Main()
    {
        DisplayDelegate d = Show;

        d();
    }
}
```

### Output

```text
Hello Delegate
```

---

# Multicast Delegate

A delegate can call multiple methods.

```csharp
delegateObj += Method1;
delegateObj += Method2;
```

Output:

```text
Method1
Method2
```

---

# Advantages

* Loose coupling
* Callback methods
* Event handling
* Flexible code

---

# 4. Events

## Definition

An **Event** is a mechanism through which one object notifies other objects when something happens.

Events are built on top of delegates.

---

# Real-Life Analogy

```text
Door Bell

↓

Visitor Presses Bell

↓

Bell Rings

↓

Owner Opens Door
```

Event = Bell Ring

---

# Event Flow

```text
Button Click

↓

Event Raised

↓

Event Handler Executes
```

---

# Example

```csharp
using System;

public delegate void Notify();

class Button
{
    public event Notify Click;

    public void Press()
    {
        Click?.Invoke();
    }
}

class Program
{
    static void Message()
    {
        Console.WriteLine("Button Clicked");
    }

    static void Main()
    {
        Button b = new Button();

        b.Click += Message;

        b.Press();
    }
}
```

### Output

```text
Button Clicked
```

---

# Delegates vs Events

| Delegate                | Event                  |
| ----------------------- | ---------------------- |
| Stores method reference | Notification mechanism |
| Can be called directly  | Raised by publisher    |
| Can exist independently | Built using delegates  |

---

# Company Usage

Events are heavily used in:

* ASP.NET Button Click
* GridView Events
* DropDownList SelectedIndexChanged
* Windows Forms
* WPF

---

# Interview Questions

## Exception Handling

### Q1. What is Exception Handling?

Handling runtime errors without crashing the application.

---

### Q2. Which keywords are used?

* try
* catch
* finally
* throw

---

### Q3. What is the purpose of `finally`?

It always executes, whether an exception occurs or not.

---

## File Handling

### Q4. Which namespace is used?

`System.IO`

---

### Q5. Which method writes a complete file?

`File.WriteAllText()`

---

### Q6. Which method reads a complete file?

`File.ReadAllText()`

---

## Delegates

### Q7. What is a Delegate?

A type-safe function pointer.

---

### Q8. Why are delegates used?

To hold references to methods and support callback/event programming.

---

## Events

### Q9. What is an Event?

A notification mechanism built using delegates.

---

### Q10. Are events based on delegates?

Yes.

---

# Flashcards

**Q:** Which keyword throws an exception?
**A:** `throw`

**Q:** Which block always executes?
**A:** `finally`

**Q:** Which namespace is used for file handling?
**A:** `System.IO`

**Q:** What is a delegate?
**A:** A type-safe function pointer.

**Q:** What is an event?
**A:** A notification mechanism based on delegates.

**Q:** Which operator safely invokes an event?
**A:** `?.Invoke()`

---

# Mini Practice

1. What is exception handling?
2. Why do we use `finally`?
3. What is the purpose of `throw`?
4. Name five common exceptions.
5. Which namespace is used for file handling?
6. Name four methods of the `File` class.
7. Define a delegate.
8. What is a multicast delegate?
9. What is an event?
10. What is the relationship between delegates and events?

---

# Quick Revision

## Exception Handling

* `try` → Risky code
* `catch` → Handles exception
* `finally` → Always executes
* `throw` → Raises exception

---

## File Handling

* Namespace → `System.IO`
* Write → `WriteAllText()`
* Read → `ReadAllText()`
* Append → `AppendAllText()`

---

## Delegates

* Type-safe function pointer
* Holds method references
* Supports callbacks
* Used by events

---

## Events

* Built on delegates
* Used for notifications
* Common in ASP.NET Web Forms (`Button_Click`, `Page_Load`, etc.)
