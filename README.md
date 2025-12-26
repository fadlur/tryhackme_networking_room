# TRYHACKME NETWORKING

Ini adalah catatan materi tentang networking di tryhackme

**Di materi networking ada 4 room**
1. Networking Concepts
2. Networking Essentials
3. Networking Core Protocols
4. Networking Secure Protocols

## NETWORKING CONCEPTS

### OSI MODEL

The OSI (Open Systems Interconnection) model is a conceptual model developed by the International Organization for Standardization (ISO) that describes how communications should occur in a computer network. In other words, the OSI model defines a framework for computer network communications. Although this model is theoretical, it is vital to learn and understand as it helps grasp networking concepts on a deeper level. The OSI model is composed of seven layers:

1. Physical Layer
2. Data Link Layer
3. Network Layer
4. Transport Layer
5. Session Layer
6. Presentation Layer
7. Application Layer

Buat ngapalin biasanya pake term "Please Do Not Throw Spinach Pizza Away".

<img width="1077" height="800" alt="image" src="https://github.com/user-attachments/assets/c3733bd0-b904-4f2d-be09-02e37ba89e3b" />


**Summary**

| Layer Number	| Layer Name	| Main Function	| Example Protocols and Standards|
|----------|--------------|--------------|-----------------|
| Layer 7	| Application layer	| Providing services and interfaces to applications	| HTTP, FTP, DNS, POP3, SMTP, IMAP |
| Layer 6	| Presentation layer	| Data encoding, encryption, and compression	| Unicode, MIME, JPEG, PNG, MPEG |
| Layer 5	| Session layer	| Establishing, maintaining, and synchronising sessions	| NFS, RPC |
| Layer 4	| Transport layer	| End-to-end communication and data segmentation	| UDP, TCP |
| Layer 3	| Network layer	| Logical addressing and routing between networks	| IP, ICMP, IPSec |
| Layer 2	| Data link layer	| Reliable data transfer between adjacent nodes	| Ethernet (802.3), WiFi (802.11) |
| Layer 1	| Physical layer	| Physical data transmission media	| Electrical, optical, and wireless signals |

**Answer the questions below**

Which layer is responsible for end-to-end communication between running applications?

Answer: 4 (Transport Layer)

Which layer is responsible for routing packets to the proper network?

Answer: 3 (Network layer)

In the OSI model, which layer is responsible for encoding the application data?

Answer: 6 (Presentation Layer)

Which layer is responsible for transferring data between hosts on the same network segment?

Answer: 2 (Data link Layer)

### TCP/IP Model

TCP/IP stands for Transmission Control Protocol/Internet Protocol and was developed in the 1970s by the Department of Defense (DoD). In our presentation of the ISO OSI model, we went from bottom to top, from layer 1 to layer 7. In this task, let’s look at things from a different perspective, from top to bottom. From top to bottom, we have:

1. **Application Layer**: The OSI model application, presentation and session layers, i.e., layers 5, 6, and 7, are grouped into the application layer in the TCP/IP model.
2. **Transport Layer**: This is layer 4.
3. **Internet Layer**: This is layer 3. The OSI model’s network layer is called the Internet layer in the TCP/IP model.
4. **Link Layer**: This is layer 2.

The table below shows how the TCP/IP model layers map to the ISO/OSI model layers.

| Layer Number	| ISO | OSI Model	| TCP/IP Model (RFC 1122)	Protocols |
| ------------- | --- | --------- | --------------------------------- |
| 7	| Application Layer	| Application Layer	HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH,
| 6	| Presentation Layer | | |
| 5	| Session Layer | | |
| 4	| Transport Layer	| Transport Layer |	TCP, UDP |
| 3	| Network Layer	| Internet Layer |	IP, ICMP, IPSec |
| 2	| Data Link Layer	| Link Layer	| Ethernet 802.3, WiFi 802.11 |
| 1	| Physical Layer | | |

Di beberapa buku, ada yang mengikutkan Physical Layer

**Answer the questions below**

To which layer does HTTP belong in the TCP/IP model?

Answer: Application Layer

How many layers of the OSI model does the application layer in the TCP/IP model cover?

Answer: 3 (Presentation Layer, Session Layer & Physical Layer)

### IP Addresses and Subnets

Every host on the network needs a unique identifier for other hosts to communicate with him. Without a unique identifier, the host cannot be found without ambiguity. When using the TCP/IP protocol suite, we need to assign an IP address for each device connected to the network.

One analogy of an IP address is your home postal address. Your postal address allows you to receive letters and parcels from all over the world. Furthermore, it can identify your home without ambiguity; otherwise, you cannot shop online!

As you might already know, we have IPv4 and IPv6 (IP version 6). IPv4 is still the most common, and whenever you come across a text mentioning IP without the version, we expect them to mean IPv4.

So, what makes an IP address? An IP address comprises four octets, i.e., 32 bits. Being 8 bits, an octet allows us to represent a decimal number between 0 and 255. An IP address is shown in the image below.

<img width="1140" height="487" alt="image" src="https://github.com/user-attachments/assets/405f164d-4aee-4e28-9b26-c113b366a860" />

**Answer the questions below**

Which of the following IP addresses is not a private IP address?

- 192.168.250.125
- 10.20.141.132
- 49.69.147.197 (Answer)
- 172.23.182.251

Which of the following IP addresses is not a valid IP address?

- 192.168.250.15
- 192.168.254.17
- 192.168.305.19 (Answer)
- 192.168.199.13

### UDP and TCP

**UDP**

UDP (User Datagram Protocol) allows us to reach a specific process on this target host. UDP is a simple connectionless protocol that operates at the transport layer, i.e., layer 4. Being connectionless means that it does not need to establish a connection. UDP does not even provide a mechanism to know that the packet has been delivered.

