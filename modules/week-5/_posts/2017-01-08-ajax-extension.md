---
title: AJAX Extensions
module: 5
jotted: true
---

# AJAX Extensions

## ScriptManager

This control is required for any of the AJAX controls to function correctly. It handles all the requests correctly.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server"></asp:ScriptManager>
```

## UpdatePanel

This control allows for partial page updates which means one can update a section of the page without reloading the entire page.

```html
    <asp:UpdatePanel ID="UpdatePanel1" runat="server"></asp:UpdatePanel>
```

## UpdateProgress

This control provides status updates when an AJAX call is being performed.

```html
<asp:UpdateProgress ID="UpdateProgress1" runat="server"></asp:UpdateProgress>
```

## Timer

This control acts like a clock and performs actions on continual basis until the clock is turned off.

```html
<asp:Timer ID="Timer1" runat="server"></asp:Timer>
```