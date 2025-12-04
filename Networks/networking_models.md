# Models

## (OSI) Open System Interconnection 

**What:** The OSI Model is a seven-layer model for networking. It describes how information moves from an application on a network device to its destination over a medium. The model outlines the seven layers, and the protocols used at those layers. 

**So-What:** It provides a way for people to standardize protocols, software, and technology communication. It makes creating easier, since improvements can be made in an isolated setting that won’t hurt other protocols or software. It makes testing easier, since it’s isolated and its focused on the specific creation. It makes debugging easier, since people can narrow down which layer, or step, the issue may be occurring in. It’s also a helpful model to teach how communication is done, as well as networking concepts in general. 

![OSI Model](./images/osi-model.png)

As shown in the image above, the seven layers are laid out as such:

| Layer | Method |
| :---- | :---- |
| Layer 7 | Application |
| Layer 6 | Presentation |
| Layer 5 | Session |
| Layer 4 | Transport |
| Layer 3 | Network |
| Layer 2 | Data Link |
| Layer 1 | Physical |

Layers 5-7 focus on applications: interfacing for a user, formatting data, etc. Layers 1-4 focus on transporting data. When following the process of data transporting from a device to a destination device, follow the flow shown in the image. It starts at Layer 7 and moves down to Layer 1 on the first device. Then after it transports and reaches the destination, it starts at Layer 1 and goes to Layer 7. Depending on certain scenarios and protocols in play, it could start or end at a lower level.

### Application Layer
This is the layer closest to the end user. It provides network services to applications on the user’s device, making them able to communicate over a network. For example, when the web browser performs DNS resolution and begins to prepare reaching out to a web server, this is Layer 7\. Sending and receiving emails also starts at layer 7\. 

**Protocols used:** HTTP, FTP, SMTP/POP3 (send and receive emails), DNS, and others used by software to communicate over the network.

### Presentation Layer 
This layer specializes in translating data between the application layer and the varying formats the data may need to be in to transfer over the network. Data encryption/decryption, compression, and data translation are examples of what happens in this layer.

**Data translation** is the process of turning data from one format into another. This makes it so complex code or information can be reformatted into a standardized type of data that can be easily transferred, and then it can be restored when it reaches the target device. For example, files can be compressed using ZIP compression, becoming a zipped file and compressed for easier delivery.

**Protocols used:** SSL/TLS for encryption

### Session Layer  
This layer manages the connection and communication between two devices or applications. The several phases of this layer are as follows:

1. Establishes/initiates the “**session**”, or connection, between the devices/applications.  
2. Maintains the session as the devices communicate. It determines if the communication is using **half-duplex** (each endpoint takes turn sending data, back and forth), or **full-duplex** (both endpoints send and receive data at the same time). This layer will send occasional synchronization points, so if the connection is interrupted, then the communication can continue from a saved point rather than restarting the entire thing. It will also perform recovery, so data loss can be mitigated.  
3. Properly closes the session.

**Protocols used:** Point-to-Point Tunneling Protocol (PPTP)


### Transport Layer
This layer focuses on making sure data is **reliably** transported across a network.

Data is broken up into pieces called **packets** to be sent across the network. Each packet is given two additional sections: a header and footer. Information is put in them to help facilitate the transfer. Then, it manages the flow of data to prevent congestion in the traffic. The structure of the header differs between IPv4 (Internet Protocol version 4) and IPv6 (Internet Protocol version 6).

If the protocol is using TCP (Transport Control Protocol), it will check for errors and resend any lost or corrupted packets. Then it wil re-arrange the packets back into order.

If the protocol is using UDP (User Datagram Protocol), then it prioritizes speed but disregards the connection itself and statuses. It gets the packets sent faster by not doing any checks for errors, and it does not do any handshakes or negotiations for connections. If a packet is corrupted, it does not get resent. This is popular for live services like video streaming and video games.

This layer uses ports to help direct traffic. It helps software anticipate what type of data is being sent by setting a standard for what type of data will be sent to which port, and how that data will be formatted.

#### IPv4 Header
The IPv4 header can range from 20-60 bytes. There are 13 mandatory fields and an optional field, totalling with up to 14 fields. Parts of the IPv4 header are:
- **Version (4 bits)**: This will always equal '4', as it states that this packet is using IPv4 instead of IPv6.
- **Internet Header Length (4 bits)**: length of the header, with a minimum of 5 (to represent 20 bytes) and a maximum of 15 (to represent 60 bytes).
- **DSCP (Differentiated Services Code Point) (6 bits)**: this defines the quality of the service needed for this packet. This determines whether to prioritize this data or not. Should it be delivered quickly, or should there be extra effort to guarantee that this was sent correctly? This determines what to do.
- **Explicit Congestion Notififcation (2 bits)**: this piece is used to indicate to the sender if there is network congestion. When the network is congested and packets are being sent to quickly, packets will get dropped. However, if this field is used, then a value is set and the sender is notified, so then the sending of packets slows down, reducing the chance of packets dropping. *NOTE*: This field will only work if the sender, receiver, and routers that forward the packets support this feature. A lot of modern implementations of devices come with this feature, but it's default to be disabled.
- **Total Packet Size (16 bits)**
- **Identification (16 bits)**: determines what packet this fragment is a part of. Sometimes a packet is too big, so it gets broken down into pieces called *fragments*. This ID is set so all the fragments can be reassembled into the packet.
- **Flags (3 bits)**: There are three flags to determine extra status/behavior.
    - **Reserved (1 bit)**: always set to 0. No current functionality. If it's set to 1, the packet is considered invalid.
    - **Don't Fragment (1 bit)**: determines if this packet is eligible to be broken into fragments.
    - **More Fragments (1 bit)**: If this packet is unfragmented, this flag is cleared. If it's fragmented, all fragments except the last one will have this flag set. The last fragment has a non-zero Fragment Offset, so it can still be told apart from an unfragmented packet.
- **Fragment Offset (13 bits)**: This field is used to determined the order of fragments and where this specific fragment fits into the overall packet.
- **Time to Live (TTL) (8 bits)**: gives a limited number of hops in between each receiving router. Once the timer hits 0, the packet is discarded, and an ICMP (Internet Control Message Protocol) message is sent to inform the sender that the packet didn't make it to the recipient. This helps prevent loops, in case routers keep passing it in a circle.
- **Protocol Being Used (8 bits)**: examples are ICMP, TCP, and UDP.
- **Header Checksum (16 bits)**: This field determines if this packet has any changes while in transit. Helps detect if any errors, corruptions, and modifications took place.
- **Source IP Address (32 bits)**
- **Destination IP Address (32 bits)**
- **Options (0 - 320 bits)**: Funnily enough, this is the *optional* field. This is not option used, as some options are seen as dangerous, so the packet could get blocked. This can allow extra control, routing features, and statistics.


#### IPv4 Footer
Parts of the footer are:

#### IPv6 Header
The IPv6 header is 40 bytes. 


## (TCP/IP) Transmission Control Protocol/Internet Protocol