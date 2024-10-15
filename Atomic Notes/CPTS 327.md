---
id: CPTS
created_date: 2024-10-14
updated_date: 2024-10-14
type: note
tags:
---

# CPTS 327

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

One time pad cipher
- A key that is used once and not more.
Substitution Cipher
- plain text substituted with cipher text using a key shift. Weak due to a small number of possible keys.
Transposition Cipher
- Cipher text is a permutation of plain text. Shuffling is key.

A logic bomb is a malicious piece of code inserted into software that is set off when certain conditions are met.

A race condition attack exploits a race condition with malicious code or data to gain unauthorized access to a system or data.

Mandatory access control restricts the ability of an individual resource to grant or deny access to resource objects in a file system. Permissions cannot be altered by end users.

Role based access control gives access to information necessary based on the role of a user in an organization.

Discretionary access control gives end users the ability to give and take away permissions for resources.

A backdoor is a attack to sidestep normal authentication procedures to gain unauthorized access to a system.

TLS (transport layer security) provides communications security over a network using asymmetric encryption to encrypt a session key and then using symmetric encryption to encrypt and decrypt data.

Asymmetric encryption is where the sender and recipient use two different keys, also known as public key encryption.