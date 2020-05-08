> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  HTTP Headers**


## HTTP Headers

HTTP supports a large number of headers, some of which are designed for specific unusual purposes. Some headers can be used for both requests and responses, and others are specifi c to one of these message types.

#### [General Headers](HTTP_Headers.md#general-headers-1)
#### [Request Headers](HTTP_Headers.md#request-headers-1)
#### [Response Headers](HTTP_Headers.md#response-headers-1)
#### [Response (Security) Headers](HTTP_Headers.md#response-security-headers-1)


## General Headers

- `Connection` tells the other end of the communication whether it should close the TCP connection after the HTTP transmission has completed or keep it open for further messages.

- `Content-Encoding` specifies what kind of encoding is being used for the content contained in the message body, such as `gzip`, which is used by some applications to compress responses for faster transmission.

- `Content-Length` specifies the length of the message body, in bytes (except in the case of responses to `HEAD` requests, when it indicates the length of the body in the response to the corresponding `GET` request).

- `Content-Type` specifies the type of content contained in the message body, such as `text/html` for HTML documents.

- `Transfer-Encoding` specifies any encoding that was performed on the message body to facilitate its transfer over HTTP. It is normally used to specify chunked encoding when this is employed.


## Request Headers

##### Here is an example: 

>  GET Request 

```
GET /home.html HTTP/1.1
Host: developer.example.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.example.com/testpage.html
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Mon, 18 Jul 2016 02:36:04 GMT
If-None-Match: "c561c68d0ba92bbeb8b0fff2a9199f722e3a621a"
Cache-Control: max-age=0
```

> POST Request

```
POST /myform.html HTTP/1.1
Host: developer.example.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Content-Length: 128
```

- `Host` specifies the hostname that appeared in the full URL being requested.

- `User-Agent` provides information about the browser or other client software that generated the request.

- `Accept` tells the server what kinds of content the client is willing to accept, such as image types, office document formats, and so on.
 
- `Accept-Language` The Accept-Language request-header field is similar to Accept, but restricts the set of natural languages that are preferred as a response to the request. Multiple languages can be listed separated by commas and the optional qvalue represents an acceptable quality level for non preferred languages on a scale of 0 to 1. 
 
- `Accept-Encoding` tells the server what kinds of content encoding the client is willing to accept.

- `Referer` specifies the URL from which the current request originated.

- `Connection` The Connection general-header field allows the sender to specify options that are desired for that particular connection and must not be communicated by proxies over further connections.
HTTP/1.1 defines the "close" connection option for the sender to signal that the connection will be closed after completion of the response.

   - `Connection: close`

   - By default, HTTP 1.1 uses persistent connections, where the connection does not automatically close after a transaction. HTTP 1.0, on the other hand, does not have persistent connections by default. If a 1.0 client wishes to use persistent connections, it uses the keep-alive parameter as follows:

   - `Connection: keep-alive`

- `Origin` is used in cross-domain Ajax requests to indicate the domain from which the request originated.

- `Authorization` submits credentials to the server for one of the built-in HTTP authentication types.

- `If-Modified-Since` specifies when the browser last received the requested resource. If the resource has not changed since that time, the server may instruct the client to use its cached copy, using a response with status code `304`.

- `If-None-Match` specifies an entity tag, which is an identifier denoting the contents of the message body. The browser submits the entity tag that the server issued with the requested resource when it was last received. The server can use the entity tag to determine whether the browser may use its cached copy of the resource.

- `Cookie` submits cookies to the server that the server previously issued.

## Response Headers

##### Here is an example: 

>  GET Request 

```
200 OK
Access-Control-Allow-Origin: *
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Mon, 18 Jul 2016 16:06:00 GMT
Etag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"
Keep-Alive: timeout=5, max=997
Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT
Server: Apache
Set-Cookie: mykey=myvalue; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding
X-Backend-Server: developer.webapp.testserver.example.com
X-Cache-Info: not cacheable; meta data too large
X-kuma-revision: 1085259
x-frame-options: DENY
```

- `Access-Control-Allow-Origin` indicates whether the resource can be retrieved via cross-domain Ajax requests.

- `Cache-Control` passes caching directives to the browser (for example, `no-cache`).