An IP address identifies the host; we need a mechanism to determine the sending and receiving process. This can be achieved by using port numbers. A port number uses two octets; consequently, it ranges between 1 and 65535; port 0 is reserved. (The number 65535 is calculated by the expression 216 − 1.)

A real-life example similar to UDP is the standard mail service, with no delivery confirmation. In other words, there is no guarantee that the UDP packet has been received successfully, similar to the case of sending a parcel using standard mail with no confirmation of delivery. In the case of standard mail, it means a cheaper cost than the mail delivery options with confirmation. In the case of UDP, it means better speed than a transport protocol that provides “confirmation.”

But what if we want a transport protocol that acknowledges received packets? The answer lies in using TCP instead of UDP.

**TCP**

TCP (Transmission Control Protocol) is a connection-oriented transport protocol. It uses various mechanisms to ensure reliable data delivery sent by the different processes on the networked hosts. Like UDP, it is a layer 4 protocol. Being connection-oriented, it requires the establishment of a TCP connection before any data can be sent.

In TCP, each data octet has a sequence number; this makes it easy for the receiver to identify lost or duplicated packets. The receiver, on the other hand, acknowledges the reception of data with an acknowledgement number specifying the last received octet.

A TCP connection is established using what’s called a three-way handshake. Two flags are used: SYN (Synchronise) and ACK (Acknowledgment). The packets are sent as follows:

1. SYN Packet: The client initiates the connection by sending a SYN packet to the server. This packet contains the client’s randomly chosen initial sequence number.
2. SYN-ACK Packet: The server responds to the SYN packet with a SYN-ACK packet, which adds the initial sequence number randomly chosen by the server.
3. ACK Packet: The three-way handshake is completed as the client sends an ACK packet to acknowledge the reception of the SYN-ACK packet.

<img width="1280" height="640" alt="image" src="https://github.com/user-attachments/assets/17581b50-f6b4-4381-8ec1-c25e3b426c23" />

## Encapsulation

Encapsulation is an essential concept as it allows each layer to focus on its intended function. In the image below, we have the following four steps:

- **Application data**: It all starts when the user inputs the data they want to send into the application. For example, you write an email or an instant message and hit the send button. The application formats this data and starts sending it according to the application protocol used, using the layer below it, the transport layer.
- **Transport protocol segment or datagram** : The transport layer, such as TCP or UDP, adds the proper header information and creates the TCP segment (or UDP datagram). This segment is sent to the layer below it, the network layer.
- **Network packet**: The network layer, i.e. the Internet layer, adds an IP header to the received TCP segment or UDP datagram. Then, this IP packet is sent to the layer below it, the data link layer.
- **Data link frame**: The Ethernet or WiFi receives the IP packet and adds the proper header and trailer, creating a frame.
We start with application data. At the transport layer, we add a TCP or UDP header to create a TCP segment or UDP datagram. Again, at the network layer, we add the proper IP header to get an IP packet that can be routed over the Internet. Finally, we add the appropriate header and trailer to get a WiFi or Ethernet frame at the link layer.

<img width="1603" height="602" alt="image" src="https://github.com/user-attachments/assets/aff3b560-7e26-4e44-99d2-6a6d20570119" />

**The Life of a Packet**

Based on what we have studied so far, we can explain a simplified version of the packet’s life. Let’s consider the scenario where you search for a room on TryHackMe.

1. On the TryHackMe search page, you enter your search query and hit enter.
2. Your web browser, using HTTPS, prepares an HTTP request and pushes it to the layer below it, the transport layer.
3. The TCP layer needs to establish a connection via a three-way handshake between your browser and the TryHackMe web server. After establishing the TCP connection, it can send the HTTP request containing the search query. Each TCP segment created is sent to the layer below it, the Internet layer.
4. The IP layer adds the source IP address, i.e., your computer, and the destination IP address, i.e., the IP address of the TryHackMe web server. For this packet to reach the router, your laptop delivers it to the layer below it, the link layer.
5. Depending on the protocol, The link layer adds the proper link layer header and trailer, and the packet is sent to the router.
6. The router removes the link layer header and trailer, inspects the IP destination, among other fields, and routes the packet to the proper link. Each router repeats this process until it reaches the router of the target server.

The steps will then be reversed as the packet reaches the router of the destination network. As we cover additional protocols, we will revisit this exercise and create a more in-depth version.

### Telnet

The TELNET (Teletype Network) protocol is a network protocol for remote terminal connection. In simpler words, telnet, a TELNET client, allows you to connect to and communicate with a remote system and issue text commands. Although initially it was used for remote administration, we can use telnet to connect to any server listening on a TCP port number.

On the target virtual machine, different services are running. We will experiment with three of them:

- Echo server: This server echoes everything you send it. By default, it listens on port 7.
- Daytime server: This server listens on port 13 by default and replies with the current day and time.
- Web (HTTP) server: This server listens on TCP port 80 by default and serves web pages.

**Sample command akses ke http**

telnet 10.81.141.129 80
Trying 10.81.141.129...
Connected to 10.81.141.129.
Escape character is '^]'.
GET / HTTP/1.1
Host: telnet.thm

HTTP/1.1 200 OK
Content-Type: text/html
ETag: "2920831920"
Last-Modified: Thu, 20 Jun 2024 12:39:38 GMT
Content-Length: 20
Accept-Ranges: bytes
Date: Fri, 26 Dec 2025 03:40:27 GMT
Server: lighttpd/1.4.63

THM{TELNET_MASTER}

Connection closed by foreign host.
