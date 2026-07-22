# Phase 3 – ASP.NET Web Forms (Part 2A)

# Basic Web Forms Controls

## Topics Covered

1. Label
2. TextBox
3. Button
4. LinkButton
5. HyperLink
6. Image

---

# Introduction to ASP.NET Server Controls

## Definition

**ASP.NET Server Controls** are controls that run on the **server** and generate HTML that is sent to the browser.

Every server control must contain:

```aspx
runat="server"
```

Without this attribute, ASP.NET treats it as a normal HTML element.

---

# Server Control Architecture

```text
Browser

↓

HTML Request

↓

IIS

↓

ASP.NET

↓

Server Controls

↓

HTML Generated

↓

Browser
```

The browser never sees ASP.NET controls.

It only receives HTML.

---

# Basic Syntax

```aspx
<asp:ControlName
    ID="ControlID"
    runat="server" />
```

---

# 1. Label Control

## Definition

A **Label** control displays text on a web page.

Users **cannot edit** the text.

---

## Properties

| Property  | Purpose              |
| --------- | -------------------- |
| ID        | Unique control name  |
| Text      | Text displayed       |
| ForeColor | Text color           |
| Font      | Font settings        |
| Visible   | Show or hide control |

---

## Example

```aspx
<asp:Label
ID="lblMessage"
runat="server"
Text="Welcome"
ForeColor="Blue">
</asp:Label>
```

---

## Code Behind

```csharp
lblMessage.Text = "Welcome Nick";
```

---

## Output

```text
Welcome Nick
```

---

## Company Usage

* Success messages
* Error messages
* Employee names
* Login status
* Report headings

---

# 2. TextBox Control

## Definition

A **TextBox** allows users to enter input.

---

## Common Properties

| Property  | Purpose                         |
| --------- | ------------------------------- |
| Text      | Input value                     |
| TextMode  | SingleLine, Password, MultiLine |
| MaxLength | Maximum characters              |
| ReadOnly  | Prevent editing                 |
| Enabled   | Enable or disable control       |

---

## Example

```aspx
<asp:TextBox
ID="txtName"
runat="server">
</asp:TextBox>
```

---

## Reading User Input

```csharp
string name = txtName.Text;

lblMessage.Text = name;
```

---

## Output

Input

```text
Nick
```

Output

```text
Nick
```

---

# Password TextBox

```aspx
<asp:TextBox
ID="txtPassword"
runat="server"
TextMode="Password">
</asp:TextBox>
```

Output

```text
******
```

---

# MultiLine TextBox

```aspx
<asp:TextBox
ID="txtAddress"
runat="server"
TextMode="MultiLine">
</asp:TextBox>
```

---

## Company Usage

* Login
* Registration
* Search
* Feedback
* Employee Forms

---

# 3. Button Control

## Definition

A **Button** sends the page to the server and executes server-side code.

---

## Example

```aspx
<asp:Button
ID="btnSave"
runat="server"
Text="Save"
OnClick="btnSave_Click"/>
```

---

## Code Behind

```csharp
protected void btnSave_Click(
object sender,
EventArgs e)
{
    lblMessage.Text = "Data Saved";
}
```

---

## Output

```text
Data Saved
```

---

# Button Flow

```text
User Clicks Button

↓

Browser Sends Request

↓

ASP.NET

↓

Button_Click

↓

Response Returned
```

---

## Company Usage

* Save
* Update
* Delete
* Login
* Search
* Submit

---

# 4. LinkButton

## Definition

A **LinkButton** looks like a hyperlink but behaves like a server-side button.

---

## Example

```aspx
<asp:LinkButton
ID="lnkDelete"
runat="server"
OnClick="lnkDelete_Click">

Delete

</asp:LinkButton>
```

---

## Code Behind

```csharp
protected void lnkDelete_Click(
object sender,
EventArgs e)
{
    lblMessage.Text =
    "Record Deleted";
}
```

---

## Output

```text
Record Deleted
```

---

## Difference

Normal Button

```text
[ Save ]
```

LinkButton

```text
Delete
```

Both execute server-side events.

---

## Company Usage

GridView usually contains:

* Edit
* Delete
* View

implemented using LinkButton controls.

---

# 5. HyperLink

## Definition

A **HyperLink** is used to navigate from one page to another.

Unlike LinkButton, it **does not execute server-side events**.

---

## Example

```aspx
<asp:HyperLink
ID="hlHome"
runat="server"
NavigateUrl="Home.aspx"
Text="Home">
</asp:HyperLink>
```

---

## Output

```text
Home
```

Clicking it opens:

```text
Home.aspx
```