- `ETag` specifies an entity tag. Clients can submit this identifier in future requests for the same resource in the `If-None-Match` header to notify the server which version of the resource the browser currently holds in its cache.

- `Expires` tells the browser for how long the contents of the message body are valid. The browser may use the cached copy of this resource until this time.

- `Location` is used in redirection responses (those that have a status code starting with 3) to specify the target of the redirect.

- `Pragma` passes caching directives to the browser (for example, `no-cache`).

- `Server` provides information about the web server software being used.

- `WWW-Authenticate` is used in responses that have a 401 status code to provide details on the type(s) of authentication that the server supports.

- `Set-Cookie` issues cookies to the browser that it will submit back to the server in subsequent requests.

- `Transfer-Encoding` The Transfer-Encoding general-header field indicates what type of transformation has been applied to the message body in order to safely transfer it between the sender and the recipient. This is not the same as content-encoding because transfer-encodings are a property of the message, not of the entity-body. All transfer-coding values are case-insensitive. 

- `Vary` The Vary response-header field specifies that the entity has multiple sources and may therefore vary according to the specified list of request header(s). You can specify multiple headers separated by commas and a value of asterisk __*__ signals that unspecified parameters are not limited to the request-headers.

- `X-Frame-Options` indicates whether and how the current response may be loaded within a browser frame.


## Response (Security) Headers 

#### [HTTP Strict Transport Security (HSTS)](HTTP_Headers.md#http-strict-transport-security-hsts-1)
#### [Public Key Pinning Extension for HTTP (HPKP)](HTTP_Headers.md#public-key-pinning-extension-for-http-hpkp-1)
#### [X-Frame-Options](HTTP_Headers.md#x-frame-options-1)
#### [X-XSS-Protection](HTTP_Headers.md#x-xss-protection-1)
#### [X-Content-Type-Options](HTTP_Headers.md#x-content-type-options-1)
#### [Content-Security-Policy](HTTP_Headers.md#content-security-policy-1)
#### [X-Permitted-Cross-Domain-Policies](HTTP_Headers.md#x-permitted-cross-domain-policies-1)
#### [Referrer-Policy](HTTP_Headers.md#referrer-policy-1)
#### [Expect-CT](HTTP_Headers.md#expect-ct-1)
#### [Feature-Policy](HTTP_Headers.md#feature-policy-1)


## HTTP Strict Transport Security (HSTS)

HTTP Strict Transport Security (HSTS) is a web security policy mechanism which helps to protect websites against protocol [downgrade attacks]() and [cookie hijacking](). It allows web servers to declare that web browsers (or other complying user agents) should only interact with it using secure HTTPS connections, and never via the insecure HTTP protocol. A server implements an HSTS policy by supplying a header (Strict-Transport-Security) over an HTTPS connection (HSTS headers over HTTP are ignored). 

##### Values

Value | Description
------------ | -------------
max-age=SECONDS | The time, in seconds, that the browser should remember that this site is only to be accessed using HTTPS.
includeSubDomains |	If this optional parameter is specified, this rule applies to all of the site's subdomains as well. 

##### Here is an example: 

`Strict-Transport-Security: max-age=31536000 ; includeSubDomains`


## Public Key Pinning Extension for HTTP (HPKP)

HTTP Public Key Pinning (HPKP) is a security mechanism which allows HTTPS websites to resist impersonation by attackers using mis-issued or otherwise fraudulent certificates. 

__For example,__ 
sometimes attackers can compromise certificate authorities, and then can mis-issue certificates for a web origin.

The HTTPS web server serves a list of public key hashes, and on subsequent connections clients expect that server to use one or more of those public keys in its certificate chain. Deploying HPKP safely will require operational and organizational maturity due to the risk that hosts may make themselves unavailable by pinning to a set of public key hashes that becomes invalid. With care, host operators can greatly reduce the risk of [man-in-the-middle (MITM)]() attacks and other false authentication problems for their users without incurring undue risk. 

##### Values

Value | Description
------------ | -------------
max-age=SECONDS | The time, in seconds, that the browser should remember that this site is only to be accessed using HTTPS.
includeSubDomains | If this optional parameter is specified, this rule applies to all of the site's subdomains as well.

##### Here is an example: 

