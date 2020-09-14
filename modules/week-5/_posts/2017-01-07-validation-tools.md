---
title: Validation Tools
module: 5
jotted: true
---

# Validation Tools

These tools attach to existing controls on the page.  We can connect them and make the overall page unmoving until the entire paeg is valid.

## RequiredFieldValidator

This control ensures that the control contains any information.  This control is typically connected to textboxes to check that something was entered.

```html
<asp:RequiredFieldValidator ID="RequiredFieldValidator1" runat="server" ErrorMessage="RequiredFieldValidator"></asp:RequiredFieldValidator>
```

## RegularExpressionValidator

This control checks to see if the information that was entered matches a pattern.  This is useful for checking things like email, phone, and more.

```html
<asp:RegularExpressionValidator ID="RegularExpressionValidator1" runat="server" ErrorMessage="RegularExpressionValidator"></asp:RegularExpressionValidator>
```

## RangeValidator

This controls ensures that the values entered fall within a certain range.  It handles the logic to determine this.

```html
<asp:RangeValidator ID="RangeValidator1" runat="server" ErrorMessage="RangeValidator"></asp:RangeValidator>
```

## CompareValidator

In this final control, the value entered is compared to something in the validator.  It could be checking to see if the value is greater than, less than or equal to.

```html
<asp:CompareValidator ID="CompareValidator1" runat="server" ErrorMessage="CompareValidator"></asp:CompareValidator>
```

## In PHP

```php
<?php
$str = "Visit W3Schools";
$pattern = "/w3schools/i";
echo preg_match($pattern, $str); // Outputs 1 if there is a match, 0 if not.
?>
```

<a href="https://www.w3schools.com/php/php_ref_regex.asp" target="_new"> PHP Regular Expression Reference</a>