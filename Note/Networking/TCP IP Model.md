- commonly known as IP suite
- Transmission Control Protocol / Internet Protocol 
- used to interconnect  devices on internet
- defines how data is transferred in a network
- practically this model is used in modern computing
### Layers
![[Pasted image 20250827200106.png]]
1. Application Layer:  high-level protocols like HTTP, FTP, and SMTP operate. layer where user applications interact with the network.
2. Transport Layer: responsible for providing communication services between systems. most important protocols in this layer are TCP (Transmission Control Protocol) and UDP (User Datagram Protocol). TCP provides reliable communication, while UDP is used for low-latency applications that can tolerate some data loss.
3. Internet Layer:   primary protocol in this layer is IP (Internet Protocol). It's responsible for routing packets of data from the source to the destination across different networks. IP addressing and routing protocols like ICMP (Internet Control Message Protocol) come into play.
4. Network Access Layer (Link Layer):  corresponds to the physical network hardware and protocols, like Ethernet or Wi-Fi, and is responsible for moving data across the physical network.  handles framing and addressing within the local network.


![[Pasted image 20250827201656.png]]

### IP header
- used for routing data packets across networks
- added at the network layer of the TCP / IP model
- key function is to ensure data packets is sent from source to destination correctly
![[Pasted image 20250827202101.png]]

version: ip version being used IPv4 or IPv6-4bit
Header length: indicate length of IP header-4bit
Type of service: how packets should be handled in terms of priority (QoS) -8bit
Total Length: specify length of entire packet-16 bit
identification: to identify fragment  of original IP - 16 bit
flag : to control or identify fragments-3bit
 Fragment Offset: Represents the number of Data Bytes ahead of the particular fragment in the particular Datagram. Specified in terms of number of 8 bytes, which has the maximum value of 65,528 bytes. 
Time to live:Datagram’s lifetime (8 bits), It prevents the datagram to loop through the network by restricting the number of Hops taken by a Packet before delivering to the Destination.
Protocol: Name of the protocol to which the data is to be passed (8 bits) 
Header Checksum: 16 bits header checksum for checking errors in the datagram header 
Source IP address_:_32 bits IP address of the sender 
Destination IP address_:_ 32 bits IP address of the receiver 
Option: Optional information such as source route, record route. Used by the Network administrator to check whether a path is working or not.

Function of IP header
routing, fragmentation and time to live

### TCP header 
- added at transport layer and is used for  ensuring reliability and ordered delivery of data between two system
- complex than ip header but guarantees error free data delivery in correct order



![[Pasted image 20250827204244.png]]

sequence port ( 16 bit) port number of sending device
destination port (16 bit) port number of receiving device
sequence number (32 bit) ensures ordered delivery by keeping track  of bytes in data stream
acknowledgement number (32 bit): confirms receipt of data by acknowledgement  the last successfully  receiver
data bus( 4 bits): indicates the size of TCP header
flag (6 bits): control bits to manage connection 
EG flag:
SYN: syncronization flag to sync sequence number
ACK: acknowledgement flag
FIN: termination flag
RST: Reset flag for connection
PSH: pushes the data to application layer
URG: Marks data as urgent


Function of TCP header
connection establishment using 3 way handshake
reliable data transfer by using sequence and acknowledgement number
flow control so that sender doesn't overwhelm receiver
error detection by  checksum that ensures header and data are not corrupted  during transmission


### User Datagram Protocol (UDP)
- UDP is a connectionless protocol operating at the transport layer (Layer 4)
- Does not establish a connection before sending data
- Does not provide delivery acknowledgment
- Faster but less reliable than TCP
- No error checking or retransmission mechanisms
- IP address identifies the host
- Port number identifies the sending and receiving processes
- Port numbers range from 1 to 65535
- Port 0 is reserved
- Range comes from $2^{16}$−1= 65535
- UDP is like standard mail without delivery confirmation
- Cheaper and faster, but delivery is not guaranteed
- TCP is used when delivery acknowledgment is required
- TCP is connection-oriented and reliable
