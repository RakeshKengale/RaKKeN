> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Authentication vs Authorization**

Authentication means confirming your own identity, while authorization means granting access to the system. In simple terms, authentication is the process of verifying who you are, while authorization is the process of verifying what you have access to.

## Authentication

Authentication is the act of validating that users are who they claim to be. Authentication is about validating your credentials such as Username/User ID and password to verify your identity. The system then checks whether you are what you say you are using your credentials. Whether in public or private networks, the system authenticates the user identity through login passwords. Usually authentication is done by a username and password, although there are other various ways to be authenticated. Validating authenticity can be accomplished by having something physical like a key card, by having a user login with passwords or 2FA, utilizing Captcha tests, or even biometrics for a user.


## Authorization

Authorization is a process of giving a user permission to access a specific resource(s) or function(s). Authorization occurs after your identity is successfully authenticated by the system, which therefore gives you full access to resources such as information, files, databases, funds, etc. However authorization verifies your rights to grant you access to resources only after determining your ability to access the system and up to what extent. In other words, authorization is the process to determine whether the authenticated user has access to the particular resources. Authorization levels are the difference between a general user and an admin user. An admin user will have more abilities that a general user and it is important to authorize the rolls properly to ensure general users don't accidently, or intentionally, harm a system. Keep in mind that authentication is not 100% needed to gain authorization. This depends on the system and what information/abilities the systems has if it needs different levels of authorization and where authentication is needed. 


#### Differences between authentication and authorization:

Authentication | Authorization
---------- | ----------
Authentication confirms your identity to grant access to the system. | Authorization determines whether you are authorized to access the resources.
Authentication is the first step of authorization so always comes first. | Authorization is done after successful authentication.
It is the process of validating user credentials to gain user access. | It is the process of verifying whether access is allowed or not.
Challenges the user to validate credentials (for example, through passwords, answers to security questions, or facial recognition) | Verifies whether access is allowed through policies and rules.
Generally, transmits info through an ID Token | Generally, transmits info through an Access Token
Generally governed by the OpenID Connect (OIDC) protocol | Generally governed by the OAuth 2.0 framework.
__Ways of Authentication:__ Passwords, Two-factor authentication, Captcha test, Biometric authentication. | __Techniques used in Authorization:__ OAuth (Open Authorization), Permissions – Read-write access to files, Allowing to access of the database, Specifying user roles to access data.
