Date : 24/04/2026

# Topic - OSI Model
Objective : Understand how data travels from one system to another using layered architecture.

Concept :
The OSI(Open Systems Interconnection) model is considered as most important model for the representation of how the data travels through one system to another system. There are seven layers of OSI model from user interaction to physical transmission. 

Layers (Top --> Bottom) :

1.Application Layer - User interacts (browser request)
2.Presentation Layer - Data formatting + encryption
3.Session layer - Maintains connection between systems
4.Transport Layer - Breaks data into segments, add port info
5.Network Layer - Breaks segments into packets, assigns IP address
6.Data link Layer - Breaks packets into frames, MAC based communication
7.Physical Layer - Converts data into binary and transmit physically

Attacker Thinking : 
--> Session layer can be compromised by session ID hijacking
--> Transport layer can be used for port based attacks
--> Network layer can help to retrieve IP address 


# Topic - TCP/IP Model
The TCP/IP model is further classifies OSI model into only four layers which is used in recent times to explain how data is transmitted between computers over a network,serving as the foundational protocol suite of the modern interne
Structure :
Application Layer
Transport Layer
Internet Layer
Network Access Layer

# Topic - IP Address
IP address is the logical address of a system which is assigned to a device to access the internet. There are two versions of IP address is used IPv4 and IPv6 but currently vesion 4 is most widely used for connections.
The IP address are classified into five classes :

<img width="640" height="480" alt="Ip address" src="https://github.com/user-attachments/assets/dee4736b-9a41-41c3-90e4-f7a59ea4888f" />

There are two types of IP address :
1. Public IP  - A public IP address is a unique, globally routable identifier assigned by your Internet Service Provider (ISP) to your modem or router, allowing your network to communicate over the internet. It enables external devices and websites to identify and connect with your network, unlike private IPs used internally.
2. Private IP - A private IP address is a non-routable address assigned to devices within a local network (LAN) by a router, allowing them to communicate with each other. Unlike public IPs, they are not visible on the internet and are reused across different private networks. Common ranges include 192.168.x.x, 10.x.x.x, and 172.16.x.x-172.31.x.x.

# Topic - MAC Address
A MAC (Media Access Control) address is a unique, permanent 48-bit identifier assigned to a network interface controller (NIC) for local network communications, usually displayed as 12 hexadecimal characters (e.g., 00:1A:2B:3C:4D:5E). Unlike IP addresses, they do not change and are used by routers and switches to direct data to the correct physical device.

# Topic - Ports
<img width="1955" height="2113" alt="Ports" src="https://github.com/user-attachments/assets/2ade7607-b21f-4222-a2ff-9b11b6745660" />

# Topic - Protocols 
ARP - IP to MAC mapings
FTP - send files
SMTP - used for email communication
HTTP - for web servers
SSL - for tunneling 
HTTPS - secured version of http
DNS - converts names to IP adress
DHCP - DHCP servers provides IP/SM/DG/DNS

