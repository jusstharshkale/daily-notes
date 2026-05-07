Date : 05-05-2026

# Topic Network Scanning and Enumeration
Objective : To perform network scanning and enumeration using tools like Nmap to identify active hosts, open ports, running services, and system information in a network.

Concept : 
Network scanning is the process of discovering devices, services, and vulnerabilities in a network.
Enumeration is the process of extracting detailed information about those discovered systems.
5 Goals of network scanning : 
--> Host discovery - Using netdiscover -r <target ip range>
--> Open ports - Using nmap -p <port> <target ip>
--> Service protocols - using nmap  -p <port> <target ip> 
--> Software + versions - using nmap -p <port> -sV <target ip>
--> OS detection - using nmap -p <port> <target ip> -O

Importance of Network Scanning :
1.Identifies network weaknesses
2.Helps in penetration testing
3.Detects unauthorized devices
4.Improves network security posture
5.Provides system visibility

What is Enumeration?
Enumeration is the process of actively extracting detailed information from a target system after network scanning has identified it as active.
While scanning tells you what is there, enumeration tells you what exactly it is and how it is configured.

What Does Enumeration Reveal?

Enumeration can help identify:
--> Usernames and groups
--> Running services and their configurations
--> Shared folders or resources
--> System information (OS details, hostname)
--> Network shares and permissions
--> Potential entry points for attacks

Script-based Enumeration (NSE) : 
nmap --script=vuln <target_ip>
nmap --script=default <target_ip>
nmap --script=http-enum <target_ip>

Tools for enumeration : 
SMB enumeration → enum4linux
DNS enumeration → dig, nslookup
SNMP enumeration → snmpwalk









