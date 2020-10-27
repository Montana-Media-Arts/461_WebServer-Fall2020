---
title: Cross Scripting Attacks
module: 11
jotted: false
---

# Cross Scripting Attacks

## Defintion

Cross-site scripting, often abbreviated as XSS, is a type of attack in which malicious scripts are injected into websites and web applications for the purpose of running on the end user's device. During this process, unsanitized or unvalidated inputs (user-entered data) are used to change outputs.

Some XSS attacks do not have a specific target; the attacker simply exploits a vulnerability in the application or site, taking advantage of anyone unlucky enough to fall victim. But in many cases, XSS is performed in a more direct way, such as in an email message. An XSS attack can turn a web application or website into a vector for delivering malicious scripts to the web browsers of unsuspecting victims.

XSS attacks can exploit vulnerabilities in a range of programming environments, including VBScript, Flash, ActiveX, and JavaScript. Most often, XSS targets JavaScript because of the language's tight integration with most browsers. This ability to exploit commonly used platforms makes XSS attacks both dangerous and common.

## How does it work?

Armed with this idea of what a cross-site scripting attack is, let's see how it works.

Imagine a person sitting at a computer. The screen shows a file manager, text editor, spreadsheet, and music player icon in the lower-right corner. All is ordinary and familiar so far. But something is missing from this picture—an Internet browser with dozens of tabs open simultaneously.

These tabs are filled with interesting headlines, funny videos, ads for sporting goods, online stores, and a payment site with a just-paid receipt for a speeding ticket. All of these sites have one thing in common: they would hardly be possible without JavaScript.

Then a simple click on an advertising banner triggers another page. The page contains a script that connects to an online banking site and quietly transfers money from the user's account to the attacker's card. Rather unpleasant, to put it mildly. Fortunately, browsers eliminate this possibility thanks to the same-origin policy (SOP). This policy ensures that the scripts executed on a web page don't have access to the wrong data. If scripts have been loaded from a different domain, the browser won't be able to run them.

Does this guarantee a happy ending?

Cybercriminals use various methods to bypass the SOP and exploit application vulnerabilities. When successful, they make the user's browser execute an arbitrary script on a given page.

## Infect a website

The same-origin policy is supposed to allow scripts only when a script is loaded from the same domain as the page that the user is currently viewing. And in reality, attackers don't have direct access to the server responsible for the page displayed by the browser. So how do attackers do it?

Application vulnerabilities can help attackers by enabling them to embed fragments and malicious code in page content.

For example, a typical search engine echoes the user's query when displaying search results. What if the user tries to find the string "<script> alert (1) </script>"? Will the contents of the search results page lead to this script being executed, and will a dialog box with the message "1" appear? This depends on how well the web application developers verify user input and transform it into a safe format.

The main difficulty lies in the fact that users run a wide variety of browser versions, from the latest pre-alphas to ones that are no longer supported. Every browser handles web pages in a slightly different way. In some cases, an XSS attack can be quite successful when inputs are not sufficiently filtered. So the first step in an XSS attack is to determine how to embed user data on a web page.

## Infected Website

The second step is for the attacker to convince the user to visit a specific page. The attacker also needs to pass the attack vector to the page. Once again, there is nothing here that poses a serious obstacle. Websites often accept data as part of a URL. To implement the attack vector, attackers can use various social engineering or phishing methods.

The following example code displays just such a string (passed by the user in the HTTP request) in the server's response:

    
```js
protected void doGet(HttpServletRequest request, HttpServletResponse resp) {
    String firstName = request.getParameter("firstName");
    resp.getWriter().append("<div>");
    resp.getWriter().append("Search for " + firstName);
    resp.getWriter().append("</div>");
}
```
    

The code processes the value of the first URL parameter passed in the user's request. Then it displays the parameter on the resulting web page. The developer seemingly doesn't expect to see anything other than plain text without HTML tags in the firstName parameter. If the attacker sends the request "http://very.good.site/search?firstName= &lt;script&gt; alert ( 1) &lt;/script&gt;", the final page will look as follows:

    
```html
<div>
    Search for &lt;script&gt;alert(1)&lt;/script&gt;
</div>
```
    

You can easily check that when this HTML fragment is loaded onto a web page in the user's browser, the script passed in the firstName URL parameter is executed. In this case, malicious JavaScript is executed in the context of the vulnerable server. The script can therefore access the domain's cookie data, its API, and more. Of course, the attacker will develop the actual vector in a way that conceals their presence on the user-viewed page.

## Statistics

According to Positive Technologies analytics, XSS is among the three most common web application attacks. The relative percentage of XSS compared to other attack types has dipped in previous years. Still, there is no sign of XSS losing popularity.


Why is XSS still near the top of the list? Consider the number of vulnerable websites. As detailed in our 2019 report, more than two-thirds of tested websites had XSS vulnerabilities.


Sectors most commonly targeted by XSS are hospitality and entertainment (33%), finance (29%), education and science (29%), and transportation (26%). IT (16%) and government (16%) are also impacted, but not to the same extent.

## Types of XSS

Types of cross-site scripting attacks
Most XSS attacks can be divided into three categories:

Reflected (non-persistent). The carrier of the attack vector is the current client HTTP request. The server returns a response containing the attack vector. In essence, the server reflects the attack.

Stored (persistent). The attack vector is located on the server side. (We will talk about how exactly it gets there a bit later in this article.)

DOM-based XSS (Document Object Model). The attack vector is on the client side. Exploitation is possible primarily due to flaws in data processing inside JavaScript code.

A few other categories exist as well, although they are seen less frequently. They include:

Flash-based XSS. This vulnerability comes from insufficient processing of user input in Flash applications.

XSSI. Resources that are hosted on external domains and servers are vulnerable.
Browser vulnerabilities can also contribute to XSS risks, for example:

uXSS (Universal XSS). This vulnerability allows bypassing the SOP to execute JavaScript from one site on another.

mXSS (Mutation XSS). Attackers bypass filtering by putting an HTML payload into the DOM with "JavaScript ([element] .innerHTML =% value%" or "document.write (% value%))" in order to change it from safe to potentially dangerous.