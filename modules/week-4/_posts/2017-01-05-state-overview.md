---
title: State
module: 4
jotted: true
---

# What is State?

<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Querystrings')">QueryStrings</button>
 <button class="tablinks" onclick="openTab(event, 'Cookies')">Cookies</button>
 <button class="tablinks" onclick="openTab(event, 'Sessions')">Sessions</button>
 <button class="tablinks" onclick="openTab(event, 'Database')">Database</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block">
The web doesn't have state because of the high volume of users would decimate the memory on our servers. So, we will look at different techniques to save state between pages.  Otherwise, all that information will be lost from page to page.
</div>
<div id="Querystrings" class="tabcontent">
The first one is the querystring. We have seen this with our GET in PHP.  Whenever we send information from a form to the server in the address bar.
<p>How and why are they used?</p>
<p>What are the security risks in using them?</p>
<p>Can we view the contents</p>
<p>What can be stored in them?</p></div>
<div id="Cookies" class="tabcontent">
What are cookies?  Cookies are small files that contain information that can be accessed on the client.
<p>How and why are they used?</p>
<p>What are the security risks in using them?</p>
<p>Can we view the contents</p>
<p>What can be stored in them?</p>
</div>
<div id="Sessions" class="tabcontent">
Sessions are another way to store state.  They allow us to files that are only good while the current user session is active.
<p>How and why are they used?</p>
<p>What are the security risks in using them?</p>
<p>Can we view the contents</p>
<p>What can be stored in them?</p>
</div>
<div id="Database" class="tabcontent">
Databases are the final way in which we can control state on a page.  We can derive what content should be shown based on some variable, retrieve information from the database and then display it on the page.
<p>How and why are they used?</p>
<p>What are the security risks in using them?</p>
<p>Can we view the contents</p>
<p>What can be stored in them?</p>
</div>

