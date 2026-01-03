# Packets
Data is broken into packets on Layer 3 (Network Layer) of the OSI Model. Packets contains headers and payloads. 

# Breakdown of Packet Headers
## IPv4 Header
The IPv4 header can range from 20-60 bytes. There are 13 mandatory fields and an optional field, totalling with up to 14 fields. Parts of the IPv4 header are:
- **Version (4 bits)**: This will always equal '4', as it states that this packet is using IPv4 instead of IPv6.
- **Internet Header Length (4 bits)**: Length of the header, with a minimum of 5 (to represent 20 bytes) and a maximum of 15 (to represent 60 bytes).
- **DSCP (Differentiated Services Code Point) (6 bits)**: This defines the quality of the service needed for this packet. This determines whether to prioritize this data or not. Should it be delivered quickly, or should there be extra effort to guarantee that this was sent correctly? This determines what to do.
- **Explicit Congestion Notififcation (2 bits)**: This piece is used to indicate to the sender if there is network congestion. When the network is congested and packets are being sent to quickly, packets will get dropped. However, if this field is used, then a value is set and the sender is notified, so then the sending of packets slows down, reducing the chance of packets dropping. *NOTE*: This field will only work if the sender, receiver, and routers that forward the packets support this feature. A lot of modern implementations of devices come with this feature, but it's default to be disabled.
- **Total Packet Size (16 bits)**
- **Identification (16 bits)**: Determines what packet this fragment is a part of. Sometimes a packet is too big, so it gets broken down into pieces called *fragments*. This ID is set so all the fragments can be reassembled into the packet.
- **Flags (3 bits)**: There are three flags to determine extra status/behavior.
    - **Reserved (1 bit)**: Always set to 0. No current functionality. If it's set to 1, the packet is considered invalid.
    - **Don't Fragment (1 bit)**: Determines if this packet is eligible to be broken into fragments.
    - **More Fragments (1 bit)**: If this packet is unfragmented, this flag is cleared. If it's fragmented, all fragments except the last one will have this flag set. The last fragment has a non-zero Fragment Offset, so it can still be told apart from an unfragmented packet.
- **Fragment Offset (13 bits)**: This field is used to determined the order of fragments and where this specific fragment fits into the overall packet.
- **Time to Live (TTL) (8 bits)**: Gives a limited number of hops in between each receiving router. Once the timer hits 0, the packet is discarded, and an ICMP (Internet Control Message Protocol) message is sent to inform the sender that the packet didn't make it to the recipient. This helps prevent loops, in case routers keep passing it in a circle.
- **Protocol Being Used (8 bits)**: Examples are ICMP, TCP, and UDP.
- **Header Checksum (16 bits)**: This field determines if this packet has any changes while in transit. Helps detect if any errors, corruptions, and modifications took place.
- **Source IP Address (32 bits)**
- **Destination IP Address (32 bits)**
- **Options (0 - 320 bits)**: Funnily enough, this is the *optional* field. This is not often used, as some options are seen as dangerous, so the packet could get blocked. This can allow extra control, routing features, and statistics.

## IPv6 Header
The IPv6 header is 40 bytes. There are eight mandatory fields, and there's a chance for optional, extended fields.

- **Version (4 bits)**: The value is 6, to indicate IPv6.
- **Traffic Class (6 + 2 bits)**: Contains the Differentiated Services information and the Explicit Congestion Notification information. 
    - **Differentiated Services (6 bits)**: This defines the quality of the service needed for this packet. This determines whether to prioritize this data or not. Should it be delivered quickly, or should there be extra effort to guarantee that this was sent correctly? This determines what to do.
    - **Explicit Congestion Notififcation (2 bits)**: This piece is used to indicate to the sender if there is network congestion. When the network is congested and packets are being sent to quickly, packets will get dropped. However, if this field is used, then a value is set and the sender is notified, so then the sending of packets slows down, reducing the chance of packets dropping. *NOTE*: This field will only work if the sender, receiver, and routers that forward the packets support this feature. A lot of modern implementations of devices come with this feature, but it's default to be disabled.
-  **Flow Label (20 bits)**: A group of packets related to each other (packets that were broken down from the same data) is called a **flow**. The flow label field in the header labels the packets belonging to the same flow, so intermediary routers that are forwarding the packets know they are part of the same flow. When special handling of these packets are set up, the routers know which packets are part of the same flow, and thus what receives the same treatment. If a router does not support this, or if the flow isn't set up for handling, then the default value is 0.
-  **Payload Length (16 bits)**: tells the size of the payload, including the header. 
-  **Next Header (8 bits)**: IPv6 replaces the Option field from IPv4 and includes **extension headers**, which optional, additional information and appear after this packet's header. The Next Header field specifies which type of extension header is next, if there is an extension header. This field will also specify it's transport layer protocol that is being used (TCP or UDP).
- **Hop Limit (8 bits)**: This field is the same as the Time To Live (TTL) field in IPv4 packets. It sets the maximum amount of intermediate nodes/devices that a packet can travel through. This is to prevent infinite loops due to a routing error.
- **Source Address (128 bits)**: the source of this packet, in IPv6 format.
- **Destination Address (128 bits)**: the destination of this packet, in IPv6 format.


