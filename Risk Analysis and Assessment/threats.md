# Threats

Types of threats:  
Malware \- viruses, worms, Torjan horses, and many “-ware” attacks. Very common  
Security breaches \- attempts to gain unauthorized access to systems. Cracking passwords, elevating privileges, breaking into a server, “hacking”  
DoS attacks \- prevent legitimate access to systems  
Web attacks \- attacks to breach websites. SQL injection, cross-site scripting (XSS)  
Session hijacking \- advanced attacks to take over a cookie session  
Insider threats \- credentialled, proper user misusing their access to steal data or compromise security, either intentionally or accidentally (untrained new employee)  
DNS poisoning \- compromises DNS server so that users are redirected to malicious websites  
Social engineering \- tricking users into thinking you are a proper user and getting ahold of information you should not have access to. Most common and most effective

Malware  
Definition \- malicious program or code that seeks to invade, damage, or disable computers/systems, networks, tablets, mobile devices

Types  
Virus \- self replicates

Trojan Horse \- malware pretending to be benign or legitimate software, but it secretly downloads other malware from within  
Spyware \- software that literally spies on the computer  
NOTE: could be good or bad, has practical uses  
Good use: Cookies, used to remember sessions or information on webpages  
Bad use:taking screenshots and sending them to the sender of the spyware; keylogger (storing keys that are typed, could be legit)  
Logic Bomb \- software that doesn’t do anything until a specific condition is met, typically date/time. When the condition is met, the software does something malicious.  
Adware \- software used to display advertisements. This can be annoying, it can slow the computer down, and the ads themselves could end up being malicious.

Security Breaches  
Definition \- attempts to gain unauthorized access to systems. There are technical and non-technical strategies to this.

Social Engineering \- breaching a system by exploiting human nature. Get users to give up information needed to gain access to a target system.   
Recon phase \- get information about an organization to use as leverage and appear as legitimate.   
Exploit phase \- get in contact, and leverage information or human nature to get additional information or access from system users.

War-driving  
	Cracker drives around to find vulnerably wireless networks and attempt to crack them.

	War flying \- drones equipped with Wi-Fi sniffing and cracking tools fly into areas of interest and attempt to gain access to wireless networks

War-dialing  
Computer is set up to call phone numbers in sequence until a computer of some kind that is attached to a phone line answers. Then the cracker can find a way to exploit that device.

Password cracking

Denial of Service (DoS) Attacks  
Bad actor blocks access to the system from legitimate users.

Common technique is to flood a service with many false connections, preventing it from addressing legitimate requests.

Common tools \- Low Orbit Ion Cannon (LOIC)

Variant \- Distributed Denial of Service (DDoS). Same goal as DoS, just with the bad actor using more than one device/service to send false connections/requests

Web Attacks  
Definition \- attacks focused on user interaction points on websites.

Common techniques  
SQL Injection \- entering SQL commands into forms, typically login forms, in an attempt to trick a server into executing those commands. Could be used to force the system to log the bad actor in, delete parts of the database, and much more

Intricate websites typically use some kind of programming language (PHP, Python if it uses something like Django as a back end, etc.). In these programming languages, it can work with SQL to automate databases or otherwise increase the ability to work with the database. When the program is operating with SQL commands, it puts them in quotes to act as a string (type of data in programming that is a list of characters/numbers/symbols acting as typical text).

Syntax of SQL example  
SELECT column1, column2 FROM tablename WHERE condition

Thinking in terms of spreadsheets, think of a table as a spreadsheet, and a column on a table is the same as a column on a table. The column specifies what information is stored in that cell. A record is equivalent to a spreadsheet’s row, indicating one instance of actual information stored in the spreadsheet. A field is one piece of the record, and it’s equivalent to a cell on a spreadsheet.

When logging in, might look like  
SELECT \* FROM users WHERE username \= ‘jsmith’

The \* is a wildcard, meaning ‘select all’   
The ‘users’ is the name of the table  
The ‘username’ is the name of a column  
The ‘jsmith’ is the value stored in a cell in the column that we are looking for

This command gives us all records that have the value ‘jsmith’ in a field under the username column on the users table.

In programming, code that would utilize this statement, IF INSECURE CODE, could look like this  
“SELECT \* FROM users WHERE username \= ‘“ \+ txtUsername.Text \+’ AND password \= ‘“ \+ txtPassword.Text \+”’” 

For SQL injection, the most basic technique is to just make a statement that is always true. A common way to do this is to put the following into the username and password fields on a website  
‘ or ‘1’1 \= 1’  
Include all quotes  
Then the query to the database will look like this  
SELECT \* FROM users WHERE username \= ‘’ OR ‘1’ \= ‘1’ AND password \= ‘’ OR ‘1’ \= ‘1’

You are telling the database to return all records that have the username equal to blank OR if 1 \= 1, and if the password is equal to blank OR if 1=1. Remember, SQL returns ALL RECORDS that match this condition. Well, 1 will always equal 1, so all records in the database get returned.

How can programmers avoid this kind of attack? A common technique is to “sanitize”, or filter, input from the user. Remove characters or anything else that could be mistaken for programming syntax. The programmer could also change how they interact/pass data around, which could help.

Cross-Site Scripting (XSS)  
Entering data other than what was intended, and it also depends on how well the programmer filters input. 

The bad actor finds an area of a website that has a textbox that other users who visit the website will see (for example, a global chat page or comment/review section). The bad actor types in code that acts as a script. Then, when another user loads that page, the website displays the text of other users. It sees the script that the bad actor types and thinks that it’s a webpage script, and either the browser or website will run the script. This script is typically in JavaScript syntax

For example, assume that Amazon is weak to this attack (it isn’t, so don’t even try; trying is a crime, anyway). I go to a popular item, and I leave a review for the item. However, instead of a review, I type in   
\<script\> window.location \= “http://www.fakeamazon.com”; \</script\>

Then, whenever someone clicks on that item, the browser loads that webpage. The script I typed gets run, and the user will get redirected to what looks like an Amazon login page (the fake website I sent them to). Then they type in their credentials, and I just stole their credentials. That’s the gist.

Session Hijacking  
Bad actor monitors an authenticated session between two legitimate devices. Can also knock out one user and pretend to be them.

Insider Threats  
Trusted user misuses their access to data, or they access data they are not authorized to access.  
To Fix: set proper security controls. Make sure users have the minimum permissions required to perform their tasks. Establish security policies to ensure data is properly and securely stored, and that disallows users from performing risky behavior, such as password storage and quality. Train users.

DNS Poisoning  
An attack that compromises DNS resolution and returns an illicit site instead of the expected one. Remember that DNS resolution is when the DNS server returns an IP address from a URL that was given to them. A poisoned record will receive the legitimate URL sent from the user, but the record points to a different IP address than the legitimate one.