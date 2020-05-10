> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  Well-Known Common Protocols**

## Well-Known Common Protocols

A protocol is a set of rules. In computer networking, a protocol defines a standard way for computers to exchange information. Most common protocols used in computer networks and the internet are `TCP (Transmission Control Protocol)`, `UDP (User Datagram Protocol)`, and `IP (Internet Protocol)`.

A port in computer networking is a logical access channel for communication between two devices. Bi-directional communications and more complex connections may use multiple ports (channels) simultaneously.

Data on the Internet is organized into standard TCP or UDP packets. Network clients use different ports (or channels) to transfer this data. Generally one port is used to send data and another to receive it, so packets don't collide. The port number (and the destination IP address) is included as part of the header each packet is given. Ports range from `1` to `65535` for the `TCP` and `UDP` protocols.


### Port numbers are generally divided into three ranges:

__Well Known Ports:__
`0–1023`, well known ports assigned to common protocols and services, they are tightly bound to some services.

__Registered Ports:__
`1024–49151`, registered ports assigned by ICANN to a specific service.

__Dynamic/Private:__ 
`49152–65535`, these ports are not assigned for service.

Can be used by any service on an ad hoc basis. Ports are assigned when a session is established, and released when the session ends.


### Well-known ports (also known as system ports) are numbered from 0 through 1023:


Port | Description
------------ | -------------
20 | FTP  (data) - port for transferring FTP data
21 | FTP  (control) - port for FTP commands and flow control 
22 | SSH (Secure Shell) - used for secure logins, file transfers (scp, sftp) and port forwarding
23 | Telnet  - unencrypted text communication, remote login service
25 | Simple Mail Transfer Protocol (SMTP) E-mail routing
53 | Domain Name System (DNS) service
67 | Dynamic Host Configuration Protocol (DHCP) - Server
68 | Dynamic Host Configuration Protocol (DHCP) - Client
80 | HTTP (HyperText Transfer Protocol) - used for transferring web pages Hypertext Transfer Protocol (HTTP) used in the World Wide Web
88 | Kerberos authentication system 
109 | POP, Post Office Protocol, version 2 	 
110 | POP3 (Post Office Protocol version 3) - used for retrieving emails 
119 | Network News Transfer Protocol (NNTP)
123 | Network Time Protocol (NTP)
143 | Internet Message Access Protocol (IMAP) Management of digital mail
161 | Simple Network Management Protocol (SNMP)
194 | Internet Relay Chat (IRC)
389 | Lightweight Directory Access Protocol (LDAP)
443 | HTTP Secure (HTTPS) HTTP over TLS/SSL 


##### Reference
- [List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)


  






