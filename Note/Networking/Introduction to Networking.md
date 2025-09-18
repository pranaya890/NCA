- Networking means the process of connecting multiple devices to share data and resources
- enables communication between different system over local or global network like internet
- can be wired or wireless
- key purpose is to allow devices to exchange information efficiently
- relies on rules on protocol for how to transmit data between devices
- these protocols ensures the data transmits to receiver without any error
- while visiting a website our devices sends a request using these protocols for a resource and it responds with the requested resource
## Why it matters?
- it is foundation of modern communication system
- understanding of how data flows across network is essential for pentesting (penetration testing)
- pen-testers assess the network by identifying weakness in how system are connected, communicating and authenticating
- networking knowledge helps pentesters to exploit vulnerabilities like open ports, misconfigured services, insecured protocols simulating how attackers may infiltrate into network
- its knowledge is crucial in identifying attack vectors in cybersecurity
- concepts like IP addressing, DNS, protocol(HTTP,FTP), firewalls and routers all play vital roles in how to communicate and how and where attacks can be launched
- knowing network operations allows tester to map out potential attack surfaces, understand impact of vulnerability and take effective counter measure
- pentester uses tools like  Nmap to scan networks for open ports and active services
- wireshark to analyze network traffic 
- metasploit to exploit network based vulnerabilities

### Key components of networking
- Nodes( devices)
-  Links ( wired/ wireless)
- Data 
### Terminologies in networking
- IP address: unique address given  to identify device on a network
- MAC address: unique hardware identifier of a device like wifi adapter
- ports: virtual entry points where communication happens. common ports 80(HTTP) and 433(HTTPS)
- packets: units of data sent over a network
- Protocols: Set of rules to be followed for communications
-  DNS(Domain Name System): translates human readable domain names to ip address
- Firewall: security system that controls network traffic allowing or blocking connection based on connection rules
- Router: device that directs network traffic and connects different networks
- subnet: smaller network within larger network, used to organize and manage device effectively
- Bandwidth: capacity of network to transfer data
### Types of network on the basis of geographical area
- LAN: Local Area network, used in homes offices etc where devices are connected to switch/router which is connected to ISP 
- WAN:  wide area network, basically connection of one or more LAN
- MAN: metropolitan area network, covers a large area but smaller than WAN
- PAN: personal area network, few meters range, slower data transmission rate, eg bluetooth

## Network Topology
- Ring Topology : connected in ring like structure, data flow is unidirectional, data packets collision is reduced, single device failure can disrupt the whole network
- Bus topology: different nodes are connected to a single bus, cost effective for small network, frequent data collision, disruption on bus can put down entire network
- Star Topology: connected to central hub, hub maintains one to many connection, failing of hub fails all network, easy to install and manage, failure of other nodes excluding hub creates no effect
- Mesh Topology: every node is connected to every other node,  high redundancy and reliability, expensive and complex to install
- Hybrid Topology: combination of multiple topologies, flexible and scalable, complex to configure and manage.
	