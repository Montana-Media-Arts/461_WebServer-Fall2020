---
title: Stored Persistant XSS
module: 11
jotted: false
---

# Stored (persistent) XSS

This type of application vulnerability occurs when a attack vector contains JavaScript that doesn't come in a user request. Instead, the JavaScript code is downloaded from the server (such as the database or file system).

The application might allow you to save data from an untrusted source and, subsequently, use this data to generate a server response to a client's request. Paired with poor handling of HTML escape sequences, this presents an opportunity for a stored XSS attack.

Imagine an online forum where people communicate regularly. If the application is vulnerable, an attacker can post a message with embedded JavaScript. The message will be saved in the system database. After that, the script in question will be executed by all users who read the message posted by the attacker.

Example of stored (persistent) XSS
An example of code for exploitation of stored XSS vulnerabilities:

```js
protected void doGet(HttpServletRequest rq, HttpServletResponse resp) {
    String name = rq.getParameter("NAME");
    StringBuffer res = new StringBuffer();
    String query = "SELECT fullname FROM emp WHERE name = '" + name + "'";
    ResultSet rs = DB.createStatement().executeQuery(query);
    res.append("<table class=\"table\"><tr><th>Employee</th></tr>");
    while (rs.next()) {
        res.append("<tr><td>");
        res.append(rs.getString("fullname"));
        res.append("</td></tr>");
    }
    res.append("</table>");
    resp.getWriter().append(res.toString());
}   
```

Here, data is read from the database and the results are passed along without client verification. If the data stored in the database contains HTML escape sequences, including JavaScript, the data will be passed to the client and executed by the browser in the context of the web application.