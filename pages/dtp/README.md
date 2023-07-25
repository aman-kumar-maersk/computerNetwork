### [Home](/README.md)

# Data Transfer Protocols

### What are Data transfer protocols ?
These are sets of rules and conventions that govern how data is exchanged between devices or systems over a network. These protocols ensure reliable, efficient, and secure data transmission.

## Some Common Data transfer protocols
> ### 1. Transmission Control Protocol (TCP)  
TCP is one of the most widely used protocols for data transfer over the internet. It provides reliable and connection-oriented communication between devices. TCP breaks data into packets, sends them, and ensures they arrive in the correct order at the destination. In case of any loss or corruption of packets, TCP automatically requests retransmission of required packets.

![TCP Handshake](/assets/tcpHandshake.png)

> ### 2. User Datagram Protocol (UDP)
UDP is connectionless as opposed to [TCP](#1-transmission-control-protocol-tcp) . It is faster because of less overhead of handshakes and headers, but that makes it less reliable too. Being connectionless, it can send data without establishing a connection.Due to being faster  and having less overhead, it is suitable for audio/video streamining or gaming application, however it does not guarantee data delivery or correct order, so error checking and retransmission must be handled by the application if needed.

![UDP Data Transfer](/assets/udpTransfer.png)

> ### 3. Hyper Text Transfer Protocol (HTTP)
HTTP is the protocol mainly used for transferring Web Pages and related resources over the Internet. It operates on top of [TCP](#1-transmission-control-protocol-tcp) and follows a Request - Response method.

> ### 4. HTTPS
> ### 4. FTP
> ### 4. HTTPS

