# Phase 3 – ASP.NET Web Forms (Part 1B)

## Topics Covered

1. Project Structure
2. Code-Behind
3. Page Life Cycle
4. Web Forms vs MVC
5. Interview Questions
6. Flashcards
7. Mini Practice

---

# 1. ASP.NET Web Forms Project Structure

## Definition

An **ASP.NET Web Forms Project** consists of multiple files and folders that work together to build and run a web application.

Each file has a specific responsibility.

---

# Typical Project Structure

```text
MyWebsite

│

├── App_Code

├── App_Data

├── App_Themes

├── Bin

├── Images

├── Scripts

├── Styles

├── Web.config

├── Default.aspx

├── Default.aspx.cs

├── Default.aspx.designer.cs

└── Global.asax
```

---

# Important Folders

## 1. App_Code

Stores common C# classes.

Example:

```text
Employee.cs

Student.cs

Utility.cs
```

These classes are shared throughout the application.

---

## 2. App_Data

Stores local databases.

Example:

```text
StudentDB.mdf
```

Normally, enterprise applications use SQL Server instead.

---

## 3. Bin

Contains compiled DLL files.

Example:

```text
BusinessLayer.dll

DataAccess.dll

Newtonsoft.Json.dll
```

---

## 4. Scripts

Stores JavaScript files.

Example:

```text
jquery.js

site.js
```

---

## 5. Styles

Stores CSS files.

Example:

```text
Site.css
```

---

## 6. Images

Stores images used by the website.

---

## 7. Web.config

Stores:

* Connection Strings
* Authentication
* Session
* AppSettings
* Custom Errors

---

## 8. Global.asax

Application-level events.

Examples:

```text
Application_Start

Session_Start

Application_End
```

---

# Company Structure

Enterprise projects are usually divided into layers.

```text
Presentation Layer

↓

Business Layer

↓

Data Access Layer

↓

SQL Server
```

This is called **Layered Architecture**.

---

# 2. Code-Behind

## Definition

The **Code-Behind** file contains the server-side C# logic for a Web Forms page.

Extension:

```text
.aspx.cs
```

---

# Example

## Login.aspx

```aspx
<asp:Button
ID="btnLogin"
runat="server"
Text="Login"
OnClick="btnLogin_Click"/>
```

---

## Login.aspx.cs

```csharp
protected void btnLogin_Click(object sender, EventArgs e)
{
    Response.Write("Welcome");
}
```

---

# Why Code-Behind?

Without Code-Behind

```text
HTML + C# Mixed Together
```

Very difficult to maintain.

With Code-Behind

```text
UI

↓

.aspx

Business Logic

↓

.aspx.cs
```

Cleaner and easier to manage.

---

# 3. ASP.NET Page Life Cycle

## Definition

The **Page Life Cycle** is the sequence of events that occur from the moment an ASP.NET page receives a request until it sends a response.

Every `.aspx` page follows this sequence.

---

# Complete Life Cycle

```text
Browser Request

↓

Page Request

↓

Start

↓

Initialization (Init)

↓

Load

↓

PostBack Events

↓

PreRender

↓

Render

↓

Unload
```

---

# Important Events

## Page_Init

Runs first.

Used for:

* Initialize controls
* Dynamic controls

```csharp
protected void Page_Init(object sender, EventArgs e)
{
}
```

---

## Page_Load

Runs every time the page loads.

Most commonly used event.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
}
```

---

# IsPostBack

Very important.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if(!IsPostBack)
    {
        // First page load only
    }
}
```

Without this condition, data may be loaded repeatedly on every postback.

---

## Button Click

```csharp
protected void btnSave_Click(object sender, EventArgs e)
{
}
```

Runs after `Page_Load`.

---

## PreRender

Last chance to modify controls before HTML is generated.

---

## Render

ASP.NET converts server controls into HTML.

Example:

```aspx
<asp:Button ... />
```

becomes

```html
<input type="submit" value="Save">
```

---

## Unload

Runs after the response is sent.

Used for cleanup.

---

# Life Cycle Diagram

```text
Request

↓

Init

↓

Load

↓

Button Click

↓

PreRender

↓

Render

↓

Unload
```

---

# Company Example

Suppose a login page.

```text
Open Login.aspx

↓

Page_Load

↓

User Clicks Login

↓

Button_Click

↓

Validate User

↓

Redirect Dashboard
```

This happens every day in Web Forms projects.

---

