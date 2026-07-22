# Phase 2 – .NET Fundamentals (Part 1)

## Topics Covered

1. What is .NET Framework?
2. CLR (Common Language Runtime)
3. CTS (Common Type System)
4. CLS (Common Language Specification)
5. Assemblies (DLL & EXE)

---

# 1. What is .NET Framework?

## Definition

The **.NET Framework** is a software development framework developed by Microsoft that provides a platform to build, run, and manage applications.

It consists mainly of:

* CLR (Common Language Runtime)
* FCL (Framework Class Library)

---

## Why Do We Need .NET Framework?

Before .NET, developers had to manage many low-level tasks manually, such as:

* Memory Management
* Exception Handling
* Security
* Thread Management

The .NET Framework provides these services automatically.

---

## Architecture

```text
            .NET Framework
                 │
      ┌──────────┴──────────┐
      │                     │
     CLR                   FCL
      │                     │
Runs Application      Ready-made Classes
```

---

## Applications Built Using .NET Framework

* Console Applications
* Windows Forms Applications
* WPF Applications
* ASP.NET Web Forms
* ASP.NET MVC
* WCF Services
* Windows Services

---

## Advantages

* Easy development
* Secure
* Automatic memory management
* Rich class library
* Language interoperability

---

## Code Example

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello .NET Framework");
    }
}
```

### Output

```text
Hello .NET Framework
```

---

## Company Example

In your company:

```text
ASP.NET Web Forms

↓

.NET Framework

↓

CLR Executes Code
```

Without the .NET Framework, the application cannot run.

---

# 2. CLR (Common Language Runtime)

## Definition

The **CLR** is the execution engine of the .NET Framework.

It is responsible for executing .NET applications and providing runtime services.

---

## Responsibilities of CLR

* Memory Management
* Garbage Collection
* Exception Handling
* Security
* Thread Management
* JIT Compilation

---

## CLR Execution Flow

```text
C# Code

↓

C# Compiler

↓

MSIL (IL)

↓

CLR

↓

JIT Compiler

↓

Machine Code

↓

CPU Executes
```

---

## Components

### C# Compiler

Converts C# code into **MSIL (Intermediate Language)**.

### MSIL (Microsoft Intermediate Language)

CPU-independent intermediate code.

### JIT Compiler

Converts IL into machine code before execution.

---

## Code Example

```csharp
Console.WriteLine("CLR Executes This");
```

Although you write C#, the CLR executes the compiled machine code produced by the JIT compiler.

---

## Advantages

* Platform independence at the IL level
* Automatic memory management
* Secure execution
* Better performance using JIT

---

# 3. CTS (Common Type System)

## Definition

The **Common Type System (CTS)** defines how data types are declared, used, and managed in the .NET Framework.

It ensures that all .NET languages understand the same data types.

---

## Why CTS?

Example:

```text
C#

↓

int

↓

CTS

↓

System.Int32

↓

VB.NET

↓

Integer
```

Even though the syntax differs, both languages represent the same underlying type.

---

## Types Defined by CTS

### Value Types

Stored directly.

Examples:

```csharp
int
char
bool
double
decimal
```

---

### Reference Types

Store a reference to an object.

Examples:

```csharp
string
object
class
interface
delegate
array
```

---

## Diagram

```text
CTS

│

├── Value Types

│      ├── int

│      ├── bool

│      └── char

│

└── Reference Types

       ├── string

       ├── class

       └── object
```

---

## Advantages

* Common data types
* Language interoperability
* Consistent behavior across .NET languages

---

# 4. CLS (Common Language Specification)

## Definition

The **Common Language Specification (CLS)** is a set of rules that .NET languages should follow so that code written in one .NET language can be used by another.

---

## Why CLS?

Suppose:

Developer A writes a library in C#.

Developer B wants to use it in VB.NET.

CLS ensures both languages can communicate.

---

## Diagram

```text
C#

↓

CLS Rules

↓

