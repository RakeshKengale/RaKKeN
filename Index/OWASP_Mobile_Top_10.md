> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  OWASP Top 10 - Mobile (2016)**


## OWASP Top 10 - Mobile - (2016)

1. [Improper Platform Usage](OWASP_Mobile_Top_10.md#m1-improper-platform-usage)
2. [Insecure Data Storage](OWASP_Mobile_Top_10.md#m2-insecure-data-storage)
3. [Insecure Communication](OWASP_Mobile_Top_10.md#m3-insecure-communication)
4. [Insecure Authentication](OWASP_Mobile_Top_10.md#m4-insecure-authentication)
5. [Insufficient Cryptography](OWASP_Mobile_Top_10.md#m5-insufficient-cryptography)
6. [Insecure Authorization](OWASP_Mobile_Top_10.md#m5-insufficient-cryptography)
7. [Poor Code Quality](OWASP_Mobile_Top_10.md#m5-insufficient-cryptography)
8. [Code Tampering](OWASP_Mobile_Top_10.md#m8-code-tampering)
9. [Reverse Engineering](OWASP_Mobile_Top_10.md#m9-reverse-engineering)
10. [Extraneous Functionality](OWASP_Mobile_Top_10.md#m10-extraneous-functionality)


## M1. Improper Platform Usage
This risk covers the misuse of an operating system feature or a failure to use platform security controls properly. This may include Android intents, platform permissions, the Keychain, or other security controls that are part of the platform. Its occurrence is common, with average detectability, and can cause a severe impact on the affected apps.

### Might include:

- android intents,
- platform permissions,
- misuse of TouchID,
- misuse the Keychain,
- misuse of other security controls.

### Improper Platform Usage Risks 
- Data Leakage by Exploiting Android Intent
- Android Intent Sniffing
- iOS Keychain Risk
- iOS TouchID Risk

### Best Practices to Avoid Improper Platform Usage
 
### iOS Keychain Best Practices

Do not allow Keychain encryptions through the server route and instead keep the encrypted keys in one device only, so that it cannot be exploited in other devices or the server.
Secure the app by using the Keychain to store the app’s secret which should have a dedicated access control list. The user authentication policy of the access control list can be enforced by the OS.

### iOS Android Intent Best Practices

Take the permission route to restrict which apps are allowed to communicate with their app, thus practically blocking all attempts from non-whitelisted traffic. Another option is to not allow an export option for intents for either or all of the activities, services and broadcast receivers with the Android framework so that Android components that have no reason to communicate with the app are kept at the outset.

### Android Intent Sniffing Best Practices

This leakage can be controlled by defining explicit intents, where the intent object is clearly defined, thus blocking every other component to access the information contained in the intent. Also, check file permissions thoroughly before making the app public to ensure the required permissions are in place.



## M2. Insecure Data Storage
Threats agents include the following: an adversary that has attained a lost/stolen mobile device; malware or another repackaged app acting on the adversary’s behalf that executes on the mobile device.

### Might include:

- Wrong keychain accessibility option, (f. ex. kSecAttrAccessibleWhenUnlocked vs. kSecAttrAccessibleAlways)
- Insufficient file data protection, (f. ex. NSFileProtectionNone vs NSFileProtectionComplete)
- Access to privacy resources when using this data incorrectly.

### Insecure Data Storage Risks
- Compromised File System
- The exploitation of Unsecured Data

### Best Practices to Avoid Insecure Data Storage

### iGoat iOS

For iOS devices, the OWASP recommends using purposefully vulnerable mobile apps, like iGoat, to threat model their apps and development frameworks. This process allows developers to understand how APIs deal with information assets and app processes, like URL caching, key-press caching, buffer caching, Keychain usage, application backgrounding, logging, data storage, browser cookie management, server communication, and traffic sent to third parties.

### Android Debug Bridge

Android developers can use Android Debug Bridge (ADB) shell to check file permissions of the targeted app and a database management system, like sqlite3, to check database encryption. ADB also offers commands like ‘logcat’ to allow developers to check error logs contained in Android logs, which can leak sensitive user or security information to a malware. While it is common knowledge that extensive error logs help developers during the development process, but if left unattended, these logs can lead to a compromised app or data. An Android developer should also use tools like Android Device Monitor and Memory Analysis Tool to ensure that the device’s memory does not have an unintended data for an unspecified duration, which could be exploited by a hacker or unauthorized person who can obtain physical access of the device. 

## M3. Insecure Communication
When designing a mobile application, data is commonly exchanged in a client-server fashion. When the solution transmits its data, it must traverse the mobile device’s carrier network and the internet. Threat agents might exploit vulnerabilities to intercept sensitive data while it’s traveling across the wire. The following threat agents exist:

- An adversary that shares your local network (compromised or monitored Wi-Fi);
- Carrier or network devices (routers, cell towers, proxy’s, etc); or
- Malware on your mobile device.

Data transmission to and from a mobile app generally takes place through a telecom carrier and/or over the internet. Hackers intercept data either as an adversary sitting in the local area network of users through a compromised Wi-Fi network, tapping into the network through routers, cellular towers, proxy servers, or exploiting the infected app through a malware.

### Might include:

- Poor handshaking/weak negotiation, (f. ex. lack of certificate pinning)
- Incorrect SSL versions,
- Cleartext communication of sensitive assets,
- HTTP instead of HTTPS.

### Insecure Communication Risks
- Stealing of Information
- Man in The Middle (MITM) Attacks
- Admin Account Compromise

### Best Practices to Avoid Insecure Communication

Developers should incorporate the following suggestions from the OWASP to address insecure communication:

- Assume that the network layer is not secure and is susceptible to eavesdropping
- Watch out for leakages over the traffic communicated between an app and the server. Also check the device that holds the app and another local device or a local network, including wired networks
- Apply SSL/TLS to transport channels that the mobile app will use to transmit sensitive information, session tokens, or other sensitive data to a backend API or web service
- Account for outside entities like third-party analytics companies, social networks, etc. by using their SSL versions when an application runs a routine via the browser/webkit. 
- Avoid mixed SSL sessions as they may expose the user’s session ID
- Use strong, industry-standard cipher suites with appropriate key lengths
- Use certificates signed by a trusted CA provider
- Establish a secure connection only after verifying the identity of the endpoint server using trusted certificates in the key chain
- Alert users through the UI if the mobile app detects an invalid certificate
- Do not send sensitive data over alternate channels (e.g, SMS, MMS, or notifications) 
- If possible, apply a separate layer of encryption to any sensitive data before it is given to the SSL channel. In the event that future vulnerabilities are discovered in the SSL implementation, the encrypted data will provide a secondary defense against confidentiality violation


## M4. Insecure Authentication
Threat agents that exploit authentication vulnerabilities typically do so through automated attacks that use available or custom-built tools.

This problem occurs when a mobile device fails to recognize the user correctly and allows an adversary to log into the app with default credentials. This typically happens when an attacker fakes or bypasses the authentication protocols, which are either missing or poorly implemented, and interacts directly with the server using either malware which sits in the mobile device or botnets, thus establishing no direct communication with the app.

### Might include:

- Failing to identify the user at all when that should be required,
- Failure to maintain the user’s identity when it is required,
- Weaknesses in session management.

### Insecure Authentication Risks
- Input Form Factor
- Insecure User Credentials

### Best Practices to Avoid Insecure Authentication

Carefully study the authentication scheme of the app and test it with binary attacks in offline mode to determine if it can be potentially exploited. The security team should check if the app is letting a POST/GET command be executed to establish a connection with the server without an access token. A successful connection establishes vulnerabilities in the app. The developer should ensure that passwords and security keys are not stored locally on the mobile device. Such data is extremely prone to manipulation.

The security team should try to implement as many of the following methods to secure the mobile app from insecure authentication:

- The security protocols of the web app should match those of the mobile app in terms of complexity and authentication methods;
- Use online authentication methods, just as in a web browser. If the ease of access takes precedence in a mobile device, try to guard against binary attacks, which are described in detail in M10 risk;
- Do not allow the loading of app data unless the server has authenticated a user session. Storing app data locally can create faster loading, but it can compromise on user security;
- Wherever local storage of data becomes an eventuality, make sure that it is encrypted with an encrypted key derived from the login credentials of the user, thus forcing the app to authenticate the app data at least once;
- Persistent authentication requests should be stored on the server and not locally. Always remember to caution the user when they opt-in for the remember-me option;
- The security team needs to be careful with using device-centric authorization tokens in the app since a stolen device app becomes vulnerable. A device-centric authorization token for an app ensures that the app cannot be accessed if the new owner of the device changes the device access password;
- Since unauthorized physical access of mobile devices is common, the security team should enforce periodic authentication of user credentials and logouts from the server-side; 
- Make sure that the user is forced to choose alphanumeric characters for passwords. They are more secure than simple letter combinations. Alongside this, the developer can force the user to identify an image or word before allowing access to the app. The two-factor authentication method is fast gaining currency. 


## M5. Insufficient Cryptography
Cryptography was attemted, but insufficient in some way. For example developer might have used an outdated cryptographic algorithm or written a custom vulnerable algorithm.
Threat agents include the following: anyone with physical access to data that has been encrypted improperly, or mobile malware acting on an adversary’s behalf.

Data in mobile apps become vulnerable due to weak encryption/decryption processes or infirmities in the algorithms that trigger encryption/decryption processes. Hackers can gain physical access to the mobile device, spy on network traffic, or use malicious apps in the device to access encrypted data. Using flaws in the encryption process, its aim is to decrypt data to its original form in order to steal it or encrypt it using an adversarial process and thus render it useless for the legitimate user.

### Insufficient Cryptography Risks
- Stealing App and User Data
- Access Encrypted Files

### Best Practices to Avoid Insufficient Cryptography

- Choose modern encryption algorithms to encrypt apps. The choice of the algorithm takes care of this vulnerability to a large extent, as an encryption algorithm from a trusted source generally is tested by the security community frequently
- The National Institute of Standards and Technology of the US government publishes cryptographic standards from time to time and recommends encryption algorithms. The developer should keep an eye on this document to watch out for emerging threats.



## M6. Insecure Authorization
Threat agents that exploit authorization vulnerabilities typically do so through automated attacks that use available or custom-built tools.

Many people confuse the M4 risk with M6 risk since both of them are about user credentials. Developers should keep in mind that insecure authorization involves the adversary taking advantage of vulnerabilities in the authorization process to log in as a legitimate user, unlike insecure authentication, in which the adversary tries to bypass the authentication process by logging in as an anonymous user.

### Insecure Authorization Risks
- Unregulated Access to Admin Endpoints
- IDOR Access

### Might include:

- Failures in authorization,(e.g., authorization decisions in the client side, forced browsing, etc.)
- Able to execute over-privileged functionality.

### Best Practices to Avoid Insecure Authorization

- Continuously test user privileges by running low-privilege session tokens for sensitive commands, which are reserved for high-privilege users. If commands can be executed successfully, immediately check the authorization scheme of the app
- Developers should keep in mind that the user authorization scheme usually goes wrong in offline mode. However, in certain cases developers allow user permissions and roles to be sent to the server, which can also cause vulnerability in the authorization scheme.
- Run authorization checks for roles and permissions of an authenticated user at the server rather than from the mobile device. The chances of authentic users exploiting high-privilege functionalities reduce in the backend verified user management schemes rather than when they are verified within the mobile device.




## M7. Poor Code Quality
Threat Agents include entities that can pass untrusted inputs to method calls made within mobile code. These types of issues are not necessarily security issues in and of themselves but lead to security vulnerabilities. For example, buffer overflows within older versions of Safari (a poor code quality vulnerability) led to high risk drive-by Jailbreak attacks. Poor code-quality issues are typically exploited via malware or phishing scams.

The M7 risk emerges from poor or inconsistent coding practices, where each member of the development team follows a different coding practice and creates inconsistencies in the final code or does not create enough documentation for others to follow. The saving grace for developers here is that even if the prevalence of this risk is common, its detectability is low. Hackers cannot easily study the patterns of poor coding and often require manual analysis, which is not easy to do. Automatic tools, which are employed to identify memory leaks or buffer overflows using fuzz testing, can help access information but do not easily allow the execution of foreign code in the mobile device.


### Poor Code Quality Risks
- Safe Web Code, Compromised in Mobiles
- Lacunae in Third-Party Libraries
- Client Input Insecurity


### Might include:

- Buffer overflows,
- Format string vulnerabilities,
- Various other code-level mistakes where the solution is to rewrite some code that’s running on the mobile device.

### Best Practices to Avoid Poor Code Quality

### Mobile-Specific Code

The simplest solution to fix this issue is to rewrite code in the mobile device rather than looking to fix problems at the server-side. Developers should keep in mind that poor coding at the server level is different from the one at the client-side. A code issue at the server side will reflect in the web view of the app too, but the mobile-side bad coding will impact only the mobile user.

### Static Analysis

The developer should consistently use third-party tools for static analysis to identify memory leaks and buffer overflows. The development team should try to eradicate the mismatch between the length of incoming buffer data and the target buffer.

### Code Logic 

The developer should avoid simple logic in codes, as it is known to be hackers’ favorite both in iOS and Android devices. Hackers can change a value in the code with simple logic and circumvent the whole security apparatus. Such codes can be attacked at assembly and runtime levels. The developer could control this leakage by stopping untrusted sessions from enforcing privileges at the device level and instead activate them at the server. It is also recommended to withhold the permissions until a session has been authenticated using OTP, secret questions, or challenges.

### Library Version

The development team should create a list of all third-party libraries used in the app and check for their newer versions periodically, even if it has used libraries only from trusted sources.

### Content Provider

Developers should consider all client input to be untrusted and validate it irrespective of whether it comes from the app or the user. They should carefully set permission flags on content provider inputs to stop all unauthorized access.

## M8. Code Tampering
Typically, an attacker will exploit code modification via malicious forms of the apps hosted in third-party app stores. The attacker may also trick the user into installing the app via phishing attacks.

Hackers prefer code tampering of apps over other forms of manipulations, as it allows them to gain unbridled access to the app, the user behavior, or even the whole mobile device. They tend to push users to download tampered versions of popular apps from third-party app stores through phishing attacks and misleading advertisements. 

### Code Tampering Risks
- Malware Infusion
- Data Theft


### Might include:

- Binary patching,
- Local resource modification,
- Method hooking and swizzling,
- Dynamic memory modification.

### Best Practices to Avoid Code Tampering

### Runtime Detection

The developer should ensure that the app can detect code change at runtime. If a tampered app wants to run in a rooted or jailbroken device and the developer does not wish to allow this kind of execution, it is best to report this compromise to the server at runtime itself. RASP is one such technology that developers can use to detect and deter attack vectors in real-time.

### Checksum Changes

The developer should use checksums and evaluate digital signatures to see if file tampering has taken place. Since code and file tampering almost always changes the checksum value, it is the easiest way to determine adversarial action.

### Data Erasure

Ensure that the app code, keys, and data are erased once tampering has been detected. Such a provision will destroy the very rationale of tampering and discourage hackers from targeting the same app again.



## M9. Reverse Engineering
An attacker will typically download the targeted app from an app store and analyze it within their own local environment using a suite of different tools.
Reverse engineering of mobile code is a commonly exploitable occurrence. Hackers tend to use external, commonly available binary inspection tools, like IDA Pro, Hopper, otool, etc., to study the original app’s code patterns and its links with server processes.

### Might include analysis of the final core binary to determine its

- Source code,
- Libraries,
- Algorithms and other assets.

Reverse engineering makes it easier to exploit other vulnerabilities in the application. It can reveal information about backend servers, cryptographic constants and ciphers, and intellectual property.

### Reverse Engineering Risks
- Dynamic Inspection at Runtime
- Code Stealing
- Premium Features


### Best Practices to Avoid Reverse Engineering

### Use Similar Tools

The best way to secure an app against reverse engineering is to use the same tools that hackers use to attempt reverse engineering. If these tools can easily analyze the app’s string tables, control flow path, interactions with servers, cryptographic constants and ciphers, metadata, etc., the code stands compromised. Developers can also use a tool like AppSealing to detect attempts at reverse engineering in real-time.

### Code Obfuscation

The obfuscation process should entail targeting specific segments of the source code, string tables, and methods that least impact code performance. The developer should ensure that the level of obfuscation they employ should not be easily reversed with de-obfuscation tools, like IDA Pro and Hopper.

### Use C Languages

Consider using C and C++, which can help in runtime manipulation to a great extent. Many libraries of these two languages easily integrate with Objective C. A similar approach for Android apps will be to use its Java Native Interface. The purpose of using C and C++ libraries is to protect the runtime or reverse-engineering tools, like class-dump, class-dump-z, Cycript, or Frida.


## M10. Extraneous Functionality
Typically, an attacker seeks to understand extraneous functionality within a mobile app in order to discover hidden functionality in in backend systems. The attacker will typically exploit extraneous functionality directly from their own systems without any involvement by end-users.

Before an app is ready for production, the development team often keeps code in it to have easy access to the backend server, create logs to analyze errors or carry staging information and testing details. This code is extraneous to the functioning of the app, i.e. it has no use for the intended user once the app is in production and is required only during the development cycle. 

### Extraneous Functionality Risks
In most cases, a benign code offers no extra advantage to an adversary who gains access. However, in certain cases, this code can carry information related to databases, user details, user permissions, API endpoints, etc. or disable functionalities like two-factor authentication. 

### Might include:

- Hidden backdoor functionality,
- Other internal development security controls not intended for production environment.

### Best Practices to Avoid Extraneous Functionality

The developer should know that automated tools cannot always detect the presence of the M10 risk. More often than not, it requires manual intervention before the app is pushed into app stores. The developer should take the following steps before the app is released:

- Ensure that no test code is present in the final build;
- Ensure that no hidden switches are present in the configuration settings;
- Logs should not contain any description of backend server processes, administrative privileges, etc.; 
- In general, logs should not be descriptive at all; 
- Ensure that full system logs are not exposed to apps by OEMs; 
- Use ProGuard or DexGuard to stop interaction between method calls and log classes; 
- Ensure that an adversary cannot set the app’s debug flag to true; and
- API endpoints accessed by the app should be well documented.




## References
- [OWASP Mobile Top 10: A comprehensive guide for mobile developers to counter risks](https://www.appsealing.com/owasp-mobile-top-10-a-comprehensive-guide-for-mobile-developers-to-counter-risks/)
- [OWASP mobile top 10 security risks explained with real world examples](https://medium.com/swlh/owasp-mobile-top-10-explained-with-real-world-examples-685c2f09e48c)
