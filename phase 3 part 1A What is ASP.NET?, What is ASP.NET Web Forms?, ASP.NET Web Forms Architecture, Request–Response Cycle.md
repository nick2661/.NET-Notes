# Phase 3 – ASP.NET Web Forms (Part 1A)

## Topics Covered

1. What is ASP.NET?
2. What is ASP.NET Web Forms?
3. ASP.NET Web Forms Architecture
4. Request–Response Cycle

---

# 1. What is ASP.NET?

## Definition

**ASP.NET** is a web application framework developed by Microsoft that is used to build **dynamic websites, web applications, web services, and APIs** using the **.NET Framework**.

It provides everything required to create web applications, including:

* Server-side programming
* State management
* Authentication
* Security
* Data access
* Configuration
* Session management

---

## Where Does ASP.NET Fit?

```text
.NET Framework
│
├── Console Applications
├── Windows Forms
├── WPF
├── WCF
└── ASP.NET
      │
      ├── Web Forms
      ├── MVC
      └── Web API
```

ASP.NET is **one technology inside the .NET Framework**.

---

## Why Use ASP.NET?

Without ASP.NET, developers would need to manually write code for:

* Processing browser requests
* Managing sessions
* Authentication
* Routing
* Security
* Configuration

ASP.NET provides these features out of the box.

---

## Features

* Event-driven programming
* Server-side execution
* Built-in security
* State management
* Rich server controls
* Easy database connectivity
* IIS integration

---

## Company Example

In a legacy enterprise application:

```text
Employee Opens Browser

↓

Login.aspx

↓

ASP.NET

↓

Business Layer

↓

SQL Server

↓

Response Sent Back
```

ASP.NET coordinates communication between the browser, business logic, and database.

---

# 2. What is ASP.NET Web Forms?

## Definition

**ASP.NET Web Forms** is a server-side web development framework in ASP.NET that allows developers to build web applications using **.aspx pages**, **server controls**, and an **event-driven programming model**.

> **Interview Definition**
>
> ASP.NET Web Forms is a server-side framework that uses `.aspx` pages, server controls, and code-behind files to create dynamic web applications.

---

## Main Components

* `.aspx` page (User Interface)
* `.aspx.cs` file (Code-Behind)
* Server Controls
* ViewState
* Events

---

## Real-Life Analogy

Think of a restaurant.

```text
Customer

↓

Waiter

↓

Kitchen

↓

Food

↓

Customer
```

Here:

* Customer = Browser
* Waiter = ASP.NET
* Kitchen = C# Code
* Food = HTML Response

The browser never enters the kitchen. It only receives the final result.

---

## Code Example

### Login.aspx

```aspx
<asp:TextBox
    ID="txtName"
    runat="server" />

<asp:Button
    ID="btnLogin"
    runat="server"
    Text="Login"
    OnClick="btnLogin_Click" />

<asp:Label
    ID="lblMessage"
    runat="server" />
```

---

### Login.aspx.cs

```csharp
protected void btnLogin_Click(object sender, EventArgs e)
{
    lblMessage.Text = "Welcome " + txtName.Text;
}
```

---

### Browser Output

```text
Welcome Nick
```

---

# Web Forms File Structure

Each page normally has:

```text
Login.aspx

Login.aspx.cs

Login.aspx.designer.cs
```

| File                   | Purpose                             |
| ---------------------- | ----------------------------------- |
| Login.aspx             | UI                                  |
| Login.aspx.cs          | Business Logic                      |
| Login.aspx.designer.cs | Auto-generated control declarations |

---

# 3. ASP.NET Web Forms Architecture

## Architecture Diagram

```text
Browser

↓

IIS (Web Server)

↓

ASP.NET Runtime

↓

Page (.aspx)

↓

Code-Behind (.aspx.cs)

↓

Business Layer (BLL)

↓

Data Access Layer (DAL)

↓

SQL Server
```

---

## Step-by-Step Flow

### Step 1

User enters:

```text
http://localhost/Login.aspx
```

---

### Step 2

Browser sends an HTTP request.

---

### Step 3

