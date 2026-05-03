Date : 30-04-2026

# Topic  - Documentation of Try Hack Me walkthrough --> Nmap : The basics
Objective : To understand the basics of Nmap and how it is used to scan networks.

Concept : Nmap (Network Mapper) is a tool used for network discovery and security auditing. It helps identify:
Open ports
Services running on those ports
Potential attack surfaces

Documentation: 
The room is to practice the nmap tool, which performs scanning of the network to detect the attack surface, ports, and services running on the ports.
The first command we used was:

-sn → ping scan

Then we used:

-sL → list scan

For performing specific protocol-based scans:

-sT --> TCP connect scan
-sU --> UDP scan

Other scan options:

-sS → TCP SYN scan
-F → fast scan
-p → specify a port range

Additional options:

-O → OS detection
-sV → service version detection
-A → aggressive scan
-v → verbosity

For debugging and saving results:

-d → debug the scan
-oN → save output in normal format
-oA → save output in all formats

# Topic -  Documentation of Try Hack Me walkthrough --> Networking essentials
Objective : To understand basic networking protocols and how devices communicate.

Concept : Protocols are basically the rules that devices follow to communicate with each other over a network. Without them, computers, phones, and servers wouldn’t understand how to send or interpret data.

Documentation:
The room 2 was about networking devices or identities where the first topic we studied was DHCP (Dynamic Host Configuration Protocol). We learned about the DHCP method to get a public IP address via DHCP.
Then we analyzed ARP (Address Resolution Protocol), which maps local networks with MAC addresses. Also understood the default syntax of MAC addresses.
Then we used ICMP echo requests, which include ping, to check if the target is alive and responding back with basic information.
We also used the traceroute command, which helps to find the path (routers) to reach the target.
At last, we learned routing via a diagram which states that a router has both public IP and private IP.
The public IP is used to connect to the internet, and the private IP is used within internal devices it is connected with.
