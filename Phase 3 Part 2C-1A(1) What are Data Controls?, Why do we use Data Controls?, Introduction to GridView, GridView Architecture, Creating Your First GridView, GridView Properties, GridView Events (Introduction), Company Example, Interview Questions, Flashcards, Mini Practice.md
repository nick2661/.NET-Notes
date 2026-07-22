# Phase 3 – ASP.NET Web Forms (Part 2C-1A(1))

# Introduction to Data Controls & GridView Basics

---

# Topics Covered

1. What are Data Controls?
2. Why do we use Data Controls?
3. Introduction to GridView
4. GridView Architecture
5. Creating Your First GridView
6. GridView Properties
7. GridView Events (Introduction)
8. Company Example
9. Interview Questions
10. Flashcards
11. Mini Practice

---

# 1. What are Data Controls?

## Definition

**Data Controls** are ASP.NET server controls used to display, edit, and manipulate data from a data source such as SQL Server.

Unlike simple controls (Label, TextBox, Button), Data Controls can display **multiple records** at once.

---

## Real Life Analogy

Imagine an Excel sheet.

```text
Employee ID | Name | Salary

101         | Nick | 30000

102         | John | 45000

103         | Alex | 50000
```

Instead of displaying one employee at a time, a Data Control displays an entire table.

---

## Common Data Controls

| Control     | Purpose                               |
| ----------- | ------------------------------------- |
| GridView    | Display data in a table               |
| Repeater    | Custom data display                   |
| DataList    | Repeated layout with more flexibility |
| DetailsView | Display one record                    |
| FormView    | Display one record with templates     |

In most legacy enterprise applications, **GridView** is the most commonly used control.

---

# Why Do We Need Data Controls?

Without Data Controls:

You would manually create HTML for every row.

```text
Employee 1

Employee 2

Employee 3

Employee 4

Employee 5
```

If there are 5,000 employees, this becomes impossible to maintain.

---

With GridView:

```text
GridView

↓

Automatically creates rows

↓

Displays database records

↓

Supports editing

↓

Supports deleting

↓

Supports paging

↓

Supports sorting
```

One control can display thousands of records.

---

# Company Example

Employee Management System

```text
EmployeeID

Employee Name

Department

Salary

Status
```

Instead of creating labels for every employee, developers bind the GridView directly to SQL Server.

---

# 2. Introduction to GridView

## Definition

**GridView** is an ASP.NET server control that displays data in a table format.

It can automatically generate rows and columns from a data source.

---

## Why is GridView Popular?

Because it provides built-in support for:

* Displaying records
* Editing
* Updating
* Deleting
* Paging
* Sorting
* Selecting rows

without manually writing HTML tables.

---

# GridView Structure

```text
GridView

---------------------------------

EmployeeID

Name

Department

Salary

---------------------------------

101

Nick

IT

30000

---------------------------------

102

John

HR

35000

---------------------------------

103

Alex

Sales

42000
```

Each row represents one record from the database.

---

# GridView Architecture

```text
SQL Server

↓

ADO.NET

↓

DataTable / DataSet

↓

GridView

↓

HTML Table

↓

Browser
```

Notice that the browser does **not** receive the GridView control.

ASP.NET converts it into a normal HTML table before sending it to the browser.

---

# GridView Syntax

```aspx
<asp:GridView
    ID="gvEmployees"
    runat="server">
</asp:GridView>
```

This creates an empty GridView.

---

# Sample Output

```text
-------------------------------------

EmployeeID

Name

Salary

-------------------------------------

101

Nick

30000

-------------------------------------

102

John

45000

-------------------------------------
```

---

# 3. GridView Properties

## 1. ID

Unique name of the control.

```aspx
ID="gvEmployees"
```

---

## 2. runat

Must always be

```aspx
runat="server"
```

Without it, ASP.NET cannot process the GridView.

---

## 3. AutoGenerateColumns

```aspx
AutoGenerateColumns="True"
```

ASP.NET automatically creates columns from the data source.

Example

Database

```text
EmployeeID

Name

Salary
```

GridView automatically creates

```text
EmployeeID

Name

Salary
```

No manual column creation required.

---

## AutoGenerateColumns="False"

Developer creates columns manually.

