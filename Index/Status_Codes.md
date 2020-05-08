
## Status Codes

Each HTTP response message must contain a status code in its first line, indicating the result of the request. The status codes fall into five groups, according to the code’s first digit:

- [1xx — (Informational)]() The request has been received and the process is continuing..
- [2xx — (Success)]() The request was successful.
- [3xx — (Redirection)]() The client is redirected to a different resource.
- [4xx — (Client Error)]() The request contains  incorrect syntax or error of some kind.
- [5xx — (Server Error)]() The server encountered an error fulfilling the request.

There are numerous specific status codes, many of which are used only in specialized circumstances. Here are the status codes you are most likely to encounter when attacking a web application, along with the usual reason phrase associated with them:

### 1xx — (Information responses)

- _`100 Continue`_ is sent in some circumstances when a client submits a request containing a body. The response indicates that the request headers were received and that the client should continue sending the body. The server returns a second response when the request has been completed.

- _`101 Switching Protocol`_ This code is sent in response to an Upgrade request header from the client, and indicates the protocol the server is switching to.

- _`102 Processing (WebDAV)_` This code indicates that the server has received and is processing the request, but no response is available yet.

- _`103 Early Hints`_ This status code is primarily intended to be used with the Link header, letting the user agent start preloading resources while the server prepares a response.

### 2xx — (Successful responses)

- _`200 OK`_ indicates that the request was successful and that the response body contains the result of the request.

- GET: The resource has been fetched and is transmitted in the message body.
- HEAD: The entity headers are in the message body.
- PUT or POST: The resource describing the result of the action is transmitted in the message body.
- TRACE: The message body contains the request message as received by the server

- _`201 Created`_ The request has succeeded and a new resource has been created as a result. This is typically the response sent after POST requests, or some PUT requests.

- _`202 Accepted`_ The request has been received but not yet acted upon. It is noncommittal, since there is no way in HTTP to later send an asynchronous response indicating the outcome of the request. It is intended for cases where another process or server handles the request, or for batch processing.

- _`203 Non-Authoritative Information`_ This response code means the returned meta-information is not exactly the same as is available from the origin server, but is collected from a local or a third-party copy. This is mostly used for mirrors or backups of another resource. Except for that specific case, the `200 OK` response is preferred to this status.

- _`204 No Content`_ There is no content to send for this request, but the headers may be useful. The user-agent may update its cached headers for this resource with the new ones.

- _`205 Reset Content`_ Tells the user-agent to reset the document which sent this request.

- _`206 Partial Content`_ This response code is used when the Range header is sent from the client to request only part of a resource.

- _`207 Multi-Status (WebDAV)`_ Conveys information about multiple resources, for situations where multiple status codes might be appropriate.

- _`208 Already Reported (WebDAV)`_ Used inside a `<dav:propstat>` response element to avoid repeatedly enumerating the internal members of multiple bindings to the same collection.

- _`226 IM Used (HTTP Delta encoding)`_ The server has fulfilled a `GET` request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.


### 3xx — (Redirection messages)

- _`300 Multiple Choice`_ The request has more than one possible response. The user-agent or user should choose one of them.

- _`301 Moved Permanently`_ redirects the browser permanently to a different URL, which is specified in the Location header. The client should use the new URL in the future rather than the original.

- _`302 Found`_ redirects the browser temporarily to a different URL, which is specified in the Location header. The client should revert to the original URL in subsequent requests.

- _`303 See Other`_ The server sent this response to direct the client to get the requested resource at another URI with a `GET` request.

- _`304 Not Modified`_ instructs the browser to use its cached copy of the requested resource. The server uses the `If-Modified-Since` and `If-None-Match` request headers to determine whether the client has the latest version of the resource.


### 4xx — (Client Error Responses)

- _`400 Bad Request`_ indicates that the client submitted an invalid HTTP request. You will probably encounter this when you have modified a request in certain invalid ways, such as by placing a space character into the URL.

- _`401 Unauthorized`_ indicates that the server requires HTTP authentication before the request will be granted. The `WWW-Authenticate` header contains details on the type(s) of authentication supported.

- _`403 Forbidden`_ indicates that no one is allowed to access the requested resource, regardless of authentication.

- _`404 Not Found`_ indicates that the requested resource does not exist.

- _`405 Method Not Allowed`_ indicates that the method used in the request is not supported for the specified URL. 

**For example,**

you may receive this status code if you attempt to use the `PUT` method where it is not supported.

- _`406 Not Acceptable`_ This response is sent when the web server, after performing server-driven content negotiation, doesn't find any content that conforms to the criteria given by the user agent.

- _`407 Proxy Authentication Required`_ This is similar to `401` but authentication is needed to be done by a proxy.

- _`408 Request Timeout`_ This response is sent on an idle connection by some servers, even without any previous request by the client. It means that the server would like to shut down this unused connection.

- _`409 Conflict`_ This response is sent when a request conflicts with the current state of the server.

- _`410 Gone`_ This response is sent when the requested content has been permanently deleted from server, with no forwarding address. 

- _`411 Length Required`_ Server rejected the request because the Content-Length header field is not defined and the server requires it.
 
- _`412 Precondition Failed`_ The client has indicated preconditions in its headers which the server does not meet.

- _`413 Payload Too Large`_ If you are probing for buffer overflow vulnerabilities in native code, and therefore are submitting long strings of data, this indicates that the body of your request is too large for the server to handle.

- _`414 URI Too Long`_ is similar to the `413` response. It indicates that the URL used in the request is too large for the server to handle.

- _`415 Unsupported Media Type`_ The media format of the requested data is not supported by the server, so the server is rejecting the request.

- _`429 Too Many Requests`_ The user has sent too many requests in a given amount of time ("rate limiting").


### 5xx — (Server Error responses)

- _`500 Internal Server Error`_ indicates that the server encountered an error fulfilling the request. This normally occurs when you have submitted unexpected input that caused an unhandled error somewhere within the application’s processing. You should closely review the full contents of the server’s response for any details indicating the nature of the error.

- _`501 Not Implemented`_ The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.

- _`502 Bad Gateway`_ This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.

- _`503 Service Unavailable`_ normally indicates that, although the web server itself is functioning and can respond to requests, the application accessed via the server is not responding. You should verify whether this is the result of any action you have performed.

- _`504 Gateway Timeout`_ This error response is given when the server is acting as a gateway and cannot get a response in time.

- _`505 HTTP Version Not Supported`_ The HTTP version used in the request is not supported by the server.


#### Reference

- [List of HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)