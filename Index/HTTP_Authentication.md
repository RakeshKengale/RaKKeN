> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  HTTP Authentication** 


## HTTP Authentication

The HTTP protocol includes its own mechanisms for authenticating users using various authentication schemes, including the following:

- Basic is a simple authentication mechanism that sends user credentials as a Base64-encoded string in a request header with each message.
- NTLM is a challenge-response mechanism and uses a version of the Windows NTLM protocol.
- Digest is a challenge-response mechanism and uses MD5 checksums of a nonce with the user’s credentials.

It is relatively rare to encounter these authentication protocols being used by web applications deployed on the Internet. They are more commonly used within organizations to access intranet-based services.


##### COMMON MYTH

> __Basic authentication is insecure.__

> Because basic authentication places credentials in unencrypted form within the HTTP request, it is frequently stated that the protocol is insecure and should not be used. But forms-based authentication, as used by numerous banks, also places credentials in unencrypted form within the HTTP request. Any HTTP message can be protected from eavesdropping attacks by using HTTPS as a transport mechanism, which should be done by every security-conscious application. In relation to eavesdropping, at least, basic authentication in itself is no worse than the methods used by the majority of today’s web applications.
