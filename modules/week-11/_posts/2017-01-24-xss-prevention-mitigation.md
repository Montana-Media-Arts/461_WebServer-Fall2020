---
title: XSS Prevention and Mitigation
module: 11
jotted: false
---

# XSS attack prevention and mitigation

From a technical point of view, XSS is an injection-class vulnerability, in which the attacker manipulates the logic of the web application in a browser. So to prevent such vulnerabilities, one needs to thoroughly check any data that enters the application from the outside. To do so, the application must implement a number of approaches, which we describe here.

## Force inputs to the same data type

User input is initially presented in string form. This data should be transformed into objects of a specified type. This functionality is often implemented at the framework level, so that the action is transparent to the user. One such transparent process takes place in the following Java code:

```java
@GetMapping(value = "/result")
public void getJobResult(
        @RequestParam(name = "scan-id") Integer scanId,
        @RequestParam(name = "artifact") String artifact,
        HttpServletResponse response) throws ServiceUnavailableException {
    // Real controller code skipped
```

This example shows the declaration of an HTTP GET request handler. It's accessible at the relative path "/result" and takes two required parameters as input: integer scan-id and string artifact. During initial processing of the request, the framework performs the actions needed to determine the correctness of the inputs.

In the event of a type mismatch, the requesting party sees an error message even before control transfers to the application code. This would happen if, for instance, a scan-id parameter contains a non-numeric value.

## Input validation

During validation, input data is checked against both grammatical and semantic criteria. The user's year of birth, say, can be checked for grammar with the regular expression "^[0-9]{4}$". This expression verifies that the string truly consists of four (and only four) digits. Once the string is converted to a number, we then need to check semantics: the year of birth should not be 1000 or 9876.

It also makes sense to apply allowlist and blocklist validation. For a blocklist, you need to define certain patterns that shouldn't be found in the input data.

However, blocklist approaches have a number of serious disadvantages. Patterns tend to be needlessly complex and become obsolete quickly. Creating patterns to cover all possible permutations of malicious data is far from easy. Developers will inevitably find themselves struggling to catch up with attackers. This is why it is more efficient to apply an allowlist that defines rules with which input data must comply.

## Output sanitization

Regardless of how well (or not) the previous two techniques are implemented, the key action for preventing XSS is to check and convert output data. It is important to ensure that untrusted data cannot be passed to an HTML document. The exceptions are certain contexts in which the data still needs to follow certain rules. These rules must ensure that the web browser treats the output as data, not as code. These contexts include:

Context

Method/property

Content of HTML element

<div>userData</div>

Value attribute of HTML element

<input value="userData">

Value in JavaScript

var name="userData";

Value of URL request parameter

http://site.org/?param=userData

Value in CSS

color:userData

For each of these contexts, you should apply individual verification and conversion rules. For the content of an HTML element (such as inside <div>, <p>, <b>, <td>, and similar tags), XML and HTML special characters should be replaced with safe variants. Replace "&" with "&amp", "<" with "&lt;", ">" with "&gt;", double quotes with "&quot;", and single quotes with "«&#x27;".

The "/" character, which can close HTML tags, is replaced by "&#x2F;". For example, when using the StringEscapeUtils.escapeHtml4 function from the Apache Commons Text library on the server side, user-entered data is made safe like so:

String data = "<script>alert(1)</script>";

String safeData = StringEscapeUtils.escapeHtml4(data);

The result of the conversion will be the string "&lt;script&gt;alert(1)&lt;/script&gt;", which will not be parsed by the browser as an HTML escape sequence.

The LibProtection library allows automatically determining context and sanitizing data. In addition, the library can signal when input data contains an attack vector.

For example, the following code fragment contains three points at which user data can be embedded:

Value attribute of HTML element (a)
Value of JavaScript parameter (b)
Content of HTML element (c)

```csharp 
Response.Write($"<a href='{a}' onclick='alert("{b}");return false'>{c}</a>");
```

Let's assume that the attacker has passed the following variables as input:

```js
a = 'onmouseover='alert(`XSS`)
b = ");alert(`XSS`)
c = <script>alert(`XSS`)</script>
```
If we do not check the input, the response will look like this:

```html    
<a href=''onmouseover='alert(`XSS`)' onclick='alert("");alert(`XSS`)");return false'><script>alert(`XSS`)</script></a>
```

Thus an attacker can perform an XSS attack in three different ways. LibProtection converts data, determining the context and applying rules in a way transparent to the developer:

```csharp    
Response.Write(SafeString.Format<Html>($"<a href='{a}' onclick='alert("{b}");return false'>{c}</a>"));
```

The resulting string is converted to:

```html
<a href='%27onmouseover%3d%27alert(%60XSS%60)' onclick='alert("\&quot;);alert(`XSS`)");return false'>&lt;script&gt;alert(`XSS`)&lt;/script&gt;</a>
```

LibProtection supports C #, Java, and C ++ and allows sanitizing inputs against other types of attacks. This protection extends to SQL injection and vulnerabilities based on improper handling of URLs and path directories.

Client- and server-side sanitization

Data can be sanitized in different ways based on the application architecture and programming languages used. Because technologies and languages can be so different, it is hard to recommend one single way for checking on the server side. But since JavaScript has become the de facto standard on the client side, we can still try to formulate universal principles for a number of contexts:

Context

Method/property

Content of HTML element

<div>userData</div>

Value attribute of HTML element

<input value="userData">

Value in JavaScript

var name="userData";

Value of URL request parameter

http://site.org/?param=userData

Value in CSS

color:userData

