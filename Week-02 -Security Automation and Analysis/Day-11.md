Date : 04-05-2026

# Topic - Deep packet analysis with wireshark
Objective : To understand how network packets are captured and analyzed using Wireshark and how deep packet analysis helps in network troubleshooting and security monitoring.

Concept : 
What is Packet Analysis?
Packet analysis is the process of capturing and inspecting data packets traveling over a network to understand communication between devices.
What is Deep Packet Analysis?
Deep Packet Analysis is an advanced method of inspecting network traffic where both packet headers and data (payload) are analyzed to understand what is happening inside the network communication.
It helps in:

--> Detecting suspicious activity
--> Troubleshooting network issues
--> Monitoring data flow
--> What is Wireshark?

Wireshark is a free and open-source tool used to capture and analyze network packets in real time.
It allows users to:

1.Capture live network traffic
2.View packet details
3.Filter specific traffic
4.Analyze protocols

Basic Working of Wireshark : 
--> Select a network interface (Wi-Fi/Ethernet)
--> Start packet capture
--> Generate network traffic (browsing, ping, etc.)
--> Analyze captured packets
--> Stop and save capture if needed

Common Protocols Seen : 
1.TCP/UDP – Communication protocols
2.HTTP/HTTPS – Web traffic
3.DNS – Domain name resolution
4.ARP – IP to MAC mapping
5.ICMP – Network testing (ping)

Basic Wireshark Filters : 
ip.addr == x.x.x.x → Filter specific IP
http → HTTP traffic
dns → DNS queries
tcp → TCP packets
arp → ARP traffic
icmp → Ping requests

Detecting suspicious traffic
Understanding network behavior
Security monitoring
