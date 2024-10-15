---
id: CPTS
created_date: 2024-10-14
updated_date: 2024-10-14
type: note
tags:
---

# CPTS 327

## Web Security
HTTP - HyperText Transfer Protocol

Stateless by default. Forced to be stateful through cookies and session tokens. Cookies are containers for storing variable data on web browsers. Session tokens are identifiers that uniquely identify every authenticated session.

SQL (Structured Query Languages)

Used to view and manage data in a relational database. SQL injection (Improper Neutralization of Special Elements used in SQL command). Occurs due to improper or no sanitization of user input responses.

Cross Site Scripting (XSS)

Injecting malicious content into a web page. Malicious content can be set to execute at desired times using parameters.
Types:
- Stored: malicious content is stored in the web server and executes when user accesses the web server.
- Reflected: malicious script is included in a URL that user accesses.

XSS can be protected against from using input validation, encoding data, content security policy.

Same origin policy prevents scripts from modifying the DOM without permission. CSP prevents loading of malicious code.

Cross Site Request Forgery (CSRF), tricks users into executing a malicious script. Browsers allow the script execution since a legit user initiated the script.