`Strict-Transport-Security: max-age=31536000 ; includeSubDomains`


## X-Frame-Options

X-Frame-Options response header improve the protection of web applications against Clickjacking. It declares a policy communicated from a host to the client browser on whether the browser must not display the transmitted content in frames of other web pages. 

##### Values

Value | Description
------------ | -------------
deny | No rendering within a frame.
sameorigin | No rendering if origin mismatch.
allow-from: DOMAIN | Allows rendering if framed by frame loaded from DOMAIN.

##### Here is an example: 

`X-Frame-Options: deny`


## X-XSS-Protection

This header enables the Cross-site scripting (XSS) filter in your browser. 

##### Values

Value | Description
------------ | -------------
0 | Filter disabled.
1 | Filter enabled. If a cross-site scripting attack is detected, in order to stop the attack, the browser will sanitize the page.
1; mode=block |	Filter enabled. Rather than sanitize the page, when a XSS attack is detected, the browser will prevent rendering of the page.
1; report=http://[YOURDOMAIN]/your_report_URI | Filter enabled. The browser will sanitize the page and report the violation. This is a Chromium function utilizing CSP violation reports to send details to a URI of your choice.

##### Here is an example: 

`X-XSS-Protection: 1; mode=block` 


## X-Content-Type-Options

Setting this header will prevent the browser from interpreting files as something else than declared by the content type in the HTTP headers.

##### Values

Value | Description
------------ | -------------
nosniff | Will prevent the browser from MIME-sniffing a response away from the declared content-type.

##### Here is an example: 

`X-Content-Type-Options: nosniff`


## Content-Security-Policy

A Content Security Policy (CSP) requires careful tuning and precise definition of the policy. If enabled, CSP has significant impact on the way browsers render pages (e.g., inline JavaScript disabled by default and must be explicitly allowed in policy). CSP prevents a wide range of attacks, including Cross-site scripting and other cross-site injections. 

##### Values

Directive | Description
------------ | -------------
base-uri | Define the base uri for relative uri.
default-src | Define loading policy for all resources type in case of a resource type dedicated directive is not defined (fallback).
script-src | Define which scripts the protected resource can execute.
object-src | Define from where the protected resource can load plugins.
style-src | Define which styles (CSS) the user applies to the protected resource.
img-src | Define from where the protected resource can load images.
media-src | Define from where the protected resource can load video and audio.
frame-src | Deprecated and replaced by child-src. Define from where the protected resource can embed frames.
child-src | Define from where the protected resource can embed frames.
frame-ancestors | Define from where the protected resource can be embedded in frames.
font-src | Define from where the protected resource can load fonts.
connect-src | Define which URIs the protected resource can load using script interfaces.
manifest-src | Define from where the protected resource can load manifest.
form-action | Define which URIs can be used as the action of HTML form elements.
sandbox | Specifies an HTML sandbox policy that the user agent applies to the protected resource.
script-nonce | Define script execution by requiring the presence of the specified nonce on script elements.
plugin-types | Define the set of plugins that can be invoked by the protected resource by limiting the types of resources that can be embedded.
reflected-xss | Instructs a user agent to activate or deactivate any heuristics used to filter or block reflected cross-site scripting attacks, equivalent to the effects of the non-standard X-XSS-Protection header.
block-all-mixed-content | Prevent user agent from loading mixed content.
upgrade-insecure-requests | Instructs user agent to download insecure resources using HTTPS.
referrer | Define information user agent must send in Referer header.
report-uri | Specifies a URI to which the user agent sends reports about policy violation.
report-to | Specifies a group (defined in Report-To header) to which the user agent sends reports about policy violation.

##### Here is an example: 

`Content-Security-Policy: script-src 'self'`


## X-Permitted-Cross-Domain-Policies

A cross-domain policy file is an XML document that grants a web client, such as Adobe Flash Player or Adobe Acrobat (though not necessarily limited to these), permission to handle data across domains. When clients request content hosted on a particular source domain and that content make requests directed towards a domain other than its own, the remote domain needs to host a cross-domain policy file that grants access to the source domain, allowing the client to continue the transaction. Normally a meta-policy is declared in the master policy file, but for those who can’t write to the root directory, they can also declare a meta-policy using the X-Permitted-Cross-Domain-Policies HTTP response header.

