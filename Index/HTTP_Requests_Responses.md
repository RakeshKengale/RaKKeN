> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  HTTP Protocol**

## HTTP Protocol

Hypertext transfer protocol (HTTP) is the core communications protocol used to access the World Wide Web and is used by all of today’s web applications. It is a simple protocol that was originally developed for retrieving static text-based resources. It has since been extended and leveraged in various ways to enable it to support the complex distributed applications that are now commonplace.

HTTP uses a message-based model in which a client sends a request message and the server returns a response message. The protocol is essentially connectionless: although HTTP uses the stateful TCP protocol as its transport mechanism, each exchange of request and response is an autonomous transaction and may use a different TCP connection.

#### [HTTP Requests](Index/HTTP_Requests_Responses.md#http-requests-1)
#### [HTTP Responses](Index/HTTP_Requests_Responses.md#http-responses-1)

## HTTP Requests

All HTTP messages (requests and responses) consist of one or more headers, each on a separate line, followed by a mandatory blank line, followed by an optional message body. 

> A typical HTTP request is as follows:

```
GET /auth/488/Details.ashx?uid=129 HTTP/1.1
Accept: application/x-ms-application, image/jpeg, application/xaml+xml, image/gif, image/pjpeg, application/x-ms-xbap, application/x-shockwaveflash, */*
Referer: https://example.com/auth/488/Home.ashx
Accept-Language: en-GB
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; .NET4.0C; InfoPath.3; .NET4.0E; FDM; .NET CLR 1.1.4322)
Accept-Encoding: gzip, deflate
Host: example.com
Connection: Keep-Alive
Cookie: SessionId=5B70C71F3FD4968935CDB6682E545476
```

The first line of every HTTP request consists of three items, separated by spaces:

- A verb indicating the HTTP method. The most commonly used method is __GET__, whose function is to retrieve a resource from the web server. __GET__ requests do not have a message body, so no further data follows the blank line after the message headers.

- The requested __URL__. The URL typically functions as a name for the resource being requested, together with an optional query string containing parameters that the client is passing to that resource. The query string is indicated by the `?` character in the URL. The example contains a single parameter with the name `uid` and the value `129`.

- The HTTP version being used. The only HTTP versions in common use on the Internet are __1.0__ and __1.1__, and most browsers use version __1.1__ by default. There are a few differences between the specifications of these two versions; however, the only difference you are likely to encounter when attacking web applications is that in version 1.1 the Host request header is mandatory.

- The __Referer__ header is used to indicate the URL from which the request originated (for example, because the user clicked a link on that page). Note that this header was misspelled in the original HTTP specification, and the misspelled version has been retained ever since.

- The __User-Agent__ header is used to provide information about the browser or other client software that generated the request. Note that most browsers include the Mozilla prefix for historical reasons. This was the User-Agent string used by the originally dominant Netscape browser, and other browsers wanted to assert to websites that they were compatible with this standard. As with many quirks from computing history, it has become so established that it is still retained, even on the current version of Internet Explorer, which made the request shown in the example.

- The __Host__ header specifies the hostname that appeared in the full URL being accessed. This is necessary when multiple websites are hosted on the same server, because the URL sent in the first line of the request usually does not contain a hostname.

- The __Cookie__ header is used to submit additional parameters that the server has issued to the client.


## HTTP Responses

> A typical HTTP response is as follows:

```
HTTP/1.1 200 OK
Date: Tue, 19 Apr 2011 09:23:32 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
Set-Cookie: tracking=tI8rk7joMx44S2Uu85nSWc
X-AspNet-Version: 2.0.50727
Cache-Control: no-cache
Pragma: no-cache
Expires: Thu, 01 Jan 1970 00:00:00 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 1067

<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 Transitional//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”><htmlxmlns=”http://www.w3.org/1999/xhtml” ><head><title>Your details</title>
...
```

The first line of every HTTP response consists of three items, separated by spaces:

- The HTTP __Version__ being used.

- A numeric status code indicating the result of the request. __200__ is the most common status code; it means that the request was successful and that the requested resource is being returned.

- A textual “reason phrase” further describing the status of the response. This can have any value and is not used for any purpose by current browsers. 

- The __Server__ header contains a banner indicating the web server software being used, and sometimes other details such as installed modules and the server operating system. The information contained may or may not be accurate.

- The __Set-Cookie__ header issues the browser a further cookie; this is submitted back in the __Cookie__ header of subsequent requests to this server.

- The __Pragma__ header instructs the browser not to store the response in its cache. The __Expires__ header indicates that the response content expired in the past and therefore should not be cached. These instructions are frequently issued when dynamic content is being returned to ensure that browsers obtain a fresh version of this content on subsequent occasions.

- Almost all HTTP responses contain a message body following the blank line after the headers. The __Content-Type__ header indicates that the body of this message contains an HTML document.

- The __Content-Length__ header indicates the length of the message body in bytes.

