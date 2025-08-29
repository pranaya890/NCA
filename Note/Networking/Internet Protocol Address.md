Internet Protocol (IP) Address is a unique string number assigned to each devices connected in computer network
It is an identifier of a device on a network
Sending/ Receiving address is identified using IP address
to know class of ip address we need to know 
enables routing of information across global network

Examples: `192.168.100.1`

### Network and Host part of IP
network part identifies the network
and host part specifies the device in the network


![[Pasted image 20250828200728.png]]

### Types of IP
- public ip: used in internet
- private ip: used within local network


![[Pasted image 20250828191101.png]]



### IPv4: The Classic Workhorse
- widely used
- 32-bit address scheme i.e. $2^{32}$ =4294967296=4.3 billion approximately
- which are running out
- Ex: 192.168.100.1
- `.` sign separates 8-bit of address which is equals to 1 byte of address
each part ranges from 0-255

### Subnetting in IPv4
- subnetting allows  larger network to be broken down into smaller manageable sections 

### Subnet Mask 
- 32 bit number used in ip addressing  to divide ip address into two parts
- network part and host part
IP address: `192.168.10.1`
Subnet Mask: `255.255.255.0` => `11111111.11111111.11111111.00000000`
- first 24 bit  are for network and last 8 bit are for host within that network
#### Common subnet Masks
- `255.255.255.0`: for small networks upto 254 devices
- `255.255.0.0` : for medium networks upto 65534 devices
- `255.0.0.0`: for  larger network upto 16.7 million devices

### Address Classes of IPv4 
class A: 1-126
class B: 128-191
class C: 192-233
class D: 224-239
Class E: 240-254
 127 is for localhost technically because of first octet  it should lie in A but it is for localhost so it is reserved
 ![[Pasted image 20250828210140.png]]

### Introduction to CIDR (Classless Inter-Domain Routing)
- CIDR allows more efficient use of IP address by removing class limitation
- consist of an IP address  followed by slash and the number of network bits

### VLSM (Variable -Length Subnet Masking)
- Allows network to use subnets of different sizes based on requirements
- enables more flexible subnetting, preventing IP address wastage


### DNS
- converts human readable domain (www.example.com) into ip address (eg  14.24.1.0)
- working: browser sends request to  DNS server then DNS server responds with corresponding IP that is mapped
- Key Components:
			DNS server: resolves the names
			DNS Records: A(for IPv4), AAAA(for IPv6), CNAME (Canonical Name), MX(Mail Exchange)
- Use Cases: easy navigation, vital for web processing

### Address Resolution Protocol (ARP)
- resolves IP address to MAC address on a local network
![[Pasted image 20250829210740.png]]
- broadcast request to find MAC address for given IP
- host with matching IP responds with its MAC address
- basically oi ip tero mac address dey ta 
- ARP cache is the temporary storage of resolved IP to MAC mappings









## Media Access Control Address
MAC address is physical address of a  computer
it is unique identifier assigned to network device
spoofing it can help us to avoid tracking or access network that devices based on MAC address
if a network block a device, the device MAC address can be changed to mimic/imitate an allowed one.
48 bit hexadecimal number (eg: 00:1A:2B:3C:4D:5E)
layer 2 connection in local network
	

### DHCP server
- Dynamic Host Configuration Protocol
- is network management protocol in IP
- it automatically assigns IP and  other communication parameter using client server architecture
- eliminates need of individually configuring networking parameters and avoid IP conflict
- process: discover, offer, request acknowledgement (DORA)

### ICMP (Internet Control Message Protocol)
- used for network diagnostics  and error
- Functions:ping(echo request and reply) and traceroute ( path tracking)
- Types of ICMP messages: echo request/replies, destination unreachable, time exceeded

### Network Address Translator ( NAT)
- technique that maps multiple private IP address to a single public IP address
Types of NAT:
Static NAT:  one to one mapping
Dynamic NAT:  Maps private IPs to available public IPs dynamically
PAT(Port Address Translator): many to one  using port numbers


### IPv6 Addressing
- developed to provide a virtually limitless number of  addresses
- 128 bit address
- $2^{128}$ = 340 undecillion 