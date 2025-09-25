- while performing security audits the first and foremost thing is mapping the given system 
- i.e we have to know what things are running in target
Domain Controller is the server computer that respond to security authentication request within windows domain
- first stage is establishing the map of the landscape called port scanning 
- when computer runs a network service the computer opens a path called port to receive connection


- open source tool used for network exploration and security auditing
- designed to rapidly scan large network  and works fine with single host too
- uses raw ip packets in novel ways to determine what hosts are available on network
- `nmap` will connect to each port of target in turn
- depending on the response of port the port can be considered open closed or filtered( usually by firewall)
- by using `nmap` we can enumerate which services are running on each port manually or by using `nmap`
- can be accessed in terminal by using keyword `nmap` followed by some of switches or command argument 
- help menu for `nmap` is `nmap -h` or `man nmap`
``` Shell
nmap [target]

```
information we can get from nmap:
- what services are those host offering?
- what operating system are they running?
- what type of packet filter or firewall are being used?

---
commonly used for security audits, many system and network administration
Output of Nmap is list of scanned targets with supplemental information on each depending on the options used
the table list the port number and protocol, service name and state 
state is either open , filtered, closed or unfiltered 
open means the application on target machine is listening for connection/packets on port
filtered means the firewall filter or other network obstacle blocking the port so that nmap cannot tell the port is open or closed
closed port have no application listening on them though they could open at any time
port are classified as unfiltered when they are responsive to Nmap probes but `nmap` cannot determine whether they are opened or closed 
`nmap` reports the state combination open|filtered and closed|filtered  when it cannot determine which of this two state describe the port
port table may also include software version detail when version detection has been requested 
Nmap can provide further information on targets, including reverse DNS names, operating system guesses, device types, and MAC addresses.

---
some times normal output is not enough we can use aggressive mode using `-A`
it is always recommended to uses `-vv` as option to produce a verbose output



### Types of scan
- three basic types of scan
- TCP connect scan (-sT)
- SYN "Half-open" Scans (-sS) {A **half-open scan** (often called a **TCP SYN scan**) is a common network reconnaissance technique used to discover open TCP ports on a target system without completing a full TCP connection}
- UDP connect scan (-sU)
>[!note]
>In a half-open scan:
>The scanner sends only the **SYN** packet to the target port    
>If the port is **open**, the target replies with **SYN-ACK**.
> Instead of sending the final **ACK**, the scanner sends a **RST (reset)** or simply ignores the SYN-ACK.


---

### TCP SCAN
- if Nmap sends a TCP request with the _SYN_ flag set to a **_closed_** port, the target server will respond with a TCP packet with the _RST_ (Reset) flag set. By this response, Nmap can establish that the port is closed.
![[Pasted image 20250925205117.png]]
- If the request is sent to an _open_ port, the target will respond with a TCP packet with the SYN/ACK flags set. Nmap then marks this port as being _open_ (and completes the handshake by sending back a TCP packet with ACK set).
![[Pasted image 20250925210016.png]]

- if the port is open and hidden behind firewall: Many firewalls are configured to simply **drop** incoming packets. Nmap sends a TCP SYN request, and receives nothing back. This indicates that the port is being protected by a firewall and thus the port is considered to be _filtered_.
---
 it is very easy to configure a firewall to respond with a RST TCP packet. For example, in IPtables for Linux, a simple version of the command would be as follows:

`iptables -I INPUT -p tcp --dport <port> -j REJECT --reject-with tcp-reset`
This can make it extremely difficult (if not impossible) to get an accurate reading of the targets

---

### Advantages of SYN scan as hacker
- it can be used to bypass older intrusion detection system (a security tool that monitors network traffic or computer systems for signs of unauthorized access misuse, or malicious activity ) as they are looking out for a full three way handshake but this is no longer the case with modern IDS
-  SYN scans are often not logged by applications listening on open ports, as standard practice is to log a connection once it's been fully established. Again, this plays into the idea of SYN scans being stealthy.
- Without having to bother about completing (and disconnecting from) a three-way handshake for every port, SYN scans are significantly faster than a standard TCP Connect scan
### Disadvantages 
- They require sudo permissions in order to work correctly in Linux. This is because SYN scans require the ability to create raw packets (as opposed to the full TCP handshake), which is a privilege only the root user has by default.
- Unstable services are sometimes brought down by SYN scans, which could prove problematic if a client has provided a production environment for the test.


>[!warning]
>SYN scan if run without  sudo permissions, Nmap defaults to the TCP Connect scan 
