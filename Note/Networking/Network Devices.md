### Routers ( The traffic Detectors )
- decides the best path for data to travel between different Networks
- connects different network together 
- The router routes traffic from  devices to the internet while making sure responses come back to the correct device.
- Functions: 
- connects to different network 
- uses Network Address  Translation (NAT) to allow multiple device use a single public ip
- uses dynamic routing protocol  (RIP,OSPF, BGP) to determine best path
>[!note] a process where  router can forward data via different route for given destination based on current condition of communication circuit is dynamic routing
>RIP (routing information protocol):  distance vector routing protocol via number of hops allowed in path
>OSPF (Open Shortest Path First)

- provides basic firewall functionality i.e. blocks suspicious connection
- key router ports: WAN( connects to the internet)
				: LAN( connects to local devices)
-  router  can also have DHCP server built in it
### Switches ( the internal connector)
- like a high speed traffic cop inside a network
- connects multiple devices within the same local network
- efficiently directs data only to intended receipent
Function:
- connects multiple devices within a local network
- uses MAC address to determine  where to forward traffic (Layer 2)
- reduce network congestion by sending data only to correct destination
- support VLAN to seperate traffic logically
Types:
- unmanaged switch: simple, no configuration is required
- managed switches : advanced, configurable for VLANs, QoS and security policies
### Firewalls (the security guard)
- is a security device that controls incoming and outgoing network traffic based on  security rules
- allows authorised traffic in and blocks any suspicious 
Function: 
- filter traffic based on rules ( allow HTTP traffic, block FTP traffic)
- can be hardware based (physical firewall appliance) of software based ( windows defender firewall)
- uses packet filtering, stateful inspection, and deep packet inspection( DPI) for security
- protect agains cyber threats like DDoS (Distributed Denial of Service ) attack, unauthorized access and malware
Types of Firewall:
- Packet Filtering Firewall: examines each packet header (source/destination IP, port)
- Stateful Inspection: tracks active connection and allows  only expected response
- Next-Gen Firewalls (NGFWs): includes deep packet inspection, intrusion prevention, and advance threat protection
 More on this : 
 Devices like Hubs, Modems, Access Point, Bridge  Gateways  Load balancer and repeater


