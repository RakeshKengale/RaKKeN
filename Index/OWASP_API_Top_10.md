
# OWASP API Security Top 10

The Open Web Application Security Project (OWASP) is a non-profit, collaborative online community behind the OWASP Top 10. They produce articles, methodologies, documentation, tools, and technologies to improve application security.
Since 2003, OWASP Top 10 project has been the authoritative list of information prevalent to web application vulnerabilities and the ways to mitigate them. However, the rise of the APIs has — and is — changing security landscape so fundamentally that a new approach is needed. As a result, in 2019, OWASP started an effort to create a version of their Top 10 dedicated specifically to API security. The first OWASP API Security Top 10 list was released on 31 December 2019.

API Security focuses on strategies and solutions to understand and mitigate the unique vulnerabilities and security risks of Application Programming Interfaces (APIs).

### API Security Top 10 2019
1. [Broken Object Level Authorization]()
2. [Broken User Authentication]()
3. [Excessive Data Exposure]()
4. [Lack of Resources & Rate Limiting]()
5. [Broken Function Level Authorization]()
6. [Mass Assignment]()
7. [Security Misconfiguration]()
8. [Injection]()
9. [Improper Assets Management]()
10. [Insufficient Logging & Monitoring]()


## 1. Broken Object Level Authorization
APIs tend to expose endpoints that handle object identifiers, creating a wide attack surface Level Access Control issue. Object level authorization checks should be considered in every function that accesses a data source using an input from the user.
APIs commonly track the identity of a particular user with a user ID embedded in the API request. While this is useful for quickly identifying a particular session, the embedded user ID should not be fully trusted.If an API fully trusts a user ID, then an attacker can substitute another user’s ID number in an API request. If the API does not maintain state on the server, this would enable the attacker to access the other user’s account.
Attackers substitute the ID of their own resource in the API call with an ID of a resource belonging to another user. The lack of proper authorization checks allows attackers to access the specified resource. This attack is also known as IDOR (Insecure Direct Object Reference).

### Use case

- API call parameters use the ID of the resource accessed through the API `/api/shop1/financial_info.`
- Attackers replace the IDs of their resources with a different one which they guessed through `/api/shop2/financial_info.`
- The API does not check permissions and lets the call through.
- Problem is aggravated if IDs can be enumerated `/api/123/financial_info.`

### How to prevent

- Implement authorization checks with user policies and hierarchy.
- Do not rely on IDs that the client sends. Use IDs stored in the session object instead.
- Check authorization for each client request to access database.
- Use random IDs that cannot be guessed (UUIDs).

## 2. Broken User Authentication
Authentication mechanisms are often implemented incorrectly, allowing attackers to compromise authentication tokens or to exploit implementation flaws to assume other user’s identities temporarily or permanently. Compromising system’s ability to identify the `client/user`, compromises API security overall.
Broken authentication APIs are designed to provide access to sensitive data or protected functionality. If an attacker can wrongly access an account on an API, they may be able to steal this data, use functionality that they should not be able to access or perform a denial-of-service (DoS) attack against the API. To protect against this, APIs commonly include authentication to ensure that the requestor is actually the owner of an account. However, authentication mechanisms can be complex, and a simple mistake can render them completely ineffective.
Poorly implemented API authentication allows attackers to assume other users’ identities.

### Use case

- Unprotected APIs that are considered “internal”
- Weak authentication that does not follow industry best practices
- Weak API keys that are not rotated
- Passwords that are weak, plain text, encrypted, poorly hashed, shared, or default passwords
- Authentication susceptible to brute force attacks and credential stuffing
- Credentials and keys included in URLs
- Lack of access token validation (including JWT validation)
- Unsigned or weakly signed non-expiring JWTs

### How to prevent

- Check all possible ways to authenticate to all APIs.
- APIs for password reset and one-time links also allow users to authenticate, and should be protected just as rigorously.
- Use standard authentication, token generation, password storage, and multi-factor authentication (MFA).
- Use short-lived access tokens.
- Authenticate your apps (so you know who is talking to you).
- Use stricter rate-limiting for authentication, and implement lockout policies and weak password checks.


## 3. Excessive Data Exposure
Looking forward to generic implementations, developers tend to expose all object properties without considering their individual sensitivity, relying on clients to perform the data filtering before displaying it to the user.
APIs are generally designed to expose data. The purpose of an API is to enable programmatic access to an organization’s online offerings, which enables bulk and low-latency operations with minimal overhead on the client or server side.However, many APIs go overboard on providing data to their clients. The assumption is that a client will perform all necessary filtering, so developers implement APIs using a generic model that does not take into account the possibility of sensitive data in the API response. As a result, someone eavesdropping on communications with an API may be able to extract sensitive data through simple traffic analysis.
The API may expose a lot more data than what the client legitimately needs, relying on the client to do the filtering. If attackers go directly to the API, they have it all.

### Use case

- The API returns full data objects as they are stored in the backend database.
- The client application filters the responses and only shows the data that the users really need to see.
- Attackers call the API directly and get also the sensitive data that the UI would filter out.

