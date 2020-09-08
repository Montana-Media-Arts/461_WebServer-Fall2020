---
title: QueryStrings
module: 4
jotted: true
---

# QueryStrings

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Webforms')">QueryStrings with Web Forms</button>
 <button class="tablinks" onclick="openTab(event, 'PHP')">QueryStrings with PHP</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block">
The web doesn't have state because of the high volume of users would decimate the memory on our servers.
</div>
<div id="Webforms" class="tabcontent">
<div class="tabhtml" markdown="1">
<p>Access QueryStrings in Webforms</p>
  <p>What is the code to access querystrings on a webform</p>

  ```csharp
    Request.QueryString["NameOfVariable"].ToString();
  ```
</div>  
</div>
<div id="PHP" class="tabcontent">
<div class="tabhtml" markdown="1">
<p>Access QueryStrings in PHP</p>
<p>What is the code to access querystrings on a PHP form</p>

  ```php
    $_GET["NameofVariable"]
    $_SERVER['QUERY_STRING'] // what does that do?
  ```
  </div>
</div>
