# Protocols in Depth

**DNS** \- port 53  
	Service that translates domain names (URLs that we can understand and easily memorize, such as [www.google.com](http://www.google.com)) into IP Addresses (set of numbers/characters that computers easily understand, such as 8.8.8.8), and vice versa. This service is needed to navigate the Internet. A URL paired with its corresponding IP address is called a “record”. This translation process is referred to as **DNS resolution**.  
Computers have a port for this service, as all computers will need this functionality. However, only some computers are capable of providing this service. We call them DNS servers. By “providing this service”, I mean they perform the translations and then send the corresponding value back to the other device.   
	There are different types of DNS servers  
		**Authoritative** \- they store the actual records for translation. For instance, there is data on the server stating that if a user requests [www.google.com](http://www.google.com), it’d send a corresponding IP address back, and vice versa.   
		**Recursive** \- a server that will query other DNS servers until they find a server that contains the requested translation. They will pass information to another server, and when they receive the response, they return that response.  
		**Caching** \- these servers go the extra mile by temporarily storing heavily-requested translations. If their users commonly search for [www.google.com](http://www.google.com), they will just store an appropriate IP address and return that instead of querying to another DNS server or looking through its own records.  
There is specific software that performs these DNS functions, so any computer can be a DNS server, either dedicated or partial. However, most users will most likely communicate with another device that is dedicated to performing DNS functions. There are open-source DNS Servers that anyone can use. Examples include Google (8.8.8.8), Cloudflare (1.1.1.1), and OpenDNS (208.67.222.222). For a lot of users, their Internet Service Provider (ISP) will typically own a recursive DNS server that will be the user’s first point of contact (this is how your ISP sees all your Internet traffic). Enterprises and other organizations may also have their own private DNS server that holds the records for internal sites. Then only people using internal computers that can communicate with this DNS server can access those sites.  
Recursive DNS servers may have trouble knowing where to find the specific record it is looking for. Authoritative DNS servers don’t hold all possible records. Thus, they will generally escalate up a hierarchy of DNS servers until they find the path they can go. The servers may pass it to a **root server**. Root servers are part of the “backbone” of the Internet. When passed a URL/IP address, they won’t know the exact location of the record. However, they can use part of what they are given (for example, the ‘.com’ in the URL) and pass it to a **Top-Level Domain** (TLD) **Server**. Each TLD is over a specific top-level domain part of the URL (.com, .net, and .edu in URLs are called top-level domains). Once they receive the URL from the root server, then they will search until they find the record. Once the record is obtained, it’s passed through the same path it took to get there until it reaches the end user.

**SNMP** \- ports 161, 162

SNMP’s service is to monitor and manage network devices. Network devices include routers, switches, servers, and printers. Each of these devices have an **agent** installed on them. An **agent** is a software module that monitors the device’s performance, status, and configuration. It allows SNMP manager software to get this information. 

**SNMP managers** are systems responsible for monitoring and managing the managed devices. They collect and analyze data from agents, and they can also send commands to agents to control devices or change their configuration.

Steps in SNMP communication:

1. Get-Request/Get-Response: The SNMP manager initiates communication by sending a "Get-Request" to the agent running on the managed device. The request includes the OID (Object Identifier) of the data the manager wants to retrieve.  
   1. Example: The manager might send a Get-Request for the CPU usage of a router.  
2. Agent: The agent receives the Get-Request, retrieves the requested data (such as CPU usage), and sends it back to the manager in a "Get-Response" message.  
3. Set-Request/Set-Response: The manager can also send a "Set-Request" to change the configuration or control parameters of the managed device. The agent processes the request and sends a "Set-Response" back to the manager.  
   1. Example: The manager might send a Set-Request to change the network configuration of a router.  
4. Trap: Agents can also send unsolicited messages called "Traps" to the manager to notify it of specific events or conditions, such as a system reboot, interface status change, or critical error.

PORTS:

Port 161 \- SNMP, specifically the communication from the SNMP manager to the agents

Port 162 \- SNMP, specifically when agents send a Trap message to the SNMP manager

**SMTP** \- ports 25, 465, 587  
This is a service that strictly sends emails from a client (the end user) to an email server, or from an email/mail server to another email/mail server. 

Steps in SMTP communication:

1. The email client (Outlook, Thunderbird, Gmail, or equivalent email service provider’s software) connects to an SMTP mail server. These email service providers have their own designated SMTP server(s).  
2. The email is sent to the SMTP server.   
3. The SMTP server processes the email and finds the domain name for the recipient(s) of the email. Then the SMTP server performs a **DNS lookup** on the domain name to find that domain’s mail server, if they have one. If the domain has a mail server, it will have a **Mail Exchange (MX) record**. The MX record will point to the mail server’s location.  
4. The SMTP server will forward the email to the email server found from the MX record. If no target email server is found, and the current SMTP server isn’t the recipient’s appropriate SMTP server (ie, if I am not sending from a Gmail account to another Gmail account), then the email fails to deliver and bounces back to the sender.  
5. The email is stored by the new SMTP mail server. This server may be referred to as the Mail Delivery Agent (MDA).  
6. The IMAP protocol or POP3 protocol takes over from here.

PORTS:

Port 25 \- SMTP, specifically the default SMTP port, used for server-to-server communication.   
**NOTE**: Typically,  this port is disabled for clients, since better port options exist for client-to-server email communication (see Port 465 and Port 587).

Port 465 \- SMTP, specifically client-to-server communication using SMTPS (SMTP over SSL/TLS). Encrypts the communication between clients and servers. **NOTE**: This service was deprecated by RFC 8314, and most services will use Port 587\. However, some email service providers may allow this service to support legacy systems.

Port 587 \- SMTP, specifically client-to-server communication using STARTTLS (SMTP strictly over TLS). Encrypts and authenticates the connection, enhancing security during email submission.

**IMAP** \- ports 143, 993  
This service is used by email clients (Outlook, Thunderbird, Gmail, or equivalent email service provider’s software) to retrieve emails from a mail server. This is a newer email protocol, as opposed to POP3. It works by keeping emails stored on the server, instead of downloading them. This is more of a live service, functioning like the Cloud. This allows multiple devices and users to connect to the same inbox. Any actions or change made to the emails on the email client is synchronized (or synced) to the inbox, to reflect those changes. In other words, if someone deletes an email from the inbox, everyone else using that inbox will see that that email gets deleted. Note that this will require constant connection to function smoothly.

If users wish to download emails to save them, they can do that, depending on the email client.

Steps to IMAP:

1. The email client connects to the mail server using the user’s credentials.  
2. The email server provides access to the inbox.  
3. The email client syncs with the server, occasionally downloading information like headers to make interactions easier.  
4. As long as the email client remains connected to the server, any changes the user makes is synced to the server.  
5. The email client disconnects when they are done. Occasionally, the email client can disconnect when the user has not made actions for a bit. If the user then makes changes before the connection is re-established, all changes will be synced on reconnection.

PORTS:

Port 143 \- default port for IMAP, using connections without encryption.

Port 993 \- port for IMAP connections with SSL/TLS encryption. Also referred to as IMAPS (or IMAP Secure)

**POP3** \- ports 110, 995  
This service is used by email clients (Outlook, Thunderbird, Gmail, or equivalent email service provider’s software) to retrieve emails from a mail server. It’s the older email protocol, as opposed to IMAP. It works by downloading emails to the individual’s local device they are accessing the client on. Then the mail server may delete the emails on its side, depending on configuration.

NOTE: IMAP is a newer service for email retrieval, so you may see that in the wild more often than POP3.

Steps in POP3 communication:

1. The email client uses POP3 to establish a connection to their respective mail server, or their Mail Delivery Agent (MDA).  
2. The email client uses the credentials of the logged in user on that client and accesses their designated inbox on the server.  
3. The emails are downloaded onto the user’s local device.  
4. While the user is connected, the email client may periodically check the email server for new emails and download them.

PORTS:

Port 110 \- default port for POP3, and it uses connections without encryption. 

Port 995 \- port used for POP3 connections using SSL/TLS encryption. This service is often referred to as POP3S (POP3 Secure).