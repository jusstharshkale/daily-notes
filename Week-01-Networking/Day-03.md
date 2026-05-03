Date : 26-04-2026

# Topic  - DNS Resolution
Objective : Understand how DNS resoultion is performed 

Concept :
The DNS (Domain Name System) resolution process is the "phonebook of the internet" mechanism that translates human-readable domain names (e.g., example.com) into machine-friendly IP addresses (e.g., 192.0.2.1). There is always a dot (.) at the end of a domain name which represents root domain (usually hidden in browsers).

8 Steps of DNS Resolution :
1.User Enters Query: You type a domain name (e.g., example.com) into your web browser.
2.Browser & OS Cache Check: The browser and operating system check their local caches to see if they have recently visited this site. If found, the process ends here.
3.Request to Recursive Resolver: If not cached, the computer sends a query to the Recursive Resolver (usually provided by your Internet Service Provider - ISP).
4.Query Root Nameserver: The resolver sends the query to a DNS Root Server (.), which acts as the index. The root server refers the resolver to the Top-Level Domain (TLD) server (e.g., .com).
5.Query TLD Nameserver: The resolver queries the TLD server (.com). The TLD server provides the IP address of the Authoritative Nameserver for the specific domain (example.com).
6.Query Authoritative Nameserver: The resolver queries the Authoritative Nameserver, which holds the final DNS records. It returns the exact IP address of example.com.
7.Resolver Returns IP: The recursive resolver sends the IP address back to your web browser.
8.Browser Connects to Website: Your browser uses the IP address to connect to the web server and loads the website.

Attacking Techniques :
--> DNS cache poisoning - attacker injects fake IP into cache
--> DNS hijacking - redirects users to malicious sites

# Topic - HTTP methods
Concept : HTTP methods define what action a client (browser) wants to perform on a server resource.

GET --> Retrieve data from the server
POST --> Send data to create a new resource
PATCH --> Partially update a resource
PUT --> Update/replace an existing resource
DELETE --> Remove a resource

# Topic - using nslookup and curl commands
The nslookup command performs a direct DNS query to resolve hostnames to IP addresses, while curl is a web client that resolves hostnames internally to fetch web content.
nslookup www.example.com   
curl -I https://www.example.com   







