> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Handling User Access**

## Handling User Access

A central security requirement that virtually any application needs to meet is controlling users’ access to its data and functionality. A typical situation has several different categories of user, such as anonymous users, ordinary authenticated users, and administrative users. Furthermore, in many situations different users are permitted to access a different set of data.
Most web applications handle access using a trio of interrelated security mechanisms:

### * Authentication
### * Session management
### * Access control

Each of these mechanisms represents a signifi cant area of an application’s attack surface, and each is fundamental to an application’s overall security posture. Because of their interdependencies, the overall security provided by the mechanisms is only as strong as the weakest link in the chain. A defect in any single component may enable an attacker to gain unrestricted access to the application’s functionality and data.

## Authentication

The authentication mechanism is logically the most basic dependency in an application’s handling of user access. Authenticating a user involves establishing that the user is in fact who he claims to be. Without this facility, the application would need to treat all users as anonymous — the lowest possible level of trust. The majority of today’s web applications employ the conventional authentication model, in which the user submits a username and password, which the application checks for validity.

## Session Management
The next logical task in the process of handling user access is to manage the authenticated user’s session. After successfully logging in to the application, the user accesses various pages and functions, making a series of HTTP requests from his browser. At the same time, the application receives countless other requests from different users, some of whom are authenticated and some of whom are anonymous. To enforce effective access control, the application needs a way to identify and process the series of requests that originate from each unique user.

Virtually all web applications meet this requirement by creating a session for each user and issuing the user a token that identifi es the session. The session itself is a set of data structures held on the server that track the state of the user’s interaction with the application. The token is a unique string that the application maps to the session. When a user receives a token, the browser automatically submits it back to the server in each subsequent HTTP request, enabling the application to associate the request with that user. HTTP cookies are the standard method for transmitting session tokens, although many applications use hidden form fi elds or the URL query string for this purpose. If a user does not make a request for a certain amount of time, the session is ideally expired, 

## Access Control
The final logical step in the process of handling user access is to make and enforce correct decisions about whether each individual request should be permitted or denied. If the mechanisms just described are functioning correctly, the application knows the identity of the user from whom each request is received. On this basis, it needs to decide whether that user is authorized to perform the action, or access the data, that he is requesting.

The access control mechanism usually needs to implement some fi ne-grained logic, with different considerations being relevant to different areas of the application and different types of functionality. An application might support numerous user roles, each involving different combinations of specific privileges. Individual users may be permitted to access a subset of the total data held within the application. Specifi c functions may implement transaction limits and other checks, all of which need to be properly enforced based on the user’s identity.

Because of the complex nature of typical access control requirements, this mechanism is a frequent source of security vulnerabilities that enable an attacker to gain unauthorized access to data and functionality. Developers often make  flawed assumptions about how users will interact with the application and frequently make oversights by omitting access control checks from some application functions. Probing for these vulnerabilities is often laborious, because essentially the same checks need to be repeated for each item of functionality. Because of the prevalence of access control fl aws, however, this effort is always a worthwhile investment when you are attacking a web application.

