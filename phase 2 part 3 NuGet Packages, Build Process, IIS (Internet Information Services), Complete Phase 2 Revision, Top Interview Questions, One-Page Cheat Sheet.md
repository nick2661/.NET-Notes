## Phase 2 – .NET Fundamentals (Part 3)

### Topics Covered

1. NuGet Packages
2. Build Process
3. IIS (Internet Information Services)
4. Complete Phase 2 Revision
5. Top Interview Questions
6. One-Page Cheat Sheet

---

# 1. NuGet Packages

## Definition

**NuGet** is the official package manager for .NET.

It is used to **install, update, remove, and manage reusable libraries (packages)** in a .NET project.

### Interview Definition

NuGet is the package management system for .NET that allows developers to add and manage third-party and Microsoft libraries in a project.

---

## Why Do We Need NuGet?

Without NuGet:

* Search library on the internet
* Download ZIP
* Extract files
* Copy DLLs manually
* Add references manually
* Repeat for every project

With NuGet:

* Search package
* Click Install
* Visual Studio downloads everything automatically

---

## Real-Life Analogy

Think of NuGet as an **App Store for .NET libraries**.

Examples:

* Newtonsoft.Json
* Dapper
* log4net
* EntityFramework
* ClosedXML

You choose a package and Visual Studio installs it automatically.

---

## Where Is It in Visual Studio?

Right-click **Project → Manage NuGet Packages**.

Tabs:

* Browse
* Installed
* Updates

---

## Installing a Package

Example: **Newtonsoft.Json**

### Package Manager Console

```powershell
Install-Package Newtonsoft.Json
```

### What Happens?

NuGet:

* Downloads the package
* Downloads dependencies
* Adds DLL references
* Updates configuration files

---

## Using the Package

```csharp
using Newtonsoft.Json;

class Student
{
    public string Name { get; set; }
}

Student s = new Student { Name = "Nick" };

string json = JsonConvert.SerializeObject(s);

Console.WriteLine(json);
```

### Output

```text
{"Name":"Nick"}
```

---

## package.config (Legacy Projects)

ASP.NET Web Forms projects often contain:

```text
package.config
```

Example:

```xml
<packages>
  <package id="Newtonsoft.Json"
           version="13.0.3"
           targetFramework="net48" />
</packages>
```

This file records installed packages.

---

## Common Packages in Legacy Projects

| Package                 | Purpose            |
| ----------------------- | ------------------ |
| Newtonsoft.Json         | JSON serialization |
| log4net                 | Logging            |
| Dapper                  | Lightweight ORM    |
| Microsoft.AspNet.WebApi | Web API support    |
| AjaxControlToolkit      | Web Forms controls |

---

## Company Example

Typical Web Forms project:

```text
Web Project
│
├── Newtonsoft.Json
├── log4net
├── Dapper
└── AjaxControlToolkit
```

These packages are managed through NuGet.

---

## Advantages

* Fast installation
* Automatic dependency management
* Easy updates
* Consistent versions
* Reusable code

---

# 2. Build Process

## Definition

The **Build Process** converts your C# source code into a compiled **DLL or EXE**.

### Interview Definition

The build process is the sequence of steps that compiles source code, resolves references, generates assemblies, and produces the final executable output.

---

## Build Flow

```text
C# Files (.cs)
       │
       ▼
Compiler (csc.exe)
       │
       ▼
Intermediate Language (IL)
       │
       ▼
Assembly (DLL / EXE)
       │
       ▼
CLR Executes
```

---

## What Happens During Build?

### Step 1: Syntax Check

Compiler checks:

* Missing semicolons
* Wrong variable names
* Type mismatches
* Missing references

### Step 2: Compile

Source code is converted to **IL (Intermediate Language)**.

### Step 3: Generate Assembly

Visual Studio creates:

* `.dll`
* `.exe`

### Step 4: Copy Output

Files are placed in:

```text
bin\\Debug
```

or

```text
bin\\Release
```

---

## Build vs Rebuild vs Clean

### Build

* Compiles only changed files
* Faster

### Rebuild

* Deletes old output
* Compiles everything
* Slower

### Clean

* Deletes generated files
* Does not compile

---

## Comparison Table

| Option  | Deletes Output | Compiles           | Speed     |
| ------- | -------------- | ------------------ | --------- |
| Build   | No             | Changed files only | Fast      |
| Rebuild | Yes            | All files          | Slow      |
| Clean   | Yes            | No                 | Very Fast |

---

## Debug vs Release

### Debug

Used during development.

Characteristics:

* Debug symbols included
* Easier debugging
* Larger output
* Less optimization

### Release

Used for production.

Characteristics:

* Optimized code
* Smaller output
* Better performance
* Harder to debug

---

## Output Folders

### bin

Contains final DLL/EXE.

### obj

Contains temporary compilation files.

---

## Company Example

In Web Forms:

```text
MyWebApp
│
├── bin
│   ├── BusinessLayer.dll
│   ├── DataAccess.dll
│   └── MyWebApp.dll
│
└── obj
    └── Temporary build files
```

The `bin` folder is deployed to IIS.

---

# 3. IIS (Internet Information Services)

## Definition

**IIS** is Microsoft's web server used to host ASP.NET applications.

