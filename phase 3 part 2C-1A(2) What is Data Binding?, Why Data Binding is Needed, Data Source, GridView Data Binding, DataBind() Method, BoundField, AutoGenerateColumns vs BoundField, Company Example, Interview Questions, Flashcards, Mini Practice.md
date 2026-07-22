# Phase 3 – ASP.NET Web Forms (Part 2C-1A(2))

# Data Binding & BoundField

---

# Topics Covered

1. What is Data Binding?
2. Why Data Binding is Needed
3. Data Source
4. GridView Data Binding
5. DataBind() Method
6. BoundField
7. AutoGenerateColumns vs BoundField
8. Company Example
9. Interview Questions
10. Flashcards
11. Mini Practice

---

# 1. What is Data Binding?

## Definition

**Data Binding** is the process of connecting a control (such as a GridView) with a data source (such as SQL Server, a DataTable, or a DataSet) so that the data can be displayed automatically.

In simple words:

> **Data Binding = Connecting data to a control.**

---

# Real-Life Analogy

Imagine a TV.

```text
Cable Connection

↓

TV

↓

Channels Displayed
```

Without the cable connection, the TV cannot display channels.

Similarly,

```text
SQL Server

↓

Data Binding

↓

GridView

↓

Records Displayed
```

Without data binding, a GridView remains empty.

---

# Why Do We Need Data Binding?

Suppose your Employee table contains:

```text
EmployeeID   Name     Department

101          Nick     IT

102          John     HR

103          Alex     Sales
```

Without data binding, you would have to create every row manually.

With data binding, ASP.NET automatically displays all records.

---

# Data Binding Architecture

```text
SQL Server

↓

ADO.NET

↓

DataTable

↓

GridView.DataSource

↓

DataBind()

↓

HTML Table

↓

Browser
```

---

# 2. Data Source

## Definition

A **Data Source** is the location from which data is retrieved.

Common data sources include:

* SQL Server
* Oracle
* MySQL
* DataTable
* DataSet
* List Collection

---

# Company Example

In most enterprise projects:

```text
SQL Server

↓

Stored Procedure

↓

ADO.NET

↓

DataTable

↓

GridView
```

Developers usually bind a **DataTable** to a GridView.

---

# 3. DataSource Property

## Definition

The `DataSource` property tells the GridView **which data to display**.

Syntax:

```csharp
gvEmployee.DataSource = dt;
```

Here:

* `gvEmployee` = GridView
* `dt` = DataTable

---

# 4. DataBind() Method

## Definition

`DataBind()` tells the GridView to display the data assigned to its `DataSource`.

Without calling `DataBind()`, the GridView will not show any records.

---

# Syntax

```csharp
gvEmployee.DataSource = dt;

gvEmployee.DataBind();
```

---

# Important Point

Both statements are required.

Wrong:

```csharp
gvEmployee.DataSource = dt;
```

Result:

```text
GridView is empty
```

Correct:

```csharp
gvEmployee.DataSource = dt;

gvEmployee.DataBind();
```

Result:

```text
All records are displayed.
```

---

# Complete Example

## ASPX Page

```aspx
<asp:GridView

ID="gvEmployee"

runat="server">

</asp:GridView>
```

---

## Code Behind

```csharp
DataTable dt = new DataTable();

dt.Columns.Add("ID");
dt.Columns.Add("Name");

dt.Rows.Add("101", "Nick");
dt.Rows.Add("102", "John");
dt.Rows.Add("103", "Alex");

gvEmployee.DataSource = dt;

gvEmployee.DataBind();
```

---

# Output

```text
--------------------------------

ID      Name

--------------------------------

101     Nick

102     John

103     Alex

--------------------------------
```

---

# How Data Binding Works

```text
Create DataTable

↓

Add Columns

↓

Add Rows

↓

Assign to DataSource

↓

Call DataBind()

↓

GridView Generates HTML

↓

Browser Displays Table
```

---

# 5. BoundField

## Definition

A **BoundField** displays the value of a specific database column in a GridView.

Instead of automatically generating columns, you create them manually.

---

# Why Use BoundField?

It gives complete control over:

* Column order
* Header text
* Visibility
* Formatting

---

# Syntax

