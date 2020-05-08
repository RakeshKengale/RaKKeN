
## HTTP Headers

HTTP supports a large number of headers, some of which are designed for specific unusual purposes. Some headers can be used for both requests and responses, and others are specifi c to one of these message types.

### [General Headers]()
### [Request Headers]()
### [Response Headers]()

## General Headers

- `Connection` tells the other end of the communication whether it should close the TCP connection after the HTTP transmission has completed or keep it open for further messages.

- `Content-Encoding` specifies what kind of encoding is being used for the content contained in the message body, such as `gzip`, which is used by some applications to compress responses for faster transmission.

- `Content-Length` specifies the length of the message body, in bytes (except in the case of responses to `HEAD` requests, when it indicates the length of the body in the response to the corresponding `GET` request).

- `Content-Type` specifies the type of content contained in the message body, such as `text/html` for HTML documents.

- `Transfer-Encoding` specifies any encoding that was performed on the message body to facilitate its transfer over HTTP. It is normally used to specify chunked encoding when this is employed.


## Request Headers

- `Accept` tells the server what kinds of content the client is willing to accept, such as image types, office document formats, and so on.
 
- `Accept-Encoding` tells the server what kinds of content encoding the client is willing to accept.

- `Authorization` submits credentials to the server for one of the built-in HTTP authentication types.

- `Cookie` submits cookies to the server that the server previously issued.

- `Host` specifies the hostname that appeared in the full URL being requested.

- `If-Modified-Since` specifies when the browser last received the requested resource. If the resource has not changed since that time, the server may instruct the client to use its cached copy, using a response with status code `304`.

- `If-None-Match` specifies an entity tag, which is an identifier denoting the contents of the message body. The browser submits the entity tag that the server issued with the requested resource when it was last received. The server can use the entity tag to determine whether the browser may use its cached copy of the resource.

- `Origin` is used in cross-domain Ajax requests to indicate the domain from which the request originated.

- `Referer` specifies the URL from which the current request originated.

- `User-Agent` provides information about the browser or other client software that generated the request.

## Response Headers

- `Access-Control-Allow-Origin` indicates whether the resource can be retrieved via cross-domain Ajax requests.

- `Cache-Control` passes caching directives to the browser (for example, `no-cache`).

- `ETag` specifies an entity tag. Clients can submit this identifier in future requests for the same resource in the `If-None-Match` header to notify the server which version of the resource the browser currently holds in its cache.

- `Expires` tells the browser for how long the contents of the message body are valid. The browser may use the cached copy of this resource until this time.

- `Location` is used in redirection responses (those that have a status code starting with 3) to specify the target of the redirect.

- `Pragma` passes caching directives to the browser (for example, `no-cache`).

- `Server` provides information about the web server software being used.

- `Set-Cookie` issues cookies to the browser that it will submit back to the server in subsequent requests.

- `WWW-Authenticate` is used in responses that have a 401 status code to provide details on the type(s) of authentication that the server supports.

- `X-Frame-Options` indicates whether and how the current response may be loaded within a browser frame.

