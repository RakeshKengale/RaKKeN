> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Status Codes**


## Status Codes

Each HTTP response message must contain a status code in its first line, indicating the result of the request. The status codes fall into five groups, according to the code’s first digit:

Code | Description
------------ | -------------
[1xx — (Informational)](Status_Codes.md#1xx--information-responses) | The request has been received and the process is continuing..
[2xx — (Success)](Status_Codes.md#2xx--successful-responses) | The request was successful.
[3xx — (Redirection)](Status_Codes.md#3xx--redirection-messages) | The client is redirected to a different resource.
[4xx — (Client Error)](Status_Codes.md#4xx--client-error-responses) | The request contains  incorrect syntax or error of some kind.
[5xx — (Server Error)](Status_Codes.md#5xx--server-error-responses) | The server encountered an error fulfilling the request.

There are numerous specific status codes, many of which are used only in specialized circumstances. Here are the status codes you are most likely to encounter when attacking a web application, along with the usual reason phrase associated with them:

### 1xx — (Information responses)

##### `100 Continue` 

This code is sent in some circumstances when a client submits a request containing a body. The response indicates that the request headers were received and that the client should continue sending the body. The server returns a second response when the request has been completed.

##### `101 Switching Protocol`

This code is sent in response to an Upgrade request header from the client, and indicates the protocol the server is switching to.

##### `102 Processing (WebDAV)` 

This code indicates that the server has received and is processing the request, but no response is available yet.

##### `103 Early Hints`

This status code is primarily intended to be used with the Link header, letting the user agent start preloading resources while the server prepares a response.


### 2xx — (Successful responses)

##### `200 OK` 

This code indicates that the request was successful and that the response body contains the result of the request.
 - GET: The resource has been fetched and is transmitted in the message body.
 - HEAD: The entity headers are in the message body.
 - PUT or POST: The resource describing the result of the action is transmitted in the message body.
 - TRACE: The message body contains the request message as received by the server

##### `201 Created` 

The request has succeeded and a new resource has been created as a result. This is typically the response sent after POST requests, or some PUT requests.

##### `202 Accepted`

The request has been received but not yet acted upon. It is noncommittal, since there is no way in HTTP to later send an asynchronous response indicating the outcome of the request. It is intended for cases where another process or server handles the request, or for batch processing.

##### `203 Non-Authoritative Information`

This response code means the returned meta-information is not exactly the same as is available from the origin server, but is collected from a local or a third-party copy. This is mostly used for mirrors or backups of another resource. Except for that specific case, the `200 OK` response is preferred to this status.

##### `204 No Content` 

There is no content to send for this request, but the headers may be useful. The user-agent may update its cached headers for this resource with the new ones.

##### `205 Reset Content`

Tells the user-agent to reset the document which sent this request.

##### `206 Partial Content`

This response code is used when the Range header is sent from the client to request only part of a resource.

##### `207 Multi-Status (WebDAV)`

Conveys information about multiple resources, for situations where multiple status codes might be appropriate.

##### `208 Already Reported (WebDAV)`

Used inside a `<dav:propstat>` response element to avoid repeatedly enumerating the internal members of multiple bindings to the same collection.

##### `226 IM Used (HTTP Delta encoding)`

The server has fulfilled a `GET` request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.


### 3xx — (Redirection messages)

##### `300 Multiple Choice`

The request has more than one possible response. The user-agent or user should choose one of them.

##### `301 Moved Permanently`

Redirects the browser permanently to a different URL, which is specified in the Location header. The client should use the new URL in the future rather than the original.

##### `302 Found`

Redirects the browser temporarily to a different URL, which is specified in the Location header. The client should revert to the original URL in subsequent requests.

##### `303 See Other`

The server sent this response to direct the client to get the requested resource at another URI with a `GET` request.

##### `304 Not Modified`

Instructs the browser to use its cached copy of the requested resource. The server uses the `If-Modified-Since` and `If-None-Match` request headers to determine whether the client has the latest version of the resource.


### 4xx — (Client Error Responses)

##### `400 Bad Request`

This code indicates that the client submitted an invalid HTTP request. You will probably encounter this when you have modified a request in certain invalid ways, such as by placing a space character into the URL.

##### `401 Unauthorized`

This code indicates that the server requires HTTP authentication before the request will be granted. The `WWW-Authenticate` header contains details on the type(s) of authentication supported.

##### `403 Forbidden`

This code indicates that no one is allowed to access the requested resource, regardless of authentication.

##### `404 Not Found`

This code indicates that the requested resource does not exist.

##### `405 Method Not Allowed`

This code indicates that the method used in the request is not supported for the specified URL. 

**For example,**
you may receive this status code if you attempt to use the `PUT` method where it is not supported.

##### `406 Not Acceptable`

This response is sent when the web server, after performing server-driven content negotiation, doesn't find any content that conforms to the criteria given by the user agent.

##### `407 Proxy Authentication Required`

This is similar to `401` but authentication is needed to be done by a proxy.

##### `408 Request Timeout`

This response is sent on an idle connection by some servers, even without any previous request by the client. It means that the server would like to shut down this unused connection.

##### `409 Conflict`

This response is sent when a request conflicts with the current state of the server.

##### `410 Gone`

This response is sent when the requested content has been permanently deleted from server, with no forwarding address. 

##### `411 Length Required`

Server rejected the request because the Content-Length header field is not defined and the server requires it.
 
##### `412 Precondition Failed`

The client has indicated preconditions in its headers which the server does not meet.

##### `413 Payload Too Large`

If you are probing for buffer overflow vulnerabilities in native code, and therefore are submitting long strings of data, this indicates that the body of your request is too large for the server to handle.

##### `414 URI Too Long`

This is similar to the `413` response. It indicates that the URL used in the request is too large for the server to handle.

##### `415 Unsupported Media Type` 

The media format of the requested data is not supported by the server, so the server is rejecting the request.

##### `429 Too Many Requests`

The user has sent too many requests in a given amount of time ("rate limiting").


### 5xx — (Server Error responses)

##### `500 Internal Server Error` 

This code indicates that the server encountered an error fulfilling the request. This normally occurs when you have submitted unexpected input that caused an unhandled error somewhere within the application’s processing. You should closely review the full contents of the server’s response for any details indicating the nature of the error.

##### `501 Not Implemented` 

The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.

##### `502 Bad Gateway`

This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.

##### `503 Service Unavailable` 

Normally indicates that, although the web server itself is functioning and can respond to requests, the application accessed via the server is not responding. You should verify whether this is the result of any action you have performed.

##### `504 Gateway Timeout`

This error response is given when the server is acting as a gateway and cannot get a response in time.

##### `505 HTTP Version Not Supported`

The HTTP version used in the request is not supported by the server.


#### Reference

- [List of HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)