##### Values

Value | Description
------------ | -------------
none | No policy files are allowed anywhere on the target server, including this master policy file.
master-only | Only this master policy file is allowed.
by-content-type | [HTTP/HTTPS only] Only policy files served with Content-Type: text/x-cross-domain-policy are allowed.
by-ftp-filename | [FTP only] Only policy files whose file names are crossdomain.xml (i.e. URLs ending in /crossdomain.xml) are allowed.
all | All policy files on this target domain are allowed.

##### Here is an example: 

`X-Permitted-Cross-Domain-Policies: none`


## Referrer-Policy

The Referrer-Policy HTTP header governs which referrer information, sent in the Referer header, should be included with requests made.

##### Values

Value | Description
------------ | -------------
no-referrer | The Referer header will be omitted entirely. No referrer information is sent along with requests.
no-referrer-when-downgrade | This is the user agent's default behavior if no policy is specified. The origin is sent as referrer to a-priori as-much-secure destination (HTTPS->HTTPS), but isn't sent to a less secure destination (HTTPS->HTTP).
origin | Only send the origin of the document as the referrer in all cases. The document https://example.com/page.html will send the referrer https://example.com/.
origin-when-cross-origin | Send a full URL when performing a same-origin request, but only send the origin of the document for other cases.
same-origin | A referrer will be sent for same-site origins, but cross-origin requests will contain no referrer information.
strict-origin | Only send the origin of the document as the referrer to a-priori as-much-secure destination (HTTPS->HTTPS), but don't send it to a less secure destination (HTTPS->HTTP).
strict-origin-when-cross-origin | Send a full URL when performing a same-origin request, only send the origin of the document to a-priori as-much-secure destination (HTTPS->HTTPS), and send no header to a less secure destination (HTTPS->HTTP).
unsafe-url | Send a full URL (stripped from parameters) when performing a a same-origin or cross-origin request.

##### Here is an example: 

`Referrer-Policy: no-referrer` 


## Expect-CT

The Expect-CT header is used by a server to indicate that browsers should evaluate connections to the host emitting the header for Certificate Transparency compliance.

##### Values

Value | Description
------------ | -------------
report-uri | The optional report-uri directive indicates the URL to which the browser should report Expect-CT failures.
enforce | The optional enforce directive is a valueless directive that, if present, signals to the browser that compliance to the CT Policy should be enforced (rather than report-only) and that the browser should refuse future connections that violate its CT Policy. When both the enforce directive and report-uri directive are present, the configuration is referred to as an "enforce-and-report" configuration, signalling to the browser both that compliance to the CT Policy should be enforced and that violations should be reported.
max-age | The max-age directive specifies the number of seconds after the reception of the Expect-CT header field during which the browser should regard the host from whom the message was received as a Known Expect-CT Host.

##### Here is an example: 

`Expect-CT: max-age=86400, enforce, report-uri="https://foo.example/report"` 


## Feature-Policy

The Feature-Policy header allows developers to selectively enable and disable use of various browser features and APIs..

##### Values

Value | Description
------------ | -------------
accelerometer | Controls access to accelerometer sensors on the device.
ambient-light-sensor | Controls access to ambient light sensors on the device.
autoplay | Controls access to autoplay through play() and autoplay.
camera | Controls access to video input devices.
encrypted-media | Controls whether requestMediaKeySystemAccess() is allowed.
fullscreen | Controls whether requestFullscreen() is allowed.
geolocation | Controls access to Geolocation interface.
gyroscope | Controls access to gyroscope sensors on the device.
magnetometer | Controls access to magnetometer sensors on the device.
microphone | Controls access to audio input devices.
midi | Controls access to requestMIDIAccess() method.
payment | Controls access to PaymentRequest interface.
picture-in-picture | Controls access to Picture in Picture.
speaker | Controls access to audio output devices.
usb | Controls access to USB devices.
vibrate | Controls access to vibrate() method.
vr | Controls access to VR displays.

##### Here is an example:  

`Feature-Policy: vibrate 'none'; geolocation 'none'` 


**References**

- [HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)
- [OWASP Secure Headers Project](https://wiki.owasp.org/index.php/OWASP_Secure_Headers_Project#tab=Headers)
