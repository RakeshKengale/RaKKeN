> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  HTTP Headers**


## HTTP Headers

HTTP supports a large number of headers, some of which are designed for specific unusual purposes. Some headers can be used for both requests and responses, and others are specifi c to one of these message types.

#### [General Headers](HTTP_Headers.md#general-headers-1)
#### [Request Headers](HTTP_Headers.md#request-headers-1)
#### [Response Headers](HTTP_Headers.md#response-headers-1)

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
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/testpage.html
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Mon, 18 Jul 2016 02:36:04 GMT
If-None-Match: "c561c68d0ba92bbeb8b0fff2a9199f722e3a621a"
Cache-Control: max-age=0
```

> POST Request

```
POST /myform.html HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Content-Length: 128
```

- `Host` specifies the hostname that appeared in the full URL being requested.

- `User-Agent` provides information about the browser or other client software that generated the request.

- `Accept` tells the server what kinds of content the client is willing to accept, such as image types, office document formats, and so on.
 
- `Accept-Encoding` tells the server what kinds of content encoding the client is willing to accept.

- `Referer` specifies the URL from which the current request originated.

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
X-Backend-Server: developer2.webapp.scl3.mozilla.com
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

- `X-Frame-Options` indicates whether and how the current response may be loaded within a browser frame.


**References**

- [HTTP header fields](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)