# 4. Web Forms vs MVC

| Web Forms              | MVC                   |
| ---------------------- | --------------------- |
| Event Driven           | Request Driven        |
| Uses Server Controls   | Uses HTML Helpers     |
| Uses ViewState         | No ViewState          |
| Easier for Beginners   | More Flexible         |
| Rapid Development      | Better Testability    |
| Drag & Drop Support    | Manual UI Development |
| Code-Behind            | Controller            |
| Mostly Legacy Projects | Modern Applications   |

---

# Architecture Comparison

## Web Forms

```text
Browser

↓

.aspx

↓

Code-Behind

↓

Database
```

---

## MVC

```text
Browser

↓

Controller

↓

Model

↓

View
```

---

# Which One Will You Use?

Your company uses:

✅ ASP.NET Web Forms

NOT

❌ ASP.NET Core MVC

So your focus should be:

* Page Life Cycle
* ViewState
* Server Controls
* Events
* GridView
* ADO.NET

---

# Interview Questions

### Q1. What is Code-Behind?

The `.aspx.cs` file that contains the server-side C# logic for an ASP.NET Web Forms page.

---

### Q2. Which event runs first?

`Page_Init`

---

### Q3. Which event is used most frequently?

`Page_Load`

---

### Q4. Why do we use `IsPostBack`?

To execute code only during the first page load and avoid reloading data on every postback.

---

### Q5. Which event runs after `Page_Load` when a button is clicked?

`Button_Click`

---

### Q6. Which event converts controls into HTML?

`Render`

---

### Q7. Which event is the last event?

`Unload`

---

### Q8. What is the difference between Web Forms and MVC?

Web Forms uses an event-driven model with server controls and code-behind, while MVC uses the Model-View-Controller pattern and provides greater flexibility and testability.

---

### Q9. Where are compiled DLL files stored?

In the `Bin` folder.

---

### Q10. Which file contains application-level events?

`Global.asax`

---

# Flashcards

**Q:** Which file stores the UI?
**A:** `.aspx`

**Q:** Which file stores C# logic?
**A:** `.aspx.cs`

**Q:** Which folder contains DLL files?
**A:** `Bin`

**Q:** Which file stores application configuration?
**A:** `Web.config`

**Q:** Which event runs first?
**A:** `Page_Init`

**Q:** Which event is used most often?
**A:** `Page_Load`

**Q:** Why use `IsPostBack`?
**A:** To prevent repeated execution during postbacks.

**Q:** Which event generates HTML?
**A:** `Render`

**Q:** Which event runs last?
**A:** `Unload`

---

# Mini Practice

1. Draw the ASP.NET Web Forms project structure.
2. What is the purpose of the `App_Code` folder?
3. What is stored in the `Bin` folder?
4. Explain Code-Behind.
5. What is the Page Life Cycle?
6. List the Page Life Cycle events in order.
7. Why is `IsPostBack` important?
8. Differentiate between Web Forms and MVC.
9. Which file contains application-level events?
10. Which event should you use to load data when the page first opens?

---

# Quick Revision

## Project Structure

* `App_Code` → Common classes
* `App_Data` → Local database files
* `Bin` → Compiled DLLs
* `Scripts` → JavaScript
* `Styles` → CSS
* `Images` → Images
* `Web.config` → Configuration
* `Global.asax` → Application events

---

## Code-Behind

* Extension: `.aspx.cs`
* Contains server-side C# code.
* Separates UI from business logic.

---

## Page Life Cycle

1. Init
2. Load
3. PostBack Events (e.g., `Button_Click`)
4. PreRender
5. Render
6. Unload

Remember to use `if (!IsPostBack)` when loading data that should only appear on the first page request.

---

## Web Forms vs MVC

* **Web Forms** → Event-driven, server controls, ViewState, code-behind.
* **MVC** → Request-driven, controller-based, no ViewState, more suitable for modern applications.

---

# Company Notes (Legacy ASP.NET Web Forms)

For your company's projects, you should be especially comfortable with:

* Reading and modifying `.aspx` and `.aspx.cs` files.
* Understanding the Page Life Cycle, especially `Page_Load` and `IsPostBack`.
* Knowing where configuration (`Web.config`) and libraries (`Bin`) are located.
* Debugging issues by following the request from the browser → page → code-behind → business layer → database.
* Recognizing that most UI actions (buttons, dropdowns, GridView operations) are implemented through server-side events.
