Date : 24-04-2026

# Topic - OSI Model
Objective : Understand how data travels from one system to another using layered architecture.

Concept :
The OSI(Open Systems Interconnection) model is considered as most important model for the representation of how the data travels through one system to another system. There are seven layers of OSI model from user interaction to physical transmission. 

Layers (Top --> Bottom) :

1.Application Layer - User interacts (browser request)
2.Presentation Layer - Data formatting + encryption
3.Session layer - Maintains connection between systems
4.Transport Layer - Breaks data into segments, add port info
5.Network Layer - Breaks segments into packets, uses IP addresses for routing packets between networks
6.Data link Layer - Breaks packets into frames, MAC based communication
7.Physical Layer - Converts data into binary and transmit physically

Attacking Techniques : 
--> Session layer can be compromised by session ID hijacking
--> Transport layer can be used for port based attacks
--> Network layer can help to retrieve IP address 


# Topic - TCP/IP Model
Concept : A practical implementation derived from the OSI model used in real-world networking.

Layers :
Application Layer
Transport Layer
Internet Layer
Network Access Layer

Attacking Techniques :
--> Application layer can be exploited by auth attack
--> Transport layer can be compromised by TCP SYN flooding
--> IP spoofing can be used to break the internet layer

# Topic - IP Address
Concept : IP address is the logical address of a system which is assigned to a device to access the internet. There are two versions of IP addresses is : IPv4 and IPv6 but currently version 4 is most widely used for connections.
The IP address are classified into five classes :

<img width="640" height="480" alt="Ip address" src="https://github.com/user-attachments/assets/dee4736b-9a41-41c3-90e4-f7a59ea4888f" />

Types of IP address :
1. Public IP  - This IP is visible on the internet
2. Private IP - Private IP is used inside a local network

Attacking Technique :
--> IP address can be used for scanning and reconnaissance
--> It can also be used to track a geo-location

How to identify :
--> Use ipconfig in windows command prompt
--> ifconfig in linux terminal

# Topic - MAC Address
Concept : A MAC (Media Access Control) address is a unique, permanent 48-bit identifier assigned to a network interface controller (NIC) for local network communications, usually displayed as 12 hexadecimal characters (e.g., 00:1A:2B:3C:4D:5E). Unlike IP addresses, they do not change but can be spoofed and are used by routers and switches to direct data to the correct physical device.

Attacking Technique :
--> ARP spoofing
--> Local network attacks

# Topic - Ports
Concept : Logical communication endpoints used by services and entry points for the attackers as they provide the information about the running services
<img width="1955" height="2113" alt="Ports" src="https://github.com/user-attachments/assets/2ade7607-b21f-4222-a2ff-9b11b6745660" />

# Topic - Protocols 
ARP - IP to MAC mappings -- ARP spoofing
FTP - send files - MITM
SMTP - used for email communication
HTTP - for web servers -- XSS
SSL - encrypts connections -- expired ssl certificate
HTTPS - secured version of http
DNS - converts names to IP address - Exfiltration
DHCP - DHCP servers provides IP/SM/DG/DNS