### How to prevent

- Never rely on the client to filter data!
- Review all API responses and adapt them to match what the API consumers really need.
- Carefully define schemas for all the API responses.
- Do not forget about error responses, define proper schemas as well.
- Identify all the sensitive data or Personally Identifiable Information (PII), and justify its use.
- Enforce response checks to prevent accidental leaks of data or exceptions.


## 4. Lack of Resources & Rate Limiting
Quite often, APIs do not impose any restrictions on the size or number of resources that can be requested by the client/user. Not only can this impact the API server performance, leading to Denial of Service (DoS), but also leaves the door open to authentication flaws such as brute force.
APIs are designed to support automated, programmatic access. This makes them extremely useful for repetitive activities and bulk operations.However, every request made to the API consumes valuable resources on the server side, including network bandwidth, CPU cycles, memory and storage. This makes the API potentially vulnerable to a DoS attack, where the attacker makes frequent, repeated or high-volume requests to consume limited resources. This vulnerability to a DoS attack can exist if the API owner sets rate limiting parameters (such as execution timeouts, request payload size and so on) too high or fails to set them at all.
The API is not protected against an excessive amount of calls or payload sizes. Attackers can use this for Denial of Service (DoS) and authentication flaws like brute force attacks.

### Use case

- Attackers overload the API by sending more requests than it can handle.
- Attackers send requests at a rate exceeding the API's processing speed, clogging it up.
- The size of the requests or some fields in them exceed what the API can process.
- “Zip bombs”, archive files that have been designed so that unpacking them takes excessive amount of resources and overloads the API.

### How to prevent

- Define proper rate limiting.
- Limit payload sizes.
- Tailor the rate limiting to be match what API methods, clients, or addresses need or should be allowed to get.
- Add checks on compression ratios.
- Define limits for container resources.


## 5. Broken Function Level Authorization
Complex access control policies with different hierarchies, groups, and roles, and an unclear separation between administrative and regular functions, tend to lead to authorization flaws. By exploiting these issues, attackers gain access to other users’ resources and/or administrative functions.
APIs are designed to do a variety of different things. Some APIs may have a single level of access for all users, while others may have protected functionality only accessible to administrators, “advanced” users and so on.Broken function level authorization is when an API fails to perform checks of an API user’s permissions before granting them access to protected functionality. For example, an API developer may only publicly document publicly available functions, assuming that users will only use these functions. However, if a user discovers and properly calls an administrator-level function, it will run for them. This failure to check permissions on a per-function level and reliance upon “security through obscurity” makes an API vulnerable to attack.
The API relies on the client to use user level or admin level APIs as appropriate. Attackers figure out the “hidden” admin API methods and invoke them directly.

### Use case

- Some administrative functions are exposed as APIs.
- Non-privileged users can access these functions without authorization if they know how.
- Can be a matter of knowing the URL, or using a different verb or a parameter:
- `/api/users/v1/user/myinfo`
- `/api/admins/v1/users/all`

### How to prevent

- Do not rely on the client to enforce admin access.
- Deny all access by default.
- Only allow operations to users belonging to the appropriate group or role.
- Properly design and test authorization.



## 6. Mass Assignment
Binding client provided data (e.g., JSON) to data models, without proper properties filtering based on a whitelist, usually lead to Mass Assignment. Either guessing objects properties, exploring other API endpoints, reading the documentation, or providing additional object properties in request payloads, allows attackers to modify object properties they are not supposed to.
APIs are often implemented in object-oriented programming languages, meaning that they contain object definitions that consist of a set of properties. In many cases, some of these properties are intended to be defined by a user while others are supposed to be set only by administrators. An issue exists if an API takes a set of user-provided property values and assigns them without checking to see if all of them should be user-controllable. If this is the case, an attacker who determines the underlying structure and business logic of an API’s objects can craft requests allowing them to set protected properties (such as user.is_admin).
The API takes data that client provides and stores it without proper filtering for whitelisted properties. Attackers can try to guess object properties or provide additional object properties in their requests, read the documentation, or check out API endpoints for clues where to find the openings to modify properties they are not supposed to on the data objects stored in the backend.

### Use case

- The API works with the data structures without proper filtering.
- Received payload is blindly transformed into an object and stored.
- NodeJS:
        `var user = new User(req.body);`
        `user.save();`
- Rails:
        `@user = User.new(params[:user])`
- Attackers can guess the fields by looking at the GET request data.

### How to prevent

- Do not automatically bind incoming data and internal objects.
- Explicitly define all the parameters and payloads you are expecting.
- Use the `readOnly` property set to `true` in object schemas for all properties that can be retrieved through APIs but should never be modified.
- Precisely define the schemas, types, and patterns you will accept in requests at design time and enforce them at runtime.