Example

```aspx
<Columns>

...

</Columns>
```

This gives full control over the displayed columns.

---

## 4. Width

```aspx
Width="600px"
```

Sets GridView width.

---

## 5. CssClass

```aspx
CssClass="table"
```

Applies CSS styling.

---

## 6. Visible

```aspx
Visible="True"
```

Shows or hides the GridView.

---

# GridView Example

```aspx
<asp:GridView

ID="gvEmployee"

runat="server"

AutoGenerateColumns="True"

Width="600px">

</asp:GridView>
```

---

# Output

```text
EmployeeID

Name

Department

Salary
```

---

# 4. GridView Events (Introduction)

GridView supports many events.

| Event        | Purpose                   |
| ------------ | ------------------------- |
| RowEditing   | Edit a row                |
| RowUpdating  | Save edited row           |
| RowDeleting  | Delete a row              |
| RowCommand   | Execute custom commands   |
| RowDataBound | Format rows while binding |

You will learn these in detail later.

---

# GridView vs Label

Label

```text
Employee Name
```

One value only.

---

GridView

```text
EmployeeID

Name

Department

Salary
```

Displays many records.

---

# GridView vs Table

HTML Table

* Static
* Manual coding

GridView

* Dynamic
* Connected to database
* Supports CRUD
* Supports Paging
* Supports Sorting

---

# Company Example

Suppose HR wants all employees.

Instead of writing

```text
Nick

John

Alex

Sam

David

...
```

The developer writes

```aspx
<asp:GridView

ID="gvEmployees"

runat="server">

</asp:GridView>
```

ASP.NET automatically creates all rows after data binding.

---

# Interview Questions

### Q1. What is GridView?

A server control used to display data in tabular format.

---

### Q2. Which namespace contains GridView?

```text
System.Web.UI.WebControls
```

---

### Q3. Which property automatically creates columns?

```text
AutoGenerateColumns
```

---

### Q4. Which property gives the GridView its unique name?

```text
ID
```

---

### Q5. Does the browser receive a GridView?

No.

The browser receives an HTML table generated by ASP.NET.

---

### Q6. Can GridView display multiple records?

Yes.

It is specifically designed for displaying multiple records.

---

### Q7. Which layer usually provides data to GridView?

The Data Access Layer (DAL), often through ADO.NET using a `DataTable` or `DataSet`.

---

# Flashcards

**Q:** Which control displays data in a table?
**A:** GridView.

**Q:** Which property creates columns automatically?
**A:** `AutoGenerateColumns`.

**Q:** Which attribute is mandatory?
**A:** `runat="server"`.

**Q:** Does GridView generate HTML?
**A:** Yes, ASP.NET converts it into an HTML table.

**Q:** Which namespace contains GridView?
**A:** `System.Web.UI.WebControls`.

**Q:** Can GridView edit and delete records?
**A:** Yes.

---

# Mini Practice

1. What is a Data Control?
2. Name three ASP.NET Data Controls.
3. What is GridView?
4. Why is GridView used instead of Labels for database records?
5. Explain the purpose of `AutoGenerateColumns`.
6. What happens when `AutoGenerateColumns="False"`?
7. Which property specifies the GridView width?
8. Draw the GridView Architecture.

---

# Quick Revision

## Data Controls

* Display data from databases.
* Support multiple records.
* Used in enterprise applications.

## GridView

* Displays data in a table.
* Most commonly used ASP.NET Web Forms data control.
* Supports:

  * Display
  * Edit
  * Update
  * Delete
  * Paging
  * Sorting

## Important Properties

* `ID`
* `runat="server"`
* `AutoGenerateColumns`
* `Width`
* `CssClass`
* `Visible`

## Important Point

A **GridView is never sent directly to the browser**. ASP.NET converts it into a standard **HTML table**, which is what the browser renders.

---

# Company Notes (Legacy ASP.NET Web Forms)

In most legacy Web Forms projects, you'll encounter GridViews on pages such as:

* Employee List
* Customer List
* Product List
* Order History
* Leave Requests
* User Management

Developers typically bind a `DataTable` or `DataSet` returned from ADO.NET to the GridView. Later, they add features like paging, sorting, editing, and deleting using built-in GridView functionality.
