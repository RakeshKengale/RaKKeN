> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  URL**



## URL

__URL__ stands for __Uniform Resource Locator__. A URL is nothing more than the address of a given unique resource on the Web. In theory, each valid URL points to a unique resource. Such resources can be an HTML page, a CSS document, an image, etc. In practice, there are some exceptions, the most common being a URL pointing to a resource that no longer exists or that has moved. As the resource represented by the URL and the URL itself are handled by the Web server, it is up to the owner of the web server to carefully manage that resource and its associated URL.

> Here is an example:

```
https://example.com
https://example.com/en-US/docs/Learn/
https://example.com/en-US/search?q=URL
```

Any of those URLs can be typed into your browser's address bar to tell it to load the associated page (resource).

A URL is composed of different parts, some mandatory and others optional. Let's see the most important parts using the following URL:

`
http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument
`

__`http`__ is the protocol. The first part of the URL indicates which protocol the browser must use. A protocol is a set method for exchanging or transferring data around a computer network. Usually for websites it is the HTTP protocol or its secured version, HTTPS. 

__`www.example.com`__ is the domain name. It indicates which Web server is being requested. Alternatively, it is possible to directly use an IP address, but because it is less convenient, it is not often used on the Web.

__`:80`__ is the port. It indicates the technical "gate" used to access the resources on the web server. It is usually omitted if the web server uses the standard ports of the HTTP protocol (__80__ for __HTTP__ and __443__ for __HTTPS__) to grant access to its resources. Otherwise it is mandatory.

__`/path/to/myfile.html`__ is the path to the resource on the Web server. In the early days of the Web, a path like this represented a physical file location on the Web server. Nowadays, it is mostly an abstraction handled by Web servers without any physical reality.

__`?key1=value1&key2=value2`__ are extra parameters provided to the Web server. Those parameters are a list of key/value pairs separated with the `&` symbol. The Web server can use those parameters to do extra stuff before returning the resource. Each Web server has its own rules regarding parameters, and the only reliable way to know if a specific Web server is handling parameters is by asking the Web server owner.

__`#SomewhereInTheDocument`__ is an anchor to another part of the resource itself. An anchor represents a sort of "bookmark" inside the resource, giving the browser the directions to show the content located at that "bookmarked" spot. On an HTML document, 

__For example,__ 

The browser will scroll to the point where the anchor is defined; on a video or audio document, the browser will try to go to the time the anchor represents. It is worth noting that the part after the __#__, also known as the __fragment identifier__, is never sent to the server with the request.


**References**

- [URL - Wikipedia](https://en.wikipedia.org/wiki/URL)
- [What is a URL?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL)
