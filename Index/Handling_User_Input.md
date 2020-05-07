> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Handling User Input**

## Handling User Input

- [Varieties of Input](Handling_User_Input.md#varieties-of-input) 
- [Approaches to Input Handling](Handling_User_Input.md#approaches-to-input-handling) 
- [Boundary Validation](Handling_User_Input.md#boundary-validation) 
- [Multistep Validation and Canonicalization](Handling_User_Input.md#multistep-validation-and-canonicalization)

All user input is untrusted. A huge variety of attacks against web applications involve submitting unexpected input, crafted to cause behavior that was not intended by the application’s designers. Correspondingly, a key requirement for an application’s security defenses is that the application must handle user input in a safe manner. Input-based vulnerabilities can arise anywhere within an application’s functionality, and in relation to practically every type of technology in common use. `Input validation` is often cited as the necessary defense against these attacks. However, no single protective mechanism can be employed everywhere, and defending against malicious input is often not as straightforward as it sounds. 

## Varieties of Input

A typical web application processes user-supplied data in many different forms. Some kinds of input validation may not be feasible or desirable for all these forms of input. In many cases, an application may be able to impose very stringent validation checks on a specific item of input. 

__For example,__ 

A username submitted to a login function may be required to have a maximum length of `eight` characters and contain only `alphabetical` characters.
In other cases, the application must tolerate a wider range of possible input. 

__For example,__

An address field submitted to a personal details page might legitimately contain letters, numbers, spaces, hyphens, apostrophes, and other characters. However, for this item, restrictions still can be feasibly imposed. The data should not exceed a reasonable length limit (such as 50 characters) and should not contain any HTML markup.
In some situations, an application may need to accept arbitrary input from users.

__For example,__ 

A user of a blogging application may create a blog whose subject is web application hacking. Posts and comments made to the blog may quite legitimately contain explicit attack strings that are being discussed. The application may need to store this input in a database, write it to disk, and display it back to users in a safe way. It cannot simply reject the input just because it looks potentially malicious without substantially diminishing the application’s value to some of its user base.

## Approaches to Input Handling
Various broad approaches are commonly taken to the problem of handling user input. Different approaches are often preferable for different situations and different types of input, and a combination of approaches may sometimes be desirable.

- [Reject Known Bad (Blacklist)](Handling_User_Input.md#reject-known-bad-blacklist)
- [Accept Known Good (Whitelist)](Handling_User_Input.md#accept-known-good-whitelist)
- [Sanitization](Handling_User_Input.md#sanitization)
- [Safe Data Handling](Handling_User_Input.md#safe-data-handling)
- [Semantic Checks](Handling_User_Input.md#semantic-checks)
- [Boundary Validation](Handling_User_Input.md#boundary-validation)


## Reject Known Bad (Blacklist)

This approach typically employs a blacklist containing a set of literal strings or patterns that are known to be used in attacks. The validation mechanism blocks any data that matches the blacklist and allows everything else.

In general, this is regarded as the least effective approach to validating user input, for two main reasons. 

First, a typical vulnerability in a web application can be exploited using a wide variety of input, which may be encoded or represented in various ways. Except in the simplest of cases, it is likely that a blacklist will omit some patterns of input that can be used to attack the application. 

Second, techniques for exploitation are constantly evolving. Novel methods for exploiting existing categories of vulnerabilities are unlikely to be blocked by current blacklists. 

Many blacklist-based filters can be bypassed with almost embarrassing ease by making trivial adjustments to the input that is being blocked. 

__For example:__

`If SELECT is blocked, try SeLeCt`

`If or 1=1-- is blocked, try or 2=2--`

`If alert(‘xss’) is blocked, try prompt(‘xss’)`

In other cases, filters designed to block specific keywords can be bypassed by using nonstandard characters between expressions to disrupt the tokenizing performed by the application. 

__For example:__

`SELECT/*foo*/username,password/*foo*/FROM/*foo*/users`

`<img%09onerror=alert(1) src=a>`

Finally, numerous blacklist-based filters, particularly those implemented in web application firewalls, have been vulnerable to NULL byte attacks. Because of the different ways in which strings are handled in managed and unmanaged execution contexts, inserting a NULL byte anywhere before a blocked expression can cause some filters to stop processing the input and therefore not identify the expression. 

__For example:__

`%00<script>alert(1)</script>`

> Attacks that exploit the handling of NULL bytes arise in many areas of web application security. In contexts where a NULL byte acts as a string delimiter, it can be used to terminate a filename or a query to some backend component. In contexts where NULL bytes are tolerated and ignored (for example, within HTML in some browsers), arbitrary NULL bytes can be inserted within blocked expressions to defeat some blacklist-based filters.


## Accept Known Good (Whitelist)

This approach employs a whitelist containing a set of literal strings or patterns, or a set of criteria, that is known to match only benign input. The validation mechanism allows data that matches the whitelist and blocks everything else. 

__For example,__ 

Before looking up a requested product code in the database, an application might validate that it contains only alphanumeric characters and is exactly six characters long. Given the subsequent processing that will be done on the product code, the developers know that input passing this test cannot possibly cause any problems.

In cases where this approach is feasible, it is regarded as the most effective way to handle potentially malicious input. Provided that due care is taken in constructing the whitelist, an attacker will be unable to use crafted input to interfere with the application’s behavior. However, in numerous situations an application must accept data for processing that does not meet any reasonable criteria for what is known to be `good.` 

__For example,__ 

some people’s names contain an apostrophe or hyphen. These can be used in attacks against databases, but it may be a requirement that the application should permit anyone to register under his or her real name. Hence, although it is often extremely effective, the whitelist-based approach does not represent an all-purpose solution to the problem of handling user input.

## Sanitization

This approach recognizes the need to sometimes accept data that cannot be guaranteed as safe. Instead of rejecting this input, the application sanitizes it in various ways to prevent it from having any adverse effects. Potentially malicious characters may be removed from the data, leaving only what is known to be safe, or they may be suitably encoded or `escaped` before further processing is performed.

Approaches based on data sanitization are often highly effective, and in many situations they can be relied on as a general solution to the problem of malicious input. 

__For example,__ 

The usual defense against cross-site scripting attacks is to HTML-encode dangerous characters before these are embedded into pages of the application. 

## Safe Data Handling

Many web application vulnerabilities arise because user-supplied data is processed in unsafe ways. Vulnerabilities often can be avoided not by validating the input itself but by ensuring that the processing that is performed on it is inherently safe. In some situations, safe programming methods are available that avoid common problems. 

__For example,__ 

__SQL injection__ attacks can be prevented through the correct use of parameterized queries for database access. 
In other situations, application functionality can be designed in such a way that inherently unsafe practices, such as passing user input to an operating system command interpreter, are avoided. This approach cannot be applied to every kind of task that web applications need to perform. But where it is available, it is an effective general approach to handling potentially malicious input.

## Semantic Checks

The defenses described so far all address the need to defend the application against various kinds of malformed data whose content has been crafted to interfere with the application’s processing. However, with some vulnerabilities the input supplied by the attacker is identical to the input that an ordinary, nonmalicious user may submit. What makes it malicious is the different circumstances under which it is submitted. 

__For example,__

An attacker might seek to gain access to another user’s bank account by changing an account number transmitted in a hidden form field. No amount of syntactic validation will distinguish between the user’s data and the attacker’s. To prevent unauthorized access, the application needs to validate that the account number submitted belongs to the user who has submitted it.


## Boundary Validation

The idea of validating data across trust boundaries is a familiar one. The core security problem with web applications arises because data received from users is untrusted. Although input validation checks implemented on the client side may improve performance and the user’s experience, they do not provide any assurance about the data that actually reaches the server. The point at which user data is first received by the server-side application represents a huge trust boundary. At this point the application needs to take measures to defend itself against malicious input.
Given the nature of the core problem, it is tempting to think of the input validation problem in terms of a frontier between the Internet, which is `bad` and `untrusted`, and the server-side application, which is `good` and `trusted`. In this picture, the role of input validation is to clean potentially malicious data on arrival and then pass the clean data to the trusted application. From this point onward, the data may be trusted and processed without any further checks or concern about possible attacks.

where boundary validation is the most effective approach to defending against malicious input. The user login results in several steps of processing being performed on user-supplied input, and suitable validation is performed at each step:

1. The application receives the user’s login details. The form handler validates that each item of input contains only permitted characters, is within a specific length limit, and does not contain any known attack signatures.

2. The application performs a SQL query to verify the user’s credentials. To prevent SQL injection attacks, any characters within the user input that may be used to attack the database are escaped before the query is constructed.

3. If the login succeeds, the application passes certain data from the user’s profile to a SOAP service to retrieve further information about her account. To prevent SOAP injection attacks, any XML metacharacters within the user’s profile data are suitably encoded.

4. The application displays the user’s account information back to the user’s browser. To prevent cross-site scripting attacks, the application HTMLencodes any user-supplied data that is embedded into the returned page.

![SQL_Query_To_Verify_The_User’s_Credentials](Images/SQL_Query_To_Verify_The_User%E2%80%99s_Credentials.png)

If variations on this functionality involved passing data to further application components, similar defenses would need to be implemented at the relevant trust boundaries. 

__For example,__ 

If a failed login caused the application to send a warning e-mail to the user, any user data incorporated into the e-mail may need to be checked for SMTP injection attacks.


## Multistep Validation and Canonicalization
A common problem encountered by input-handling mechanisms arises when user-supplied input is manipulated across several steps as part of the validation logic. If this process is not handled carefully, an attacker may be able to construct crafted input that succeeds in smuggling malicious data through the validation mechanism. One version of this problem occurs when an application attempts to sanitize user input by removing or encoding certain characters or expressions. 

__For example,__ 

an application may attempt to defend against some cross-site scripting attacks by stripping the expression:

`<script>`

from any user-supplied data. However, an attacker may be able to bypass the filter by supplying the following input:

`<scr<script>ipt>`

When the blocked expression is removed, the surrounding data contracts to restore the malicious payload, because the filter is not being applied recursively. Similarly, if more than one validation step is performed on user input, an attacker may be able to exploit the ordering of these steps to bypass the filter.

__For example,__ 

if the application first removes `../` recursively and then removes `..\` recursively, 
the following input can be used to defeat the validation: 
`....\/`

A related problem arises in relation to data canonicalization. When input is sent from the user’s browser, it may be encoded in various ways. These encoding schemes exist so that unusual characters and binary data may be transmitted safely over HTTP. 
Canonicalization is the process of converting or decoding data into a common character set. If any canonicalization is carried out after input filters have been applied, an attacker may be able to use a suitable encoding scheme to bypass the validation mechanism.

__For example,__ 

an application may attempt to defend against some SQL injection attacks by blocking input containing the apostrophe character. 
However, if the input is subsequently canonicalized, an attacker may be able to use double URL encoding to defeat the filter. 

__For example:__

`%2527`

When this input is received, the application server performs its normal URL decode, so the input becomes:

`%27`

This does not contain an apostrophe, so it is permitted by the application’s filters. But when the application performs a further URL decode, the input is converted into an apostrophe, thereby bypassing the filter. If the application strips the apostrophe instead of blocking it, and then performs further canonicalization, the following bypass may be effective:

`%%2727`

It is worth noting that the multiple validation and canonicalization steps in these cases need not all take place on the server side of the application. 

__For example,__ 

in the following input several characters have been HTML-encoded:

`<iframe src=j&#x61;vasc&#x72ipt&#x3a;alert&#x28;1&#x29; >`

If the server-side application uses an input filter to block certain JavaScript expressions and characters, the encoded input may succeed in bypassing the filter. However, if the input is then copied into the application’s response, some browsers perform an HTML decode of the `src` parameter value, and the embedded JavaScript executes.

In addition to the standard encoding schemes that are intended for use in web applications, canonicalization issues can arise in other situations where a component employed by the application converts data from one character set to another. 

__For example,__ 

some technologies perform a __best fit__ mapping of characters based on similarities in their printed glyphs. Here, the characters `«` and `»` may be converted into `<` and `>`, respectively, and `Ÿ` and `Â` are converted into `Y` and `A`. This behavior can often be leveraged to smuggle blocked characters or keywords past an application’s input filters. 

Avoiding problems with multistep validation and canonicalization can sometimes be difficult, and there is no single solution to the problem. One approach is to perform sanitization steps recursively, continuing until no further modifications have been made on an item of input. However, where the desired sanitization involves escaping a problematic character, this may result in an infinite loop. Often, the problem can be addressed only on a case-by-case basis, based on the types of validation being performed. Where feasible, it may be preferable to avoid attempting to clean some kinds of bad input, and simply reject it altogether.