---

## HyperLink vs LinkButton

| HyperLink   | LinkButton        |
| ----------- | ----------------- |
| Navigation  | Executes event    |
| No PostBack | Causes PostBack   |
| Faster      | Server processing |

---

## Company Usage

* Home
* Dashboard
* Reports
* Profile
* Logout

---

# 6. Image Control

## Definition

Displays an image on the web page.

---

## Example

```aspx
<asp:Image
ID="imgLogo"
runat="server"
ImageUrl="Images/logo.png"
Width="150"
Height="100"/>
```

---

## Output

Displays:

```text
Company Logo
```

---

## Changing Image Dynamically

```csharp
imgLogo.ImageUrl =
"Images/User1.jpg";
```

---

## Company Usage

* Employee Photos
* Company Logo
* Product Images
* Reports
* User Profile

---

# Comparison of Basic Controls

| Control    | Purpose                       |
| ---------- | ----------------------------- |
| Label      | Display text                  |
| TextBox    | Accept user input             |
| Button     | Execute server-side code      |
| LinkButton | Hyperlink-style server button |
| HyperLink  | Navigate to another page      |
| Image      | Display images                |

---

# Complete Example

## ASPX Page

```aspx
<asp:Label
ID="lblResult"
runat="server"/>

<br/>

<asp:TextBox
ID="txtName"
runat="server"/>

<br/>

<asp:Button
ID="btnShow"
runat="server"
Text="Show"
OnClick="btnShow_Click"/>
```

---

## Code Behind

```csharp
protected void btnShow_Click(
object sender,
EventArgs e)
{
    lblResult.Text =
    "Welcome " + txtName.Text;
}
```

---

## Output

Input

```text
Nick
```

Output

```text
Welcome Nick
```

---

# Interview Questions

### Q1. What is a Server Control?

A control that executes on the server and generates HTML for the browser.

---

### Q2. Which attribute is mandatory?

```aspx
runat="server"
```

---

### Q3. Which control displays text?

Label

---

### Q4. Which control accepts user input?

TextBox

---

### Q5. Which property reads TextBox data?

```csharp
Text
```

---

### Q6. Which event executes when a button is clicked?

```text
Button_Click
```

---

### Q7. Difference between HyperLink and LinkButton?

HyperLink only navigates.

LinkButton performs a server-side postback and executes an event.

---

### Q8. Which property sets the image location?

```text
ImageUrl
```

---

### Q9. Which TextMode hides characters?

```text
Password
```

---

### Q10. Which TextMode creates a multi-line input?

```text
MultiLine
```

---

# Flashcards

**Q:** Which control shows text?
**A:** Label.

**Q:** Which control takes user input?
**A:** TextBox.

**Q:** Which property reads user input?
**A:** `Text`.

**Q:** Which control executes `Button_Click`?
**A:** Button.

**Q:** Which control looks like a link but runs server code?
**A:** LinkButton.

**Q:** Which control only navigates?
**A:** HyperLink.

**Q:** Which property sets an image?
**A:** `ImageUrl`.

**Q:** Which attribute is required for ASP.NET server controls?
**A:** `runat="server"`.

---

# Mini Practice

1. Create a Label that displays **"Employee Portal"**.
2. Create a TextBox for entering an employee name.
3. Create a Password TextBox.
4. Create a Button that displays **"Welcome Employee"** in a Label.
5. Create a LinkButton named **Delete**.
6. Create a HyperLink to **Dashboard.aspx**.
7. Display the company logo using the Image control.
8. Explain the difference between HyperLink and LinkButton.

---

# Quick Revision

## Label

* Displays text.
* User cannot edit it.

## TextBox

* Accepts user input.
* Common `TextMode` values:

  * SingleLine
  * Password
  * MultiLine

## Button

* Executes server-side code through events such as `Button_Click`.

## LinkButton

* Looks like a hyperlink.
* Performs a postback and executes server-side code.

## HyperLink

* Navigates to another page.
* Does not execute server-side events.

## Image

* Displays images.
* Uses the `ImageUrl` property.

---

# Company Notes (Legacy ASP.NET Web Forms)

These controls are used extensively in enterprise applications:

* **Label** → Display messages, employee names, report titles.
* **TextBox** → Login forms, search boxes, data entry.
* **Button** → Save, Update, Delete, Login, Search.
* **LinkButton** → GridView actions like Edit, Delete, View.
* **HyperLink** → Navigation menus and dashboards.
* **Image** → Company logo, employee profile pictures, product images.

As a fresher, you should be able to create these controls, read and update their properties in the code-behind, and explain when to use each one.