```aspx
<asp:GridView

ID="gvEmployee"

runat="server"

AutoGenerateColumns="False">

<Columns>

<asp:BoundField

DataField="EmployeeID"

HeaderText="Employee ID" />

<asp:BoundField

DataField="Name"

HeaderText="Employee Name" />

</Columns>

</asp:GridView>
```

---

# Explanation

`DataField`

```text
EmployeeID
```

Specifies the column from the data source.

---

`HeaderText`

```text
Employee ID
```

Specifies the heading displayed in the GridView.

---

# Output

```text
------------------------------------

Employee ID

Employee Name

------------------------------------

101

Nick

102

John

------------------------------------
```

---

# AutoGenerateColumns vs BoundField

## AutoGenerateColumns = True

```text
Database

↓

GridView

↓

Columns Created Automatically
```

Advantages:

* Quick
* Easy

Disadvantages:

* Less control

---

## AutoGenerateColumns = False

```text
Database

↓

Developer Creates BoundFields

↓

GridView
```

Advantages:

* Full control
* Professional layout

Disadvantages:

* More code

---

# Which One Do Companies Use?

Small demo projects:

```text
AutoGenerateColumns = True
```

Enterprise projects:

```text
AutoGenerateColumns = False
```

because companies want:

* Better formatting
* Proper column names
* Hidden IDs
* Custom layouts

---

# Company Example

Employee Table

```text
EmployeeID

EmployeeName

Department

Salary
```

Database column:

```text
EmployeeName
```

Company wants to display:

```text
Employee Name
```

They use:

```aspx
HeaderText="Employee Name"
```

instead of showing the database column name directly.

---

# Interview Questions

### Q1. What is Data Binding?

The process of connecting a control with a data source so it can display data.

---

### Q2. Which property specifies the data source?

```csharp
DataSource
```

---

### Q3. Which method displays the data?

```csharp
DataBind()
```

---

### Q4. What happens if `DataBind()` is not called?

The GridView remains empty even if a DataSource is assigned.

---

### Q5. What is a BoundField?

A GridView column that displays the value of a specific data source column.

---

### Q6. Which property maps a BoundField to a database column?

```text
DataField
```

---

### Q7. Which property changes the displayed column heading?

```text
HeaderText
```

---

### Q8. Which approach is preferred in enterprise applications?

`AutoGenerateColumns="False"` with manually defined `BoundField` controls.

---

# Flashcards

**Q:** What is Data Binding?
**A:** Connecting a control with a data source.

**Q:** Which property assigns data?
**A:** `DataSource`.

**Q:** Which method displays the data?
**A:** `DataBind()`.

**Q:** Which GridView field displays a database column?
**A:** `BoundField`.

**Q:** Which property maps the database column?
**A:** `DataField`.

**Q:** Which property changes the heading?
**A:** `HeaderText`.

---

# Mini Practice

1. Define Data Binding.
2. What is the purpose of the `DataSource` property?
3. Why is `DataBind()` required?
4. Create a GridView that displays `EmployeeID` and `EmployeeName` using `BoundField`.
5. Explain the difference between `AutoGenerateColumns=True` and `False`.
6. Which approach is generally used in enterprise projects, and why?

---

# Quick Revision

## Data Binding

* Connects a control to a data source.
* Requires:

  * `DataSource`
  * `DataBind()`

---

## DataSource

* Specifies the data to display.

Example:

```csharp
gvEmployee.DataSource = dt;
```

---

## DataBind()

* Renders the assigned data.

Example:

```csharp
gvEmployee.DataBind();
```

---

## BoundField

* Displays a specific column.
* Important properties:

  * `DataField`
  * `HeaderText`

---

## Company Notes (Legacy ASP.NET Web Forms)

In almost every legacy Web Forms project:

* Data is retrieved from SQL Server using **ADO.NET**.
* It is stored in a **DataTable**.
* The `DataTable` is assigned to the GridView using the `DataSource` property.
* `DataBind()` is called to display the records.
* GridViews typically use `AutoGenerateColumns="False"` with `BoundField` controls to provide better formatting and maintain a professional user interface.

These concepts are the foundation for **GridView CRUD (Create, Read, Update, Delete)** operations, which you'll learn next.
