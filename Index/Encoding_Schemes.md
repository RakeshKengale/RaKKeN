> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Encoding Schemes** 


## Encoding Schemes

Web applications employ several different encoding schemes for their data. Both the HTTP protocol and the HTML language are historically text-based, and different encoding schemes have been devised to ensure that these mechanisms can safely handle unusual characters and binary data. When you are attacking a web application, you will frequently need to encode data using a relevant scheme to ensure that it is handled in the way you intend. Furthermore, in many cases you may be able to manipulate the encoding schemes an application uses to cause behavior that its designers did not intend.

#### [URL Encoding](Encoding_Schemes.md#url-encoding-1)
#### [Unicode Encoding](Encoding_Schemes.md#unicode-encoding-1)
#### [HTML Encoding](Encoding_Schemes.md#html-encoding-1)
#### [Base64 Encoding](Encoding_Schemes.md#base64-encoding-1)
#### [Hex Encoding](Encoding_Schemes.md#hex-encoding-1)


## URL Encoding

URLs are permitted to contain only the printable characters in the `US-ASCII` character set — that is, those whose ASCII code is in the range `0x20` to `0x7e`, inclusive. Furthermore, several characters within this range are restricted because they have special meaning within the URL scheme itself or within the HTTP protocol.

The URL-encoding scheme is used to encode any problematic characters within the extended ASCII character set so that they can be safely transported over HTTP. The URL-encoded form of any character is the `%` prefix followed by the character’s two-digit ASCII code expressed in hexadecimal. Here are some characters that are commonly URL-encoded:

- `%3d — =`
- `%25 — %`
- `%20 — Space`
- `%0a — New line`
- `%00 — Null byte`

A further encoding to be aware of is the `+` character, which represents a URL-encoded space (in addition to the `%20` representation of a space).

NOTE 
> For the purpose of attacking web applications, you should URLencode any of the following characters when you insert them as data into an HTTP request:

> `space % ? & = ; + #`


## Unicode Encoding

Unicode is a character encoding standard that is designed to support all of the world’s writing systems. It employs various encoding schemes, some of which can be used to represent unusual characters in web applications.

16-bit Unicode encoding works in a similar way to URL encoding. For transmission over HTTP, the 16-bit Unicode-encoded form of a character is the `%u` prefix followed by the character’s Unicode code point expressed in hexadecimal:

- `%u2215 — /`
- `%u00e9 — é`

UTF-8 is a variable-length encoding standard that employs one or more bytes to express each character. For transmission over HTTP, the UTF-8-encoded form of a multibyte character simply uses each byte expressed in hexadecimal and preceded by the `%` prefix:

- `%c2%a9 — ©`
- `%e2%89%a0 — ≠`

For the purpose of attacking web applications, Unicode encoding is primarily of interest because it can sometimes be used to defeat input validation mechanisms. If an input filter blocks certain malicious expressions, but the component that subsequently processes the input understands Unicode encoding, it may be possible to bypass the filter using various standard and malformed Unicode encodings.


## HTML Encoding

HTML encoding is used to represent problematic characters so that they can be safely incorporated into an HTML document. Various characters have special meaning as metacharacters within HTML and are used to define a document’s structure rather than its content. To use these characters safely as part of the document’s content, it is necessary to HTML-encode them.

HTML encoding defines numerous HTML entities to represent specific literal characters:

- `&quot; — "`
- `&apos; — '`
- `&amp; — &`
- `&lt; — <`
- `&gt; — >`

In addition, any character can be HTML-encoded using its ASCII code in decimal form:

- `&#34; — "`
- `&#39; — '`

or by using its ASCII code in hexadecimal form (prefixed by an `x`):

- `&#x22; — "`
- `&#x27; — '`

When you are attacking a web application, your main interest in HTML encoding is likely to be when probing for cross-site scripting vulnerabilities. If an application returns user input unmodified within its responses, it is probably vulnerable, whereas if dangerous characters are HTML-encoded, it may be safe. 



## Base64 Encoding

Base64 encoding allows any binary data to be safely represented using only printable ASCII characters. It is commonly used to encode e-mail attachments for safe transmission over SMTP. It is also used to encode user credentials in basic HTTP authentication.

Base64 encoding processes input data in blocks of three bytes. Each of these blocks is divided into four chunks of six bits each. Six bits of data allows for 64 different possible permutations, so each chunk can be represented using a set of 64 characters. Base64 encoding employs the following character set, which contains only printable ASCII characters:

`ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/`

If the final block of input data results in fewer than three chunks of output data, the output is padded with one or two = characters. 

__For example,__  here is the Base64-encoded form of `web applications use Base64 encoding to transmit data.`

__OutPut__ `d2ViIGFwcGxpY2F0aW9ucyB1c2UgQmFzZTY0IGVuY29kaW5nIHRvIHRyYW5zbWl0IGRhdGEuIA`

Many web applications use Base64 encoding to transmit binary data within cookies and other parameters, and even to obfuscate (that is, to hide) sensitive data to prevent trivial modification. You should always look out for, and decode, any Base64 data that is issued to the client. Base64-encoded strings can often be easily recognized by their specific character set and the presence of padding characters at the end of the string.


## Hex Encoding
Many applications use straightforward hexadecimal encoding when transmitting binary data, using ASCII characters to represent the hexadecimal block.

__For example,__ hex-encoding the username “RaKKeN” within a cookie would result in this:

`52614B4B654E`

As with Base64, hex-encoded data is usually easy to spot. You should always attempt to decode any such data that the server sends to the client to understand its function.











