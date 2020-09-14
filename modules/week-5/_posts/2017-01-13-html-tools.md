---
title: Basic HTML Controls
module: 5
jotted: true
---

# HTML Tools

These are the basic HTML controls that are not server side controls.  However, we can still access them in the code view or design view in Visual Studio.

## Input

This is the basic tag that that is used for all these components.  The type of component changes based on the attribute **type** that is set.

### Text

As you all know we have worked with this many times. It's out basic input field so that we can add free-form text.

```html
<input id="Text1" type="text" />
```

### Button

With this control, users can click on a basic button to navigate to another page or process information on the same page.

```html
<input id="Button1" type="button" value="button" />
```

### Password

This control hides the data that is being entered through the web browser.  Of course, the data is not hidden or encrypted when it is sent to the server.  That has to be changed through another mechanism.

```html
<input id="Password1" type="password" />
```

### Checkbox

This basic control allows us to create multiple choices for our end users.  We create groups to ensure that they are controlled under one selection.

```html

<input type="checkbox" id="vehicle1" name="vehicle1" value="Bike">
<label for="vehicle1"> I have a bike</label><br>
<input type="checkbox" id="vehicle2" name="vehicle2" value="Car">
<label for="vehicle2"> I have a car</label><br>
<input type="checkbox" id="vehicle3" name="vehicle3" value="Boat">
<label for="vehicle3"> I have a boat</label><br>

```

### Radio

This control allows us to add multiple choices, but allow the user to only choose one.  This is vital for mutually exclusive items.  We must have a group to ensure that these choices remain exclusive to one another.

```html

<input type="radio" id="male" name="gender" value="male">
<label for="male">Male</label><br>
<input type="radio" id="female" name="gender" value="female">
<label for="female">Female</label><br>
<input type="radio" id="other" name="gender" value="other">
<label for="other">Other</label>

```