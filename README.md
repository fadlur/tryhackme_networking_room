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

