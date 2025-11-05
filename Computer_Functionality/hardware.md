# Hardware

**Hub**: a network device that connects several devices locally. When a device wants to communicate with another device, it sends the data to the hub. The hub sends that data to every device on the network. This creates a lot of noise, so the hub isn’t efficient. It’s pretty much deprecated, and it was replaced with a switch.  

**Switch**: a network device that connects devices on a local network. All traffic is sent to the switch, and then the switch reads the packet headers to determine which device should be the recipient of the data. Then the switch sends that data to the appropriate device. This reduces a lot of noise, and only the requested device gets the information, making this more secure. Replaced the hub.  

**Modem**: a network device that translates digital data (from computer and network traffic) into analog data (in order to travel across cable systems (referring to cable TV providers that provide Internet), fiber optic cables, phone lines, or satellite dish), and vice versa. This device is not common for internal Local Area Networks, but homes will frequently have a modem that connect their network to the ISP. It’s common for this device to be combined with a router into a singular device.  

**Router**: a network device that has several functions. It is the main facilitator for forwarding data traffic from the modem to the other devices on the network, and vice versa. It also functions as a DHCP server, distributing IP addresses to devices on the network. It also facilitates communication between devices on the network, with the traffic going from the sender device to the router, and then the router to the receiving device. It also allows devices on different networks or subnetworks (subnets) to communicate with each other. In this instance, data goes from the sending device to the gateway for the network. Then that router checks a routing table to find the location of the receiving device, using the receiving device’s IP address as reference. It then passes the data through networks until it reaches the gateway device for the network that the receiving device resides at. That gateway device then forwards the data to the receiving device.  

**Gateway**: a device that’s a combination of a modem and router.  

**Motherboard**: the main circuit board in a computer. It connects all parts together, and it distributes power to these parts.   

**CPU**: Central Processing Unit. The “brain” of the computer, executing instructions received by programs. It gets data from the RAM or other storage, it processes the data to know the instructions it should follow, it should perform those instructions, and then it stores that data into the proper storage.  

**GPU**: Graphics Processing Unit. A processor designed to accelerate rendering of images and videos. It also processes effectively, making it desirable for programs or functions that are heavy in computation (like crypto mining). Basically, it’s like a CPU but dedicated for quick computations and processing.  

**RAM**: Random Access Memory. A type of computer memory where data is temporarily stored, until the computer is turned off. Then it is lost. It is used by the CPU for quick and easy access to data, making processing by the CPU faster. This is called being **volatile**. By storing data temporarily, it makes your computer more efficient. This memory is stored in RAM sticks, attached to the motherboard.

**ROM**: Read-Only Memory. A type of hardware that stores critical data and programming that makes the computer function. It's configured to only allow "reading" permissions, so the data can be used when needed. It does not allow data to be written to it, since that could jepeordize the stored data and make the computer unusable. The data on the hardware is also retained, even when the device is turned off. This is called being **non-volatile**.