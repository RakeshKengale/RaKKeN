> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Type of injection attack**


## Type of injection attack

Injections are amongst the oldest and most dangerous attacks aimed at web applications. They can lead to data theft, data loss, loss of data integrity, denial of service, as well as full system compromise. The primary reason for injection vulnerabilities is usually insufficient user input validation.

SQL injection (SQLi) and Cross-site Scripting (XSS) are the most common injection attacks but they are not the only ones. The following is a list of common injection attack types.


Injection attack | Description | Potential impact
------------ | ------------- | -------------
Code injection | The attacker injects application code written in the application language. This code may be used to execute operating system commands with the privileges of the user who is running the web application. In advanced cases, the attacker may exploit additional privilege escalation vulnerabilities, which may lead to full web server compromise. | Full system compromise
CRLF injection | The attacker injects an unexpected CRLF (Carriage Return and Line Feed) character sequence. This sequence is used to split an HTTP response header and write arbitrary contents to the response body. This attack may be combined with Cross-site Scripting (XSS). | Cross-site Scripting (XSS)
Cross-site Scripting (XSS) | The attacker injects an arbitrary script (usually in JavaScript) into a legitimate website or web application. This script is then executed inside the victim’s browser. | Account impersonation, Defacement, Run arbitrary JavaScript in the victim’s browser.
Email Header Injection | This attack is very similar to CRLF injections. The attacker sends IMAP/SMTP commands to a mail server that is not directly available via a web application. | Spam relay, Information disclosure.
Host Header Injection | The attacker abuses the implicit trust of the HTTP Host header to poison password-reset functionality and web caches. | Password-reset poisoning, Cache poisoning.
LDAP Injection | The attacker injects LDAP (Lightweight Directory Access Protocol) statements to execute arbitrary LDAP commands. They can gain permissions and modify the contents of the LDAP tree. | Authentication bypass, Privilege escalation, Information disclosure.
OS Command Injection | The attacker injects operating system commands with the privileges of the user who is running the web application. In advanced cases, the attacker may exploit additional privilege escalation vulnerabilities, which may lead to full system compromise. | Full system compromise
SQL Injection (SQLi) | The attacker injects SQL statements that can read or modify database data. In the case of advanced SQL Injection attacks, the attacker can use SQL commands to write arbitrary files to the server and even execute OS commands. This may lead to full system compromise. | Authentication bypass, Information disclosure,     Data loss, Sensitive data theft, Loss of data integrity, Denial of service, Full system compromise.
XPath injection | The attacker injects data into an application to execute crafted XPath queries. They can use them to access unauthorized data and bypass authentication. | Information disclosure, Authentication bypass.


## References

- [Injection Theory](https://owasp.org/www-community/Injection_Theory)
- [Injection Flaws](https://owasp.org/www-community/Injection_Flaws)
- [What Are Injection Attacks](https://www.acunetix.com/blog/articles/injection-attacks/)
- [Types of Injection Attacks](https://www.linkedin.com/pulse/types-injection-attacks-ria-pramanik)