VB.NET

↓

F#

↓

Same .NET Library
```

---

## CTS vs CLS

| CTS                   | CLS                         |
| --------------------- | --------------------------- |
| Defines data types    | Defines language rules      |
| Used by CLR           | Used by language developers |
| Covers all .NET types | Covers only common features |

---

## Advantages

* Language interoperability
* Standard programming rules
* Easier code sharing

---

# 5. Assemblies (DLL & EXE)

## Definition

An **Assembly** is the compiled output of a .NET application.

It is the basic unit of deployment, versioning, and reuse.

Assemblies contain:

* MSIL (Intermediate Language)
* Metadata
* Manifest
* Resources

---

## Types of Assemblies

### DLL (Dynamic Link Library)

* Cannot run independently
* Reusable
* Used by other applications

Examples:

```text
BusinessLayer.dll

DataAccess.dll

Utility.dll
```

---

### EXE (Executable)

* Can run directly
* Contains the application's entry point (`Main()`)

Example:

```text
MyApplication.exe
```

---

## DLL vs EXE

| DLL                    | EXE                    |
| ---------------------- | ---------------------- |
| Library                | Executable program     |
| Cannot run alone       | Runs directly          |
| Reusable               | Starts the application |
| Referenced by projects | Entry point present    |

---

## Company Example

A typical ASP.NET Web Forms project:

```text
Presentation Layer

↓

BusinessLayer.dll

↓

DataAccess.dll

↓

SQL Server
```

The Web Forms project references DLLs for business logic and database access.

---

# Interview Questions

### Q1. What is the .NET Framework?

A software development framework developed by Microsoft used to build and run applications.

---

### Q2. What are the two main components of the .NET Framework?

* CLR
* FCL

---

### Q3. What is CLR?

The execution engine of the .NET Framework.

---

### Q4. What are the responsibilities of CLR?

* Memory Management
* Garbage Collection
* Exception Handling
* Security
* Thread Management
* JIT Compilation

---

### Q5. What is CTS?

CTS defines all data types used by .NET languages.

---

### Q6. What is CLS?

CLS is a set of common rules that enables interoperability between .NET languages.

---

### Q7. Difference between CTS and CLS?

CTS defines **types**.

CLS defines **rules**.

---

### Q8. What is an Assembly?

The compiled output of a .NET project containing IL, metadata, and resources.

---

### Q9. Difference between DLL and EXE?

DLL is a reusable library.

EXE is an executable application.

---

# Flashcards

**Q:** What are the two main components of the .NET Framework?
**A:** CLR and FCL.

**Q:** What is the execution engine of .NET?
**A:** CLR.

**Q:** What does CTS define?
**A:** Common data types.

**Q:** What does CLS define?
**A:** Common language rules.

**Q:** What is IL (MSIL)?
**A:** CPU-independent intermediate code.

**Q:** Which compiler converts IL into machine code?
**A:** JIT Compiler.

**Q:** Can a DLL run independently?
**A:** No.

**Q:** Which file contains the application's entry point?
**A:** EXE.

---

# Mini Practice

1. Define the .NET Framework.
2. Name the two main components of the .NET Framework.
3. Explain the role of the CLR.
4. What is MSIL (IL)?
5. What is the purpose of the JIT compiler?
6. Differentiate between CTS and CLS.
7. Name four value types and four reference types.
8. What is an Assembly?
9. Differentiate between a DLL and an EXE.
10. Draw the execution flow from C# code to machine code.

---

# Quick Revision

## .NET Framework

* Platform for building and running applications.
* Main components: CLR + FCL.

## CLR

* Executes applications.
* Handles memory, exceptions, security, garbage collection, threads, and JIT.

## CTS

* Defines all .NET data types.
* Includes value types and reference types.

## CLS

* Defines common language rules.
* Enables interoperability among .NET languages.

## Assemblies

* Compiled output of a .NET project.
* Types: DLL (library) and EXE (executable).
