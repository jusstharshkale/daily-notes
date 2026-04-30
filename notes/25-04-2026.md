25-4-2026

# Topic  - TCP 3 way handhsake and flags
The TCP 3-way handshake is a foundational process used by the Transmission Control Protocol (TCP) to establish a reliable, full-duplex connection between a client and a server before data transmission. It involves a three-step exchange—SYN, SYN-ACK, ACK—that synchronizes sequence numbers, acknowledges readiness, and ensures both parties can communicate.

Purpose : 
Reliability: Ensures data loss, duplication, or misordering is prevented.
Synchronization: Both sides agree on initial sequence numbers.
Ready Check: Confirms both client and server are active and ready to send/receive. 

Steps of the 3-Way Handshake :
1.SYN (Synchronize): The client sends a TCP packet with the SYN flag set to the server to initiate a connection, along with an initial sequence number (e.g., seq=100).
2.SYN-ACK (Synchronize-Acknowledgment): The server receives the SYN, and replies with a packet that has both the SYN and ACK flags set. It acknowledges the client's request (ack=101) and sends its own sequence number (seq=300).
3.ACK (Acknowledgment): The client receives the SYN-ACK and sends a final acknowledgment packet (ACK flag) to the server (ack=301).

Flags in TCP :
1.SYN (Synchronize): Initiates a connection by synchronizing sequence numbers between sender and receiver.
2.ACK (Acknowledgment): Acknowledges the successful receipt of a packet. It is used in all packets after the initial SYN.
3.FIN (Finish): Gracefully terminates a connection, indicating no more data will be sent.
4.RST (Reset): Abruptly aborts a connection due to errors, unexpected behavior, or rejected requests.
5.PSH (Push): Forces data to be sent immediately to the application rather than waiting for the buffer to fill.
6.URG (Urgent): Indicates that the data in the packet is urgent and should be processed immediately, prioritizing it over buffered data.

# Topic  - using wireshark
Wireshark is a free, open-source network protocol analyzer used to capture and inspect packets in real-time, supporting over 3,000 network protocols across Windows, macOS, and Linux.  It functions by placing the Network Interface Card (NIC) into promiscuous mode, allowing it to view all traffic on the network segment rather than just packets addressed to the specific device. 

Capturing Traffic To begin, download and install Wireshark from the official website, then open the application to view available network interfaces. Select the appropriate interface (e.g., Ethernet or Wi-Fi) and double-click it or press the blue shark fin icon to start the capture.  For long-term troubleshooting, you can configure rolling captures or ring buffers in the capture options to automatically split large files and prevent disk space exhaustion. 

Analyzing and Filtering Data Once the capture is saved as a .pcap file, use the display filter bar to isolate specific traffic.  Common filters include http for web traffic, ip.addr == <IP> for specific devices, or tcp.port == 80 for port-specific analysis. You can combine conditions using logical operators like && and ||, or use the Follow TCP Stream feature to reconstruct and view the full conversation sequence between two endpoints.
