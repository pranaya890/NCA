## Ports
- ports are virtual entry points  through with the data  enters or leaves a device
- a devices can have thousand ports but only few hundreds are actively used 
- port are necessary for making multiple network or multiple services available 
- there are total of 65535 ports
- for example different ports are used for loading different webpages on same browser  this is done by establishing connection to remote webserver using different port
- network connection are made between two ports an open port listening to server and  a randomly selected port on my computer
- standard ports can also be altered especially in CTF setting
![[Pasted image 20250922204336.png]]

### Types of port
- Well known port (0-1023):  reserved for popular services like  HTTP, HTTPS and  FTP etc
- Registered Ports (1024-49151): used by application that are not parts of the well known services but still standarized
- Dynamic or Private Ports( 49152-65335): used for temporary (ephemeral) connection
Example are HTTPS use 443 port, HTTP use 80 port  FTP used 20 for data and 21 for control  and SSH uses 22 port

## Common Protocol
- they are like languages that   computer uses to communicate
- define how data are transferred to the network

### HTTP (Hyper Text Transfer Protocol)
- port : 30
- used for transferring web pages and other resources over the internet
- it doesn't encrypt data so it is not considered secured by default

### HTTPS ( Hyper Text Transfer Protocol Secure)
- port- 433
- secure version of HTTP  that encrypts the data and to ensure privacy and security during transmission 
- used by website requiring login information or handling sensitive data
### FTP ( File Transfer Protocol)
- port 20 for data and port 21 for control
- used for transferring files over network 
- port 21 handles control commands while port 20 is used for data  transfer

### SSH (Secure Shell)
- port 22
- secure way to  remotely access and control another computer over a network 
- commonly used by system admin for managing server

### SMB ( Server Message Block)
- port 137-139 and 445
- used for sharing files  and printers  on a network especially in windows environment
- SMB allows application to  read and write to files  and request  services from server program

### ICMP (Internet Control Message Protocol)
- it doesnt uses port
- used for sending error message  and operational information 
- example is ping command which uses ICMP to test connectivity 

## MAC address ( Recall)
- is unique identifier  assigned to the network  interface card (NIC) of  a device
- unlike IP address  which can change MAC address are permanent and assigned at hardware level usually in form of 12 character hexadecimal digit
- Example: `00:1A:2B:3C:4D:5E`
- used in data link layer of OSI model to ensure data is directed to correct physical device is connecting to the network via Protocol like ARP
### ARP Protocol (Recall)
- ARP (Address Resolution Protocol) maps an IP address to a MAC address
- A device needs the MAC address of the destination IP to communicate on the local network
- If the MAC address is unknown, the device sends an ARP request asking who has the IP address
- The device with that IP replies with its MAC address
- ARP is essential for local network communication and is an initial step when two devices communicate on the same network
### DHCP ( Dynamic Host Configuration Protocol)
- Automatically assigns IP addresses, subnet masks, default gateways, and DNS servers
- Eliminates the need for manual IP configuration

### DORA ( Discover Offer  Request Acknowledge)
![[Pasted image 20250922121829.png]]
Discover: the device sends a broadcast to  the network asking for IP address
Offer: DHCP server responds with an offer including an available IP address
Request: The device then request the specific IP address from DHCP server
Acknowledge : the server acknowledge the request , and the device is  assigned  the IP address for a lease time 

## Summary

- Ports help us route traffic to the right service.
- Protocols define how that data should be handled.
- MAC addresses and ARP ensure data finds its way to the correct physical device.
- TCP and UDP control how data is delivered, depending on the need for reliability and speed.
- DHCP makes it easy to configure devices to join the network without manual input.


### NetBIOS
- synonym for Network Basic Input/ Output System 
- provides services related to session layer of OSI  model allowing application on seperate computer to communicate over a LAN
- windows NetBIOS can be found in port 139