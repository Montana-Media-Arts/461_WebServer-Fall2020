---
title: ASP.NET web.config
module: 11
jotted: false
---

# web.config

One the biggest things we can do is to prevent end-users for seeing what is going on if there is an error. For example, we can change the web.config file so that it looks like this.

```xml
<customErrors mode="On" defaultRedirect="/error" >
    <error statusCode="400" redirect="/error/badrequest"  />
    <error statusCode="404" redirect="/error/notfound"  />
    <error statusCode="500" redirect="/error/internalerror"  />
</customErrors> 
```