All sanitizing algorithms have limitations. For instance, even if you apply rules to sanitize the href HTML attribute, an attacker can still pass URL values that start with "javascript:".

## Additional XSS prevention measures

Checking inputs and outputs is the main way to protect against XSS attacks—but not the only one. You should also consider:

Standardization at the header level of Content-Type and X-Content-Type-Options. Ensure that the server response type is not "text / html" and prevent the browser from automatically detecting the data type (X-Content-Type-Options: nosniff).
Use of a Content Security Policy (CSP) to minimize negative consequences when malicious code is injected.
XSS cheat sheet
This cheat sheet provides guidance against a huge number of XSS attack vectors. Even just basic rules will be enough to stop the majority of attacks. Here are the most important ones:

1. Deny all untrusted data unless it's inserted in allowed locations.
2. Use HTML escaping before putting untrusted data into the HTML body.
3. Use escaping in HTML attributes before adding untrusted data into HTML common attributes.
4. Escape JavaScript before putting untrusted data inside data values.
5. Escape CSS before inserting untrusted data into HTML style property values.
6. Escape URLs before passing untrusted data to HTML URL parameter values.
7. Use a library to parse and sanitize HTML formatted text.
8. Since XSS can be used to infiltrate a website and attack users in many ways, it's important to approach security from multiple perspectives. Developers need to receive training on secure coding and best practices. Scan the codebase as early and frequently as possible to detect potential flaws and breaches. Pay special attention to accounts that have administrative privileges and the ability to modify page contents. To get a better angle on website security, refer to trustworthy sources like the OWASP Cheat Sheet.

### ASP.NET

```csharp
string text = HttpUtility.HtmlEncode(SomeText.Text);
```

If some markup is required:

```csharp
public static class SecurityUtility
{
    // Remove markup
    public static string RemoveHtml(string text)
    {
        // replace anything that is not a > between <> to nothing
        return Regex.Replace(text, "<[^>]*>", String.Empty);
    }
    // Covert metamarkup
    public static string ConvertHtml(string text)
    {
        text = text.Replace("[b]", "<b>").Replace("[/b]", "</b>");
        text = text.Replace("[i]", "<i>").Replace("[/i]", "</i>");
        text = text.Replace("[u]", "<u>").Replace("[/u]", "</u>");
        return text;
    }
}
```

Using this class

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
using System.Text.RegularExpressions;
public partial class MarkupConvert : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {

    }
    protected void btnSubmit_Click(object sender, EventArgs e)
    {
        string text;
        text = SecurityUtility.ConvertHtml(txtTest.Text);
        lblLegend.Text = SecurityUtility.RemoveHtml(text);
    }
}
```
<a href="https://www.howtoasp.net/how-to-handle-and-display-user-input-to-protect-asp-net-web-application-from-xss-in-c/" target="_new"><em>Source</em></a>

### Preventing XSS in HTML and PHP

Following are the methods by which we can prevent XSS in our web applications –

1. Using htmlspecialchars() function – The htmlspecialchars() function converts special characters to HTML entities. For a majority of web-apps, we can use this method and this is one of the most popular methods to prevent XSS. This process is also known as HTML Escaping.

'&' (ampersand) becomes '&amp;'

"" (double quote) becomes '&quot;'

'>' (greater than) becomes '&gt;'

2. htmlentities() – htmlentities() also performs the same task as htmlspecialchars() but this function covers more character entities. Using this function may also lead to excessive encoding and may cause some content to display incorrectly.

3. strip_tags() – This function removes content between HTML tags. This function also does not filter or encode non-paired closing angular braces.

4. addslashes() – The addslashes() function adds a slash character in an attempt to prevent the attacker from terminating the variable assignment and adding the executable code at the end.

5. Content Security Policy (CSP) – CSP is the last option that we choose to defend against XSS attack. The use of CSP puts restrictions on the attacker’s actions. Our browser executes all the JavsScript it receives from the server, whether they be internally sourced or externally sourced. When it comes to an HTML document, the browser fails to determine whether the resource is malicious or not. CSP is an HTTP header that whitelists a set of trusted resource sources that a browser can use to determine trust in the incoming resource.

6. X-Content-Security-Policy: script-src 'self'
The above line implies the browser to only trust the source URL which refers to the current domain. All the inputs for resources will be grabbed by the browser from this source only and all the others will be ignored.
There are many resource directives that we can add. Some of them are given below –

7. connect-src: Limits the sources to which you can connect using XMLHttpRequest, WebSocket, etc.

8. font-src: Limits the sources for web fonts. frame-src: Limits the source URLs that can be embedded on a page as frames.

9. img-src: Limits the sources for images. media-src: Limits the sources for video and audio.

10. object-src: Limits the sources for Flash and other plugins. script-src: Limits the sources for script files.

11. style-src: Limits the sources for CSS files.

12. Third Party PHP Libraries – There are also some third party PHP libraries that help in prevention of XSS. Some of these are listed below –
htmLawed
* PHP Anti-XSS
* HTML Purifier
* Among all of these, HTMLPurifier is frequently maintained and updated. It is quite simple to use, once the developer has attained a basic level of HTML scripting knowledge.

## Examples

Example
Convert the predefined characters "<" (less than) and ">" (greater than) to HTML entities:

```php
<?php
$str = "This is some <b>bold</b> text.";
echo htmlspecialchars($str);
?>
```

The HTML output of the code above will be (View Source):

```html
<!DOCTYPE html>
<html>
<body>
This is some &lt;b&gt;bold&lt;/b&gt; text.
</body>
</html>
```

The browser output of the code above will be:

This is some <b>bold</b> text.