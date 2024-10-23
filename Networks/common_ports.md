# List of Common Ports

**Port 20** \- FTP, specifically the transportation of files

**Port 21** \- FTP, specifically communication with the server and sending commands to login, list directory contents, upload, and download files

**Port 22** \- SSH, SFTP

**Port 23** \- Telnet (less common to be implemented, verify this is what you want open)

**Port 25**- SMTP, specifically the default SMTP port, used for server-to-server communication. **NOTE**: Typically,  this port is disabled for clients, since better port options exist for client-to-server email communication (see Port 465 and Port 587).

**Port 53** \- DNS

**Port 80** \- HTTP

**Port 110** \- POP3, default port with no encryption. Older standard for email retrieval, so you will mostly see IMAP.

**Port 143** \- IMAP, default port with no encryption.

**Port 161** \- SNMP, specifically the communication from the SNMP manager to the agents

**Port 162** \- SNMP, specifically when agents send a Trap message to the SNMP manager

**Port 443** \- HTTPS

**Port 465** \- SMTP, specifically client-to-server communication using SMTPS (SMTP over SSL/TLS). Encrypts the communication between clients and servers. **NOTE**: This service was deprecated by RFC 8314, and most services will use Port 587\. However, some email service providers may allow this service to support legacy systems.

**Port 587** \- SMTP, specifically client-to-server communication using STARTTLS (SMTP strictly over TLS). Encrypts and authenticates the connection, enhancing security during email submission.

**Port 993** \- IMAPS, or IMAP with encryption.

**Port 995** \- POP3S, or POP3 with encryption.