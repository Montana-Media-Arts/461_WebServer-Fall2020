---
title: PHP Simple Page
module: 3
---

# Create a PHP Page

You can use VS Code, Atom or any other editor to create a simple PHP file.  Just remember, it must start with:

```php
    <?
```
and end with
```php
    ?>
```
In the previous example, calling phpinfo() displayed which version of php was installed on the machine.

One can also put in the following:

```php
    <? echo 'Hello world!' ?>
```

Finally, one can also inject php code inside of HTML like this.

```html
<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
 <?php echo '<p>Hello World</p>';
 phpinfo();
 ?> 
 </body>
</html>
```
