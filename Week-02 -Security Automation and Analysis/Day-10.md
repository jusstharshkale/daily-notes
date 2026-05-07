Date : 03-05-2026

# Topic - ARP Spoofing and MITM (theory)
Objective : Learn how ARP Spoofing and Man-in-the-Middle (MITM) attacks work, how attackers intercept communication between devices, and understand the security risks and prevention techniques used in network security.

Concept : 
What is ARP?
ARP (Address Resolution Protocol) is a network protocol used to map an IP address to a MAC address inside a local network.
What is ARP Spoofing?
ARP Spoofing (also called ARP Poisoning) is a cyberattack where an attacker sends fake ARP messages to a network.
The attacker tricks devices into believing:
exmaple - "Attacker's MAC address = Router's IP address"
As a result, network traffic gets redirected through the attacker's system.

What is a MITM Attack?

MITM (Man-in-the-Middle) attack occurs when an attacker secretly places themselves between two communicating devices.
The attacker can:
1.Monitor traffic
2.Capture passwords
3.Read sensitive data
4.Modify communication
5.Inject malicious content

Attack Flow : 
1.Network Scanning
The attacker scans the local network to identify connected devices, including the victim and the router.
2.Collect IP and MAC Addresses
The attacker gathers the IP addresses and MAC addresses of both the victim system and the router.
3.Send Fake ARP Replies
The attacker sends spoofed ARP packets to the victim and router, falsely linking the attacker’s MAC address with their IP addresses.
4.Traffic Redirection
The victim and router update their ARP tables and begin sending network traffic through the attacker’s device.
5.MITM Attack Execution
The attacker intercepts, monitors, or modifies the communication between the victim and the router without their knowledge.
6.Data Capture or Manipulation
Sensitive information such as login credentials, browsing data, or session information can be captured or altered by the attacker.
