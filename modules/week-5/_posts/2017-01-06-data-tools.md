---
title: Data Tools
module: 5
jotted: true
---

# Data Tools

Again, we aren't quite to a place were can completely integrate our databases with our server-side controls, but I want you to be aware of them so you can use them when we get there.

## SqlDataSource

This built-in data control allows us to connect to our SQL Database easily and reliability.  We will look at this after we learn the internal working of connection strings.

```html
<asp:SqlDataSource ID="SqlDataSource1" runat="server"></asp:SqlDataSource>
```

## XMLDataSource

This data control allows us to connect to XML data sources which is heirarchal data source.

```html
<asp:XmlDataSource ID="XmlDataSource1" runat="server"></asp:XmlDataSource>
```

## GridView

This control allows us to display our data in a row and column format with paging, sorting, and more.  It fast and quite useful.

```html
<asp:GridView ID="GridView1" runat="server"></asp:GridView>
```