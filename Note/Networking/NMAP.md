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

### UDP scan
- switch for nmap UDP scan is  `-sU`
- when packet is sent to UDP port  there should be no response also  called `open|filtered`
- it can be used to suspect the port could be fire-walled
- if it gets UDP response which is very unusual then the port is marked open
- if  there is no response from the port on request then the request is sent again for double check if still there is no response  the port is marked `open|filtered`
- when a packet is sent to closed port the target port should respond with ICMP packet containing the packet  containing the message that the port is unreachable which identifies the closed port
- due to this difficulty in identifying open or closed port UDP scan is comparitively slower
- for this reason it is good practice to run  an NMAP with  `--tcp-ports <number>` enabled
``` Shell
nmap -sU --top-ports 20 <target>
#this will scan 20 most commonly used UDP ports
```
- when scanning UDP ports Nmap usually sends completely empty request just raw UDP packets 
- for ports which are usually occupied by well known services will  instead send a protocol-specific payload which is more likely to draw out a response from which a more accurate result can be drawn

### NULL, FIN and Xmas scan
- these scans are less commonly used than any other 
- they tend to be stealthier, relatively speaking than  a SYN "stealth" scan


NULL scan: 
- (-sN) are the scan used when the TCP request is sent without a flag
- In null scan as per RFC the target host should respond with RST (Reset flag) if the port is closed
![[Pasted image 20251013131850.png]]
- in above screenshot there is RST and ACK flag in response to  NULL scan

FIN scan: 
- -sF scan sends a FIN flag instead of sending empty packets usually to close an active connection
![[Pasted image 20251013132309.png]]

Xmas scan:
- -sX scan sends a malformed TCP packets and expects a RST response for closed ports 
- it is referred to an xmas scan because  the flag set by it  PSH, URG and FIN give it the apeallling blinking christmas tree when viewed as  a packet capture in wireshark 
- ![[Pasted image 20251013132747.png]]


- the open ports with these scans are also identical and is very similar to UDP scan
- if the port is open there is no response to malformed packet
---------
-----

- these scans only identify packets as open|filtered, closed or filtered
- If a port is identified as filtered with one of these scans then it is usually because the target has responded with an ICMP unreachable packet.


### ICMP network scanning
- our first objective is to obtain a "map" of the network structure or, 
- in other words, we want to see which IP addresses contain active hosts, and which do not.
- we can do this by using nmap to perform a "ping sweep"
- in this scan nmap sends a ICMP packet to each possible IP address for the specified network
- when it receives a response it marks IP address that responded as being alive
- we use `-sn` switch for performing a ping sweep with ip ranges with `-` or CIDR notation
``` Bash
nmap -sn 192.168.0.1-254 #using Hyphen
nmap -sn 192.168.0.10/24 #CIDR notation
``` 
- `-sn` switch tells Nmap not to scan any ports  --forcing it to rely primarily on ICMP echo packets or ARP request on local network if run with sudo or directly as root user to identify target
- `-sn` switch also cause nmap to send a TCP SYN packet to port 443 to the target  as well as TCP ACK (or TCP SYN if not run as root ) packet to port 80 of the target

### Nmap Scripting Engine (NSE)
- it is a script written in lua programming language
- it can be used to scan variety of things from scanning vulnerabilities to automating exploits for them
- particularly used for reconnaissance 
- some categories in NSE are:
     - safe: wont effect the target
     - intrusive: not safe likely to affect the target
     - vuln: scan for vulnerabilities
     - exploit: attempt to exploit the vulnerability
     - auth: attempt to bypass  authentication for running services ( Eg: login to FTP server anonymously)
     - brute: attempt to bruteforce credentials for running a services
     - discovery: attempt to query running services for further information about the network ( eg: query an SNMP server)

>[!Note]
>Simple Network Management Protocol (SNMP) is an internet standard protocol used to monitor and manage network devices connected over an IP network, including routers, switches, servers, printers, and other hardware.

>[!Alert]
>https://nmap.org/book/nse-usage.html for details


#### running a NSE script
- the switch for activating NSE script  from the `vuln` category is `--script=vuln
- for safe category is `--script=safe`
>[!note]
>  only scripts which target an active service will be activated

- to run a NSE script we can use `--script=<script_name>`  
- Example: `--script=http-fileupload-exploiter`
- multiple script can be run simultaneously by separating with commas
- Example: `--script=smb-enum-users,smb-enum-shares`
- for running a script that require argument: argument can be passed using `--script-args` nmap switch
- we can use `http-put` script to upload file using put method
- this takes two argument :
	- URL to upload the file to
	- File location on disk
- for Example: `nmap -p 80 --script http-put --script-args http-put.url='/dav/shell.php',http-put.file='./shell.php'`
>[!note] 
>argument are separated by commas and connected to corresponding script  with periods
>i.e `<script-name>,<argument>`

- https://nmap.org/nsedoc/ for more script and its corresponding argument