IIS receives the request.

---

### Step 4

ASP.NET Runtime processes it.

---

### Step 5

The `.aspx` page is loaded.

---

### Step 6

The Code-Behind executes.

---

### Step 7

Business Layer performs business logic.

---

### Step 8

Data Access Layer connects to SQL Server.

---

### Step 9

SQL Server returns data.

---

### Step 10

ASP.NET converts server controls into HTML.

---

### Step 11

HTML is returned to the browser.

---

# Important Point

The browser **never executes C# code**.

The browser receives only:

* HTML
* CSS
* JavaScript

All C# executes on the server.

---

# 4. Request–Response Cycle

## Definition

The Request–Response Cycle is the process by which a browser sends a request to the server and receives a response.

---

## Complete Flow

```text
Browser

↓

HTTP Request

↓

IIS

↓

ASP.NET Runtime

↓

Page Life Cycle

↓

Code-Behind

↓

Business Layer

↓

Database

↓

Business Layer

↓

ASP.NET Runtime

↓

HTML Response

↓

Browser
```

---

# Example

User clicks **Login**.

---

### Browser

```text
Username = Nick

Password = ****
```

---

### Request

Browser sends data to:

```text
Login.aspx
```

---

### Server

ASP.NET executes:

```csharp
protected void btnLogin_Click(...)
{
    // Validate user
}
```

---

### Database

Checks if the username and password are valid.

---

### Response

Server generates HTML.

Browser displays:

```text
Welcome Nick
```

---

# Why Is This Important?

Every ASP.NET Web Forms page follows this process.

Understanding it helps you debug issues such as:

* Button click not firing
* Session lost
* Page refresh
* Validation errors
* Database not updating

---

# Interview Questions

### Q1. What is ASP.NET?

ASP.NET is Microsoft's web application framework for building websites, web applications, web services, and APIs.

---

### Q2. What is ASP.NET Web Forms?

A server-side web framework that uses `.aspx` pages, server controls, and code-behind files.

---

### Q3. Does the browser execute C# code?

No.

The server executes C# code and sends HTML to the browser.

---

### Q4. What is Code-Behind?

The `.aspx.cs` file containing the server-side C# logic for a Web Forms page.

---

### Q5. Which web server hosts ASP.NET Web Forms applications?

**IIS (Internet Information Services).**

---

### Q6. What is the Request–Response Cycle?

The process in which the browser sends an HTTP request to the server, the server processes it, and returns an HTTP response.

---

### Q7. Which layer communicates with SQL Server?

The **Data Access Layer (DAL).**

---

### Q8. What does ASP.NET send back to the browser?

HTML (along with CSS and JavaScript references where applicable).

---

# Flashcards

**Q:** What is ASP.NET?
**A:** Microsoft's web application framework.

**Q:** What is Web Forms?
**A:** A server-side web framework using `.aspx` pages.

**Q:** Which file contains the UI?
**A:** `.aspx`

**Q:** Which file contains C# code?
**A:** `.aspx.cs`

**Q:** Which server hosts ASP.NET applications?
**A:** IIS.

**Q:** Does the browser execute C#?
**A:** No.

**Q:** What does the browser receive?
**A:** HTML.

---

# Mini Practice

1. Define ASP.NET.
2. What is ASP.NET Web Forms?
3. Name the three files associated with a Web Forms page.
4. Draw the ASP.NET Web Forms architecture.
5. Explain the Request–Response Cycle.
6. Which component executes C# code?
7. Which component communicates with SQL Server?
8. Why does the browser receive HTML instead of C# code?

---

# Company Notes (Legacy ASP.NET Web Forms)

* Most pages you'll work with are **`.aspx`** pages.
* Business logic is usually kept in the **code-behind (`.aspx.cs`)** or Business Layer.
* SQL Server access is commonly handled through a separate **Data Access Layer (DAL)**.
* When debugging, first determine where the issue occurs:

  * Browser/UI
  * ASP.NET page
  * Code-behind
  * Business Layer
  * Database

Understanding this request flow is essential for maintaining and debugging enterprise Web Forms applications.
