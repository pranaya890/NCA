- Open system interconnection model is conceptual framework used to describe how the data travels on a network
- used to describe function of a networking system
- step by step process where data moves from sender to receiver passing through different checkpoints
![[Pasted image 20250822201547.png]]


### Importance of OSI Model
- to standardize the network communication i.e clear structure of data transmission
- allows different networking devices to communicate easily
- helps cybersecurity professionals to identify vulnerability and secure network effectively
- to troubleshoot network by checking each layer
- provides universal language of networking

![[Pasted image 20250822202547.png]]

### Overview
![[Pasted image 20250822202625.png]]


### Layer 1: Physical layer

- deals with physical connection, transmission and hardware connection for transmission of data
- converts bits into electrical signals
- hardware layer
- actual carrier of raw bits of data
- actual physical connection exist in this layer
- Examples:  Ethernet cable( to connect computer to network) , Coaxial cable, wifi signals and bluetooth (radio waves), optical fibre, even in form of electrical signals in copper wires
**NOTE**:  concerns only on data not on data interpretation
###  Layer 2: Data Link Layer
- ensures data is transferred correctly between  two directly connected devices
- responsible for communication of two directly connected devices (client -router, router -router)
- deals with MAC address (physical addressing), frames and error detection
- protocols like Ethernet,  WiFi  and PPP(point to point protocol)
Examples:  MAC addressing , Ethernet  ( frame relays)
#### Sub layer for Data link layer
1. Media Access Control( MAC): control the devices on a network  to gain access to a medium
2. Logical Link Control ( LLC): for error checking and manage frame instruction

### Layer 3: Network Layer
- Determines how the network are transferred between different devices on different network (routing)
- routing chooses best possible path for reliable and fast data transfer
Functions:
- logical addressing (IP addressing)
- Routing: Decides best path for data transmission
- data packets fragmentation and re assembly
- Examples: IP(internet protocol), Routers, ICMP (Internet Control Transfer Protocol), Google maps to find best route
**NOTE**: doesnt care about physical addressing (MAC Addressing ) , and cares only about logical addressing (IP Addressing)

### Layer 4: Transport layer
- responsible for complete and correct data delivery without error
Function:
- segmentation and re assembly of data
- flow control and error control
- ensures complete data transfer (re-transmission in case of error)
Examples:
- TCP( Transmission Control Protocol) - reliable , ordered and error checked delivery. and  connection oriented. Eg : text chatting
- UDP (User Datagram Protocol)- faster but less reliable, connection less. Eg: online gaming ( slight data loss ruin gameplay) and live streaming
![[Pasted image 20250825201025.png]]
- in TCP the connection begin with SYN (short for syncronization) flag which asks the server if it is ready to connect, then the server sends back SYN+ACK to client which acknowledges the signal received and sends the SYN flag signaling ready to connect. finally the client replies ACK which acknowledges the signal received and connection is established this process can be known as  TCP three way handshake
-  in UDP the sever request the data and client responds by sending the data there is no acknowledgement so it transfers only data but data flow and server locations are unknown or the data is delivered or not
### Layer 5: Session Layer
- responsible for establishing,  managing and termination connection
- maintains dialog control between computers ( half duplex, and full duplex)
Examples: online banking, login to a website,  video calls, Network file system (NFS), Remote  Procedural Call( RPC)
![[Pasted image 20250825202532.png]]
here the request and response in sender and receiver respectively for sender and receiver for connection is manages by session layer.

### Layer 6: Presentation Layer
- responsible for formatting, encrypting and  compressing of data so it can be properly understood by the receiver application
- handles data formatting and is responsible for encryption / decryption for security purposes
- Examples: Encryption (Secure Socket Layer(SSL)/Transport Layer Security (TLS), character encoding ( ASCII, Unicode), Date compression ( ZIP, MP3, JPEG) 
![[Pasted image 20250825204957.png]]

### Layer 7:  Application Layer
- layer where application  and network services interact
- closest to end user
- provides user interface and supports application like web browsers, email client etc
- interacts with software  applications to implement network services
- Examples: HTTP(Hypertext Transfer Protocol), FTP( File transfer Protocol), DNS ( Domain Name Server), SMTP ( Simple Mail Transfer Protocol)
- layer where user directly  interact with data through application



![[Pasted image 20250916104712.png]]