## 7. Security Misconfiguration
Security misconfiguration is commonly a result of unsecure default configurations, incomplete or ad-hoc configurations, open cloud storage, misconfigured HTTP headers, unnecessary HTTP methods, permissive Cross-Origin resource sharing (CORS), and verbose error messages containing sensitive information.
APIs are a common target of cybercriminals since they are usually extremely powerful and exposed to the public internet. As a result, any vulnerability in any component of the API’s infrastructure can be a potential attack vector.Failing to properly patch software and endpoints, set permissions on files and so on can give a determined attacker an opening to exploit an organization. Even if an API has all of the patches for known vulnerabilities applied, fuzzing attacks may identify exploitable flaws in the API’s code itself.
Poor configuration of the API servers allows attackers to exploit them.

### Use case

- Unpatched systems
- Unprotected files and directories
- Unhardened images
- Missing, outdated, or misconfigured TLS
- Exposed storage or server management panels
- Missing CORS policy or security headers
- Error messages with stack traces
- Unnecessary features enabled

### How to prevent

- Establish repeatable hardening and patching processes.
- Automate locating configuration flaws.
- Disable unnecessary features.
- Restrict administrative access.
- Define and enforce all outputs, including errors.


## 8. Injection
Injection flaws, such as SQL, NoSQL, Command Injection, etc., occur when untrusted data is sent to an interpreter as part of a command or query. The attacker’s malicious data can trick the interpreter into executing unintended commands or accessing data without proper authorization.
Injection vulnerabilities are some of the most well-known and common vulnerabilities in existence. They rank at the top of the 2017 OWASP top ten list for web application vulnerabilities and third in the 2019 CWE Top 25 Most Dangerous Software Errors list.Injection vulnerabilities exist because many programming languages mix user-provided data and developer-provided code together into a single command. If the developer doesn’t properly sanitize user input, a malicious user can get their data to be interpreted and executed as code. Since APIs take and process user-provided input, they are vulnerable to injection attacks as well.
Attackers construct API calls that include SQL, NoSQL, LDAP, OS, or other commands that the API or the backend behind it blindly executes.

### Use cases

- Attackers send malicious input to be forwarded to an internal interpreter:
  - SQL
  - NoSQL
  - LDAP
  - OS commands
  - XML parsers
  - Object-Relational Mapping (ORM)

### How to prevent

- Never trust your API consumers, even if they are internal.
- Strictly define all input data, such as schemas, types, and string patterns, and enforce them at runtime.
- Validate, filter, and sanitize all incoming data.
- Define, limit, and enforce API outputs to prevent data leaks.


## 9. Improper Assets Management
APIs tend to expose more endpoints than traditional web applications, making proper and updated documentation highly important. Proper hosts and deployed API versions inventory also play an important role to mitigate issues such as deprecated API versions and exposed debug endpoints.
The ninth vulnerability on the OWASP Top Ten API Security list refers to a failure to properly track API-related assets throughout their life cycle. As code moves through the development process and the production environment evolves, the purposes of different systems and code can change. If these changes are not tracked, then the system can become vulnerable.For example, an endpoint that an API accesses may become deprecated in a new API version, but it might not be officially removed. If this problem is overlooked, connections to the deprecated system may no longer be monitored or secured.
Attackers find non-production versions of the API (for example, staging, testing, beta, or earlier versions) that are not as well protected as the production API, and use those to launch their attacks.

### Use case

- DevOps, the cloud, containers, and Kubernetes make having multiple deployments easy (for example, dev, test, branches, staging, old versions).
- Desire to maintain backward compatibility forces to leave old APIs running.
- Old or non-production versions are not properly maintained, but these endpoints still have access to production data.
- Once authenticated with one endpoint, attackers may switch to the other, production one.

### How to prevent

- Keep an up-to-date inventory all API hosts.
- Limit access to anything that should not be public.
- Limit access to production data, and segregate access to production and non-production data.
- Implement additional external controls, such as API firewalls.
- Properly retire old versions of APIs or backport security fixes to them.
- Implement strict authentication, redirects, CORS, and so forth.


## 10. Insufficient Logging & Monitoring
Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems to tamper with, extract, or destroy data. Most breach studies demonstrate the time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring.
As in every other environment, API security should not be “fire and forget.” Acquiring and deploying state-of-the-art cybersecurity solutions is of limited value if no one is monitoring them to determine if they have detected anything of interest. API security systems should be constantly monitored, just like the rest of the organization’s cybersecurity infrastructure, to ensure that they are not undergoing an attack.
Lack of proper logging, monitoring, and alerting allows attacks and attackers go unnoticed.

### Use case

- Logs are not protected for integrity.
- Logs are not integrated into Security Information and Event Management (SIEM) systems.
- Logs and alerts are poorly designed.
- Companies rely on manual rather than automated systems.

### How to prevent

- Log failed attempts, denied access, input validation failures, or any failures in security policy checks.
- Ensure that logs are formatted so that other tools can consume them as well.
- Protect logs like highly sensitive information.
- Include enough detail to identify attackers.
- Avoid having sensitive data in logs — if you need the information for debugging purposes, redact it partially.
- Integrate with SIEMs and other dashboards, monitoring, and alerting tools.

