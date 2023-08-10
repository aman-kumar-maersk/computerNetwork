### [Home](/README.md)

# Data Transfer Protocols

### What are Data transfer protocols ?
These are sets of rules and conventions that govern how data is exchanged between devices or systems over a network. These protocols ensure reliable, efficient, and secure data transmission.

## Some Common Data transfer protocols
> ### 1. Transmission Control Protocol (TCP)  
TCP is one of the most widely used protocols for data transfer over the internet. It provides reliable and connection-oriented communication between devices. TCP breaks data into packets, sends them, and ensures they arrive in the correct order at the destination. In case of any loss or corruption of packets, TCP automatically requests retransmission of required packets.

#### Features of TCP :
1. Connection Oriented
2. Relaiblity
3. Flow Control
4. Congestion Control
5. Full Duplex Communication
6. Three Way Handshake
7. Connection Termination

#### Three Way Handshake
The 3-way handshake is a process in TCP where the client and server exchange three messages to synchronize and establish a connection before they start exchanging data. It ensures that both parties are ready to communicate and establishes initial sequence numbers for data transmission.

1. **`Step 1 - SYN`**: The client sends a "SYN" (synchronize) message to the server to initiate a connection request. This message contains a sequence number that helps establish synchronization between the client and server.

2. **`Step 2 - SYN-ACK`**: Upon receiving the "SYN" message, the server responds with a "SYN-ACK" (synchronize-acknowledgment) message. This message acknowledges the client's request and also includes its own sequence number for synchronization.

3. **`Step 3 - ACK`**: Finally, the client sends an "ACK" (acknowledgment) message back to the server. This message confirms the receipt of the server's "SYN-ACK" message, and the connection is now established and ready for data transfer.

![TCP Handshake](/assets/tcpHandshake.png)

> ### 2. User Datagram Protocol (UDP)
UDP is connectionless as opposed to [TCP](#1-transmission-control-protocol-tcp) . It is faster because of less overhead of handshakes and headers, but that makes it less reliable too. Being connectionless, it can send data without establishing a connection.Due to being faster  and having less overhead, it is suitable for audio/video streamining or gaming application, however it does not guarantee data delivery or correct order, so error checking and retransmission must be handled by the application if needed.

Here's how the request-response process works in UDP:

1. **`Step 1 - Request`**: The client sends a request message to the server without any preliminary handshake. The request message contains the necessary information for the server to understand the client's request, such as the type of service or data needed.

2. **`Step 2 - Response`**: Upon receiving the request message, the server processes the request and sends a response message back to the client. The response contains the requested data or the result of the requested service.

![UDP Data Transfer](/assets/udpTransfer.png)

> ### 3. Hyper Text Transfer Protocol (HTTP)
HTTP is the protocol mainly used for transferring Web Pages and related resources over the Internet. It operates on top of [TCP](#1-transmission-control-protocol-tcp) and follows a `Request - Response method.`

#### Following are some of the features of [HTTP Protocol](/null)

1. [Stateless Protocol](/null)
2. [Request Methods (GET, POST, PUT, DELETE, etc.)](/null)
3. [Response Status Codes (200 OK, 404 Not Found, etc.)](/null)
4. [Headers](/null)
5. [Request Body](/null)
6. [Response Body](/null)
7. [URL (Uniform Resource Locator)](/null)
8. [Cookies](/null)
9. [HTTPS (Hypertext Transfer Protocol Secure)](/null)
10. [HTTP/0.9](/null)
11. [HTTP/1.1](/null)
12. [HTTP/2](/null)
13. [HTTP/3](/null)
14. [Caching](/null)
15. [Compression](/null)
16. [Content Negotiation](/null)
17. [Range Requests](/null)
18. [Keep-Alive](/null)
19. [Redirects](/null)
20. [Referrer](/null)
21. [User Authentication](/null)
22. [Content-Type Negotiation](/null)

> ### 4. HTTPS
HTTPS (Hypertext Transfer Protocol Secure) is a secure extension of HTTP that uses encryption, provided by SSL/TLS certificates, to protect data during transmission, ensuring confidentiality and integrity.

#### Following are the additional features supported in HTTPS :
1. [Secure Data Transmission](/null)
2. [SSL / TLS Handshake](/null)
3. [URL Scheme and Default Port](/null)
> ### 4. FTP

FTP (File Transfer Protocol) is a network protocol used for transferring files between a client and a server over a computer network, often used for website hosting and file sharing.

#### Some features of FTP :

1. **Two Channels:** FTP uses two separate channels - a command channel for sending commands and receiving responses, and a data channel for transferring actual files.

2. **Directory Listing:** FTP allows clients to view directory listings on the server, helping users navigate and manage remote file systems.

3. **Resume Support:** FTP supports resuming interrupted file transfers, enabling clients to pick up transfers from where they left off.

4. **Anonymous FTP:** FTP allows anonymous access to publicly available files, often used for sharing files without requiring login credentials.

5. **No Caching:** Unlike HTTP, FTP does not inherently support caching, as its primary purpose is file transfer, not web content delivery.

> ### 4. SSH
SSH (Secure Shell) is a cryptographic network protocol used for secure remote access and data transfer between two devices over an insecure network, such as the internet. It is very popular for managing remote controlled access over the internet.

#### Main features of SSH :

1. **Encryption:** SSH encrypts all communication between the client and server, ensuring that data remains confidential and secure from eavesdropping.

2. **Authentication Methods:** SSH supports various authentication methods, including password-based authentication, public-key authentication, and certificate-based authentication.

3. **Port Forwarding:** SSH allows users to create encrypted tunnels for forwarding traffic between local and remote ports, enabling secure access to services behind firewalls or NAT.

4. **Secure File Transfer (SFTP):** SSH includes SFTP, a secure file transfer protocol that allows secure uploading, downloading, and managing files on a remote server.

5. **Remote Execution (SSH Command):** SSH enables users to execute commands on a remote server securely, making it useful for server administration and automation.

6. **X11 Forwarding:** SSH can forward X Window System applications from the server to the client, allowing graphical applications to be run remotely.

7. **Tunneling:** SSH supports tunneling, which allows users to secure other network protocols like HTTP or SMTP over an SSH connection.