### Interview Definition

IIS is a web server developed by Microsoft that hosts and serves ASP.NET applications over HTTP/HTTPS.

---

## Why IIS?

A browser cannot directly execute an ASP.NET application.

IIS:

* Receives the request
* Starts the ASP.NET runtime
* Executes the application
* Sends HTML back to the browser

---

## Request Flow

```text
Browser
   │
HTTP Request
   ▼
IIS
   │
ASP.NET Runtime
   │
Web Forms Page (.aspx)
   │
C# Code Executes
   │
HTML Generated
   ▼
Browser
```

---

## IIS vs Visual Studio

| Visual Studio | IIS               |
| ------------- | ----------------- |
| Development   | Production        |
| IIS Express   | Full IIS          |
| Temporary     | Permanent hosting |
| Local testing | Real server       |

---

## Important IIS Terms

### Website

A hosted web application.

### Application Pool

A process that runs one or more web applications.

### Virtual Directory

A folder exposed through IIS.

### Physical Path

Actual folder on disk.

---

## Application Pool

### Definition

An **Application Pool** isolates web applications from each other.

### Why Important?

If one application crashes, other applications continue running.

### Diagram

```text
IIS
│
├── App Pool A
│      └── HR Application
│
└── App Pool B
       └── ERP Application
```

---

## Common Tasks

### Create Website

* Open IIS Manager
* Add Website
* Select folder
* Assign port
* Start website

### Browse Site

Example:

```text
http://localhost:8080
```

---

## Common IIS Errors

| Error | Meaning                  |
| ----- | ------------------------ |
| 404   | Page not found           |
| 403   | Access denied            |
| 500   | Internal server error    |
| 503   | Application pool stopped |

---

## Company Example

Typical deployment:

```text
Developer Machine
       │
Publish
       ▼
Server Folder
       │
       ▼
IIS Website
       │
       ▼
Users Access Application
```

This is exactly how many legacy ASP.NET Web Forms applications are deployed.

---

# Complete Phase 2 Revision

## .NET Framework

* Platform for building applications
* Main components: CLR + FCL

## CLR

* Executes applications
* Memory management
* Garbage collection
* Exception handling
* Security
* JIT compilation

## CTS

* Defines all .NET data types
* Value types and reference types

## CLS

* Defines common language rules
* Enables interoperability

## Assemblies

* Compiled output
* DLL = library
* EXE = executable

## Namespace

* Logical grouping of types
* Prevents naming conflicts

## Garbage Collection

* Automatic memory management
* Managed Heap
* Generations 0, 1, 2

## App.config

* Console/Desktop apps

## Web.config

* ASP.NET apps
* Connection strings
* Authentication
* Session settings

## NuGet

* Package manager for .NET

## Build Process

* Build
* Rebuild
* Clean
* Debug
* Release

## IIS

* Web server for ASP.NET
* Hosts Web Forms applications

---

# Top Interview Questions

### Q1. What are the two main components of the .NET Framework?

**Answer:** CLR and FCL.

### Q2. What is the role of CLR?

**Answer:** It executes .NET applications and provides runtime services.

### Q3. What is the difference between CTS and CLS?

**Answer:** CTS defines types; CLS defines common language rules.

### Q4. What is an Assembly?

**Answer:** The compiled output of a .NET project containing IL, metadata, and resources.

### Q5. Difference between DLL and EXE?

**Answer:** DLL is a reusable library; EXE is an executable application.

### Q6. What is the Managed Heap?

**Answer:** The memory area where reference-type objects are stored.

### Q7. What is the purpose of Dispose()?

**Answer:** To release unmanaged resources promptly.

### Q8. Difference between App.config and Web.config?

**Answer:** App.config is for desktop/console apps; Web.config is for ASP.NET applications.

### Q9. What is NuGet?

**Answer:** The official package manager for .NET.

### Q10. Difference between Build, Rebuild, and Clean?

**Answer:** Build compiles changed files, Rebuild compiles everything after deleting output, and Clean only deletes generated files.

### Q11. What is IIS?

**Answer:** Microsoft's web server used to host ASP.NET applications.

### Q12. What is an Application Pool?

**Answer:** A process isolation boundary for web applications.

---

# One-Page Cheat Sheet

## CLR

* Execution engine
* GC
* Exceptions
* Security
* JIT

## CTS

* Defines all data types

## CLS

* Defines common language rules

## Assembly

* DLL = library
* EXE = executable

## Namespace

* Organizes code
* Avoids naming conflicts

## Garbage Collection

* Automatic
* Managed Heap
* Gen 0 → Gen 1 → Gen 2

## Dispose()

* Manual cleanup of unmanaged resources

## App.config

* Console/Desktop apps

## Web.config

* ASP.NET apps

## NuGet

* Install/Update/Remove packages

## Build

* Changed files only

## Rebuild

* Delete + compile all

## Clean

* Delete generated files

## Debug

* Development

## Release

* Production

## IIS

* Hosts ASP.NET applications

## Application Pool

* Isolates web applications

## Most Important for Your Company

* Web.config
* Connection Strings
* Build/Rebuild/Clean
* Debug vs Release
* IIS Website
* Application Pool
* DLL references
* Garbage Collection
* Exception Handling
* Namespaces
