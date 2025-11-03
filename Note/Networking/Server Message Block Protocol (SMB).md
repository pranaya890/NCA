- client-server communication protocol used for sharing access to files, printers, serial ports and other resources in the network
- carry transaction protocols for inter-process communication
- widely implemented and continues to be one of the most popular solution for file sharing in the workplace
- known as response-request protocol i.e. it transmits multiple messages between the client and the server to establish connection
- works on port 445 supports data encryption and data signing of SMB packets securing more secure means of communication than port 139
- operates in network level but requires lower network level for transport 
- works on TCP/IP connection actually NetBIOS over TCP/IP, NetBEUI or IPX/SPX
>[!Note] NetBIOS is an acronym for Network Basic Input/Output System. It provides services related to the session layer of the OSI model allowing applications on separate computers to communicate over a local area network.

>[!Note] NetBEUI (NetBIOS Extended User Interface) is a non-routable networking protocol developed by IBM 

>[!Note] IPX/SPX stands for Internetwork Packet Exchange/Sequenced Packet Exchange. IPX and SPX are networking protocols used initially on networks



### Usage of SMB protocol
- mainly used to facilitate shared access to the resources on a network
- provides client application with secure and controlled method for opening, reading, moving creating and updating files on remote server
- can communicate with server program configure to recieve SMB client request
### How does SMB work


![[Pasted image 20251103223721.png]]

- series of request-response messages are used to initiate and facilitate communication between devices on a computer network.
- client sends a connection request for initiation 
- when server recieves the request the severs send the connection response to establish two way connection
- when the connection is established the client can access  required server resources for reading writing executing and so on
- due to sharing of resources by network server it is also called server-client protocol


https://www.techtarget.com/searchnetworking/definition/Server-Message-Block-Protocol

### Enumerating SMB
- Enumeration is the process of gathering information on a target in order to find the vulnerabilities, potential attack vectors and aid in exploitation 
- essential for making attack successful in target
- wasting time on exploits that dont work or crash the system is waste of energy
- can be used to gather information of username, password, network information, hostname, application data services or any other information that may be valuable to an attacker
- SMB shares drives on a network for viewing or transferring a file, which may be a starting point for exploring vulnerabilities of network 
- first step of enumeration is port scanning to gather as much information that we can get  about the services, application, structure and operation system of target machine 

#### TOOL: Enum4Linux
- tool used to  enumerate SMB shares on both windows and linux system 
- this tool is basically a wrapper around the tools on the Samba package and makes it easy to quickly gather information from the target pertaining (relating) to SMB 
- Syntax:
``` bash
enum4linux [option] ip
enum4linux -a 192.0.0.1
```
- Basic Tags
![[Pasted image 20251103230230.png]]
