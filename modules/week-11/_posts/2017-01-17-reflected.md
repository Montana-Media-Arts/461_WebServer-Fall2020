---
title: Reflected XSS
module: 11
jotted: false
---

# Reflected (non-persistent) XSS

In reflected XSS, the attack vector is inside the HTTP client request processed by the server. If the server's request and response are semantically related, the server's response is formed from the request data. For example, the request could be a search query and the response might be the results page.

Reflected XSS occurs if the server does a poor job of processing HTML escape sequences. In this case, the page as displayed on the server side will cause JavaScript to be executed in the context of the server, which is part of the original attack vector.

Example of reflected (non-persistent) XSS
Here is an example of thecode vulnerable code below.to reflected XSS:

    
```js
protected void info(HttpServletResponse resp, String info) {
    resp.getWriter().append("<h4>Info</h4>");
    resp.getWriter().append(info);
}
```