- Open system interconnection model is conceptual framework used to describe how the data travels on a network
- used to describe function of a networking system
- step by step process where data moves from sender to receiver passing through different checkpoints
![[Pasted image 20250822201547.png]]


### Importance of OSI Model
- to standardize the network communication i.e clear structure of data transmission
- allows different networking devices to communicate easily
- helps cybersecurity professionals to identify vulnerability and secure network effictively
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
- protocols like ethernet,  wifi  and PPP(point to point protocol)
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
- Examples: IP(internet protocol), Routers, ICMP (Internet Control Transfer Protocol)
**NOTE**: doesnt care about physical addressing (MAC Addressing ) , and cares only about logical addressing (IP Addressing)
