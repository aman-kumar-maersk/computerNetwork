### [Home](/README.md)
# Network Models

### What is a Networl Model ?
A Network Model is a blueprint for the network architecture that outlines the design, flow and orgainsation of the network.

### Need for Network Model .
Computer networks are complex in nature. A Network Model helps to guide through the complex systems and to provide insights on the different layers.

## Different Network Models.

> ### 1. OSI Model

![OSI Model &copy Cloudflare](/assets/osiModel.png)
This is a conceptual model that divides the network into 7 layers . Each layer has a specific purpose and interacts to their adjacent layers.
Following are the 7 layers listed from top to bottom :
1. Physical Layer  

    ![Physical Layer](/assets/physicalLayer.png)
    It deals with the Physical transmission of data bits over connection like Copper cables, Optical fiber or Wireless signals. Here teh specification is defined for these .

2. Data Link Layer  

    ![Data Link Layer](/assets/dataLinkLayer.png)
    It is resopnsible for handeling data frames across the Physical layer between two devices. It also has to handle error detection abd correction, flow control and MAC identification.

3. Network Layer  

    ![Network Layer](/assets/networkLayer.png)
    It's responsible for routing data packets to different addresses. It uses IP (Internet Protocol) to address the devices. It finds the optimal path for transmission of data.

4. Transport Layer

    ![Transport Layer](/assets/transportLayer.png)
    It is responsible for reliable end to end communication between devices. It is responsible for breaking down data into smaller chunks to transmit, reassembly of the chunks, and provides error recovery mechanisms.  
    [TCP (Transport Layer Protocol)](/null) and [UDP (User Datagram Protocol)](/null) are two commonly used Transport layer protocols.

5. Session Layer  

    ![Session Layer](/assets/sessionLayer.png)
    It is resopnsible for establishing, managing and terminating communication sessions between devices.

6. Presentation Layer  

    ![Presenation Layer](/assets/presentationLayer.png)
    It is responsible for data representation, encryption, compression, and translation so as both parties can exchange and correctly understand the data.

7. Application Layer  

    ![Application Layer](/assets/applicationLayer.png)
    It is the topmost layer directly interfacing to the end user. It involves protocols like [HTTP/S (Hyper Text Transfer Protocol)](/null) , [FTP (File Transfer Protocol)](/null), [DNS (Domain Name Systems)](/null), etc. 


> ### 2. TCP/IP Model
This is also a conceptual model that divides network into 4 layers (arguably 5) .
Following are the 4 layers listed from top to bottom :
1. Network Interface Layer  
    It handles both physical transmission and includes protocols for accessing network like a combination of [Physical Layer](#1-osi-model) and [Data Link Layer](#1-osi-model) of [OSI Model](#1-osi-model).

2. Internet Layer  
    It is equivalent to the [Network Layer](#1-osi-model) in the OSI model, this layer provides IP addressing, routing, and packet forwarding services.

3. Transport Layer  
    It is similar to the transport layer in the [OSI model](#1-osi-model), this layer provides reliable data transport services using protocols like [TCP](/null) and [UDP](/null).
4. Application Layer  
    It combines the functions of the session, presentation, and application layers of the OSI model. It includes protocols for various network services like [HTTP](/null), [FTP](/null), SMTP, and [DNS](/pages/dns/README.md).