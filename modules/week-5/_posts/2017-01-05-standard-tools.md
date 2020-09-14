---
title: Standard Tools
module: 5
jotted: true
---

# Standard Tools

## TextBoxes

We have worked with these already the main method is the .Text method which allows us to retrieve anything that was entered.  We can also insert data into the textbox by using Text as well.

There is also an TextChanged event that fires when text is entered.

```html

   <asp:TextBox id="txtName" runat="server" OnTextChanged="txtName_TextChanged"></asp:TextBox>

```
## Buttons

We typically use buttons to submit information to the server.  We use the click event to handle these requests.  We can change the text server-side, but if we want to disable a button from being clicked twice we need to do that client-side.

```html
 <asp:Button ID="btnSubmit" runat="server" Text="Submit" OnClick="btnSubmit_Click" />
```

## Labels

These controls are handy for displaying messages and updating the user.  We want to make sure we give users adequate feedback within our web applications.

```html
 <asp:Label ID="lblMessage" runat="server"></asp:Label>
```

## Checkboxes

These controls are useful when thinking about allowing users to choose one or more items in a list.  Please do not use checkboxes for mutually exclusive choices.  It will break standardization that users are used to.

```html
    <asp:CheckBox ID="CheckBox1" runat="server" Checked="True" />
    <br />
    <asp:CheckBox ID="CheckBox2" runat="server" />
```

## RadioButtons

These controls are meant so that users can choose only one item from a list.  This is standard and users are familiar with this.

```html
    <asp:RadioButton ID="RadioButton1" runat="server" GroupName="myButtons" />
    <br />
    <asp:RadioButton ID="RadioButton2" runat="server" GroupName="myButtons" />
```

## Calendar

The calendar control is a nice control which allows us to easily add a calendar to our site.  We can then get the current date or the date selected.  This helps users when they need to choose a date for reservations, events, or other applications.  Calendars are great visual indicators for users rather than relying on the user's memory of numerical dates.

```html

<asp:Calendar ID="Calendar1" runat="server"></asp:Calendar>

```

## Images

This controls allows us to dynamically change images when the web page is sent to the server.  Typically we set images in an img tag and then we would need to either manually update the image in the HTML or get the data through JavaScript.  This technique is perfectly viable, but the Image control simplifies the process.

```html
 <asp:Image ID="Image1" runat="server" />
```

## HyperLinks

These server-side controls allows us to dynamically create hyperlinks for the user so that the site is customized while the user navigates rather than having a static experience throughout.

```html
<asp:HyperLink ID="HyperLink1" runat="server">HyperLink</asp:HyperLink>
```

**Note** Please keep in mind that each of these controls must go to the server before they can be renderer.  This increases the load time of the page.  IIS makes it faster with object pooling, but the first request to the server will take longer.