# Acronyms

**AES** \- Advanced Encryption Standard  
A secure, common symmetric encryption method. 

**ARP** \- Address Resolution Protocol  
	A protocol that associates IP addresses to MAC addresses on a local network.

**BIOS** \- Basic Input/Output System  
	Firmware that initializes and tests hardware parts of the computer to make sure they are functioning correctly. It also provides an interface to adjust settings for the computer and its parts. 

**CMOS** \- Complementary Metal-Oxide-Semiconductor  
	A battery on the motherboard that keeps track of system settings and real-world time.

**CPU** \- Central Processing Unit.  
The “brain” of the computer, executing instructions received by programs.

**DNS** \- Domain Name System  
	Service that translates domain names (URLs that we can understand and easily memorize, such as [www.google.com](http://www.google.com)) into IP Addresses (set of numbers/characters that computers easily understand, such as 8.8.8.8), and vice versa. 

**FTP** \- File Transfer Protocol  
This allows the computer to send and receive files.

**GPU** \- Graphics Processing Unit  
	Processor designed to accelerate rendering of images and videos. It also processes effectively, making it desirable for programs or functions that are heavy in computation (like crypto mining).

**HTTP** \- Hypertext Transfer Protocol  
	This allows the computer to connect to webpages.

**HTTPS** \- Hypertext Transfer Protocol Secure  
	This allows the computer to connect to webpages securely. It utilizes encryption.

**IMAP** \- Internet Message Access Protocol  
	One of two protocols used by email clients for retrieving emails from a mail server.

**IP** \- Internet Protocol  
Service that assigns a numerical label to a device, giving it a “name” and identifying where it is on a network  
There are two versions of IP addresses.   
	IPv4, commonly used today (for example, 192.168.1.1)  
IPv6, not as common, but may become more common since more of these can coexist (they look like this: 2001:0db8:85a3:0000:0000:8a2e:0370:7334)

**IRC** \- Internet Relay Chat  
Assigned port 194, but it typically uses port 6667\. Protocol that messaging software uses to send chat messages to a server, and then to the recipient(s). Both recipients are connected to the server for this process. This is kinda dying out, not too many services left. 

**ISP** \- Internet Service Provider  
	This is the company that provides you Internet access and data.

**OS** \- Operating System  
Your computer’s main program that uses hardware to work (examples: Windows 10, Windows 11, macOS Sonoma, Ubuntu)

**OSI** \- Open System Interconnection  
	seven-layer model for networking that describes how information moves from an application on a network device to its destination over a medium.

**POP3** \- Post Office Protocol version 3  
	One of two protocols used by email clients for retrieving email from a mail server.

**POST** \- Power-On Self Test   
	The first step of the BIOS that occurs when the computer is turned on. The condition of hardware is checked, and errors are reported.

**RAM** \- Random Access Memory  
	A type of computer memory where data is temporarily stored, until the computer is turned off. Then it is lost. It is used by the CPU for quick and easy access to data, making processing by the CPU faster. This is called being **volatile**. By storing data temporarily, it makes your computer more efficient. This memory is stored in RAM sticks, attached to the motherboard.

**RFID** \- Radio Frequency Identification  
Identification and tracking objects using radio waves. Items at the store may have RFID tags on them so the store tag readers will go off if they are being taken outside of the store without removal (aka, if they are being stolen). Hotels’ key cards are tags that will be scanned by the door’s tag reader, checking if the person and their card are the authorized users of the room.   
RFID consists of two parts: tags and readers. **Tags**, or transponders, are the objects of interest that are being tracked. **Readers**, or interrogators, check them. The readers emit a radio signal via an antenna. When the tag gets in range of the signal, the tag activates and sends its identification to the reader. The reader converts the signal into digital data so it can be processed by a computer system.   
There are different ranges of frequencies that they work at. The bigger the frequency, the closer the tag has to be to the reader. The closer the tag has to be to the reader, the less chance that interference can occur.

* **Low Frequency (LF)**: 30-300 kHz, used for animal tracking, access control.  
* **High Frequency (HF)**: 3-30 MHz, used for library books, contactless payments.  
* **Ultra-High Frequency (UHF)**: 300 MHz-3 GHz, used for supply chain management, inventory tracking.  
* **Microwave Frequency**: Above 3 GHz, used for toll collection, high-speed transactions

	The Flipper Zero is a popular device that has the ability to copy the ID of a tag and then communicate with the reader. There are several other devices that can do this, such as the Chameleon Ultra and Proxmark. You can use these to copy your hotel key card so you don’t have to carry your hotel key card on you and risk losing it. **However, do not use these tools for illegal purposes**. Do not copy tags and use them when you are not authorized to do so.

**ROM** \- Read-Only Memory  
	A type of memory that permanently stores data (until it’s deleted by the user). Since it’s permanently stored, it isn’t lost when the computer is turned off. However, accessing it is slower than if it was stored in RAM. It is faster to access from ROM than from a secondary storage device, like a USB or hard drive. This storage is located on the motherboard directly.  
	If you are familiar with emulators and ROMs, those ROM files are digital copies of this physical storage that would be located on a game cartridge and console. The emulator mimics the physical hardware of the console.

**RSA** \- Rivest–Shamir–Adleman  
A secure, common asymmetric encryption method

**SFTP** \- SSH File Transfer Protocol  
This allows the computer to send and receive files securely.

**SMTP** \- Simple Mail Transfer Protocol  
	This protocol strictly sends emails from a client to a server or between servers.

**SNMP** \- Simple Network Management Protocol  
Ports 161-162. Service that monitors and manages network devices. Network devices include routers, switches, servers, and printers. Each of these devices have an **agent** installed on them. An **agent** is a software module that monitors the device’s performance, status, and configuration. It allows SNMP manager software to get this information. 

**SSH** \- Secure Shell  
	This allows a computer to securely connect to another computer remotely

**SSL** \- Secure Socket Layer  
Network security protocol that seeks to ensure secure internet connections and protecting data. Used in HTTPS. However, SSL has a lot of security vulnerabilities, and the latest version of SSL was deprecated in 2015\. Some industries still use it, though.

**TCP** \- Transmission Control Protocol  
	A service on all computers. One of two ways that data is transmitted from one device to another  
	For TCP, data is broken down into packets, organized by “headers” that track what they are and their order. Sent in pieces, and when they are all gathered on the receiving device, they organize themselves into order. If a packet is lost, it’s sent again.  
	Useful in sending important information, when it is not time sensitive (for example, file sharing). 

**TCP/IP** \- Transmission Control Protocol/Internet Protocol  
	A comprehensive set of protocols that includes not only TCP and IP but also many other protocols that handle different aspects of network communication and management.

**TLS** \- Transport Layer Security  
Network security protocol that seeks to ensure secure internet connections and protect data. Used in HTTPS. This service is more secure than SSL.

**UDP** \- User Datagram Protocol  
	A service on all computers. One of two ways that data is transmitted from one device to another  
	For UDP, data is broken down into packets, organized by “headers” that track what they are BUT NOT ITS ORDER. For UDP, order does not matter. Sent in pieces to the receiving device, but there is no organization afterwards. If a packet is lost, it is NOT resent.   
	Useful in sending time-sensitive information, when losing some packets is acceptable (for example, video games, movie streaming, video calls)

**UEFI** \- Unified Extensible Firmware Interface  
	A more modern version of the BIOS. Most computers have UEFI nowadays. However, people tend to still refer to it as the BIOS.

**VM** \- Virtual Machine  
A separate operating system (OS) installed on your computer that shares hardware with your current operating system.
