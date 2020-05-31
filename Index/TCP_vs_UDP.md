> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  TCP vs UDP**

## TCP vs UDP

- [What is TCP?](TCP_vs_UDP.md#what-is-tcp)
- [What is UDP?](TCP_vs_UDP.md#what-is-udp)
- [How TCP work?](TCP_vs_UDP.md#how-tcp-work)
- [How UDP work?](TCP_vs_UDP.md#how-udp-work)
- [Features of TCP](TCP_vs_UDP.md#features-of-tcp)
- [Difference between TCP and UDP](TCP_vs_UDP.md#difference-between-tcp-and-udp)
- [When to use UDP and TCP?](TCP_vs_UDP.md#when-to-use-udp-and-tcp)


### What is TCP?

TCP/IP helps you to determine how a specific computer should be connected to the internet and how you can transmit data between them. It helps you to create a virtual network when multiple computer networks are connected.
TCP/IP stands for Transmission Control Protocol/ Internet Protocol. It is specifically designed as a model to offer highly reliable and end-to-end byte stream over an unreliable internetwork.

### What is UDP?

UDP is a Datagram oriented protocol. It is used for broadcast and multicast type of network transmission. The full form of UDP is User Datagram Protocol (A datagram is a transfer unit associated with a packet-switched network.) The UDP protocol works almost similar to TCP, but it throws all the error-checking stuff out, all the back-and-forth communication and deliverability.

### How TCP work?

A TCP connection is established with the help of three-way handshake. It is a process of initiating and acknowledging a connection. Once the connection is established, data transfer begins, and when the transmission process is finished, the connection is terminated by the closing of an established virtual circuit.

### How UDP work?

UDP uses a simple transmission method without implied hand-shaking dialogues for ordering, reliability, or data integrity. UDP also assumes that error checking and correction is not important or performed in the application, to avoid the overhead of such processing at the network interface level. It is also compatible with packet broadcasts and multicasting.

### Features of TCP

Here, are some important features of TCP

- Delivery Acknowledgements
- Re transmission
- Delays transmission when the network is congested
- Easy Error detection

Here, are some important feature of UDP:

- Supports bandwidth-intensive applications that tolerate packet loss
- Less delay
- It sends the bulk quantity of packets.
- Possibility of the Data loss
- Allows small transaction ( DNS lookup)

## Difference between TCP and UDP

Here, are the differences between TCP and UDP

TCP | UDP
----- | -----
It is a connection-oriented protocol. | It is a connectionless protocol.
TCP reads data as streams of bytes, and the message is transmitted to segment boundaries. | UDP messages contain packets that were sent one by one. It also checks for integrity at the arrival time.
TCP messages make their way across the internet from one computer to another. | It is not connection-based, so one program can send lots of packets to another.
TCP rearranges data packets in the specific order. | UDP protocol has no fixed order because all packets are independent of each other.
The speed for TCP is slower. | UDP is faster as error recovery is not attempted.
Header size is 20 bytes | Header size is 8 bytes.
TCP is heavy-weight. TCP needs three packets to set up a socket connection before any user data can be sent. | UDP is lightweight. There are no tracking connections, ordering of messages, etc.
TCP does error checking and also makes error recovery. | UDP performs error checking, but it discards erroneous packets.
Acknowledgment segments | No Acknowledgment segments
Using handshake protocol like SYN, SYN-ACK, ACK | No handshake (so connectionless protocol)
TCP is reliable as it guarantees delivery of data to the destination router. | The delivery of data to the destination can't be guaranteed in UDP.
TCP offers extensive error checking mechanisms because it provides flow control and acknowledgment of data. | UDP has just a single error checking mechanism which is used for checksums.


### When to use UDP and TCP?

- TCP is an ideal choice, and even it has associated overhead, Therefore, when most of the overhead is in the connection, your application stays connected for any length of time.
- Use TCP sockets when both client and server independently send packets at that time; an occasional delay is acceptable. (e.g., Online Poker).
- TCP is best suited to be used for applications that require high reliability where timing is less of a concern.
  - World Wide Web (HTTP, HTTPS)
  - Secure Shell (SSH)
  - File Transfer Protocol (FTP)
  - Email (SMTP, IMAP/POP)

- UDP is ideal to use with multimedia like VoIP.
- You should use user UDP if both client and server may separately send packets, and occasional delay is also not acceptable. (e.g., Multiplayer games).
- UDP is best suited for applications that require speed and efficiency.
  - VPN tunneling
  - Streaming videos
  - Online games
  - Live broadcasts
  - Domain Name System (DNS)
  - Voice over Internet Protocol (VoIP)
- Trivial File Transfer Protocol (TFTP)
