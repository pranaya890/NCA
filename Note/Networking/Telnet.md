- teletype network protocol
- used for remote terminal connection
it is a command line tool that lets us connect to another computer over a network, like internet  similar to ssh
its like making remote phone call to computer
but it can only receive and transfer plain text from my computer to a remote computer.
mostly replaced by ssh
it is not very secure because its services can be exploited and it can send and receive text and every body can read.
``` Shell
telnet [options] [host] [port]

```

some services on  machines are 
- Echo server : this server echos everything we send to it, default port 7
- daytime server: replies current date and time  default port  13
- web (HTTP ) server : serves webpages  default port 80
Note: echo and daytime server are  considered security risk  and should not run 
Note : to close connection use  `CTRL + ] `

in short:
- Telnet is an application protocol that allows users to connect to and execute commands on a remote machine running a Telnet server.
- A Telnet client is used to establish the connection with the Telnet server.
-  Telnet sends all communication in plain text, including usernames and passwords.
- It has no encryption or security mechanisms, making it vulnerable to interception and attacks.
- Because of this, Telnet has largely been replaced by SSH (Secure Shell), which encrypts transmitted data for secure communication.
- The user connects to the server using the Telnet protocol.
- This is done by typing the telnet command in a terminal or command prompt.
- After connecting, the user can execute commands on the remote server via the Telnet prompt.
- Connection syntax: `telnet [IP address] [port]`
Example: `telnet 192.168.1.10 23`
Port 23 is Telnet’s default port.

### Exploiting telnet
Telnet is insecure: no encryption, sends all communication in plain text  
Telnet generally has poor access control  
Telnet client and server may have CVEs  
 CVEs info  at - [https://www.cvedetails.com/](https://www.cvedetails.com/) and - [https://cve.mitre.org/](https://cve.mitre.org/)   
CVE = Common Vulnerabilities and Exposures (publicly disclosed security flaws)  
More likely to find exploitable telnet misconfigurations than protocol bugs  
From enumeration: a poorly hidden telnet service is running on the machine  
From enumeration: the telnet service is labeled “backdoor”  
From enumeration: possible username “Skidy” is implicated  
A reverse shell gives command/code execution on the target machine  
A reverse shell is where the target connects back to the attacker’s listening port  
The attacker must run a listener to receive the reverse connection  
Using telnet as an initial foothold can lead to obtaining a full reverse shell  
we can connect to telnet using 
``` Shell
    telnet [ip] [port]
```


- to start the TCP dump listener
- ![[Pasted image 20251110212729.png]]
- This command captures ICMP packets (like ping requests and replies) traveling over the `tun0` network interface, using `tcpdump`.



### Netcat (nc)

it is very very powerful tool

`nc ` is a command line tool used to send and receive data over the network. 
it can send or receive files over a network 
unlike `telnet` it can transfer text binary and files too.
``` Shell
nc [-options] hostname [port]
nc google.com 80 # securing a TCP (transfer control protocal) connection
```

we can combine echo with `nc`  to send message to a TCP server
``` Shell
echo "Hello Server" | nc ip_address port 
```

netcat can also function as sever by listening its inbound connections on arbitrary port.
it shovels data back and forth until there isnt any more left. it doesnt care if it run in client or server mode

it is a tool used to read/ write data across network 

we can use netcat to connect to the server in same network  through tmux sessions
``` Shell
nc localhost <portname> # to connect to the port
nc localhost 9005
nc -lnvp <portname> # to host a liostening port 
nc -lnvp 9005
```
`-lnvp` is combination of option of `nc` that says listen to port,  numeric only ip address, v is for more than 2 verbose i.e. for receive or send one line at a time. and p is port

### Open SSL
it is a toolkit for cryptography for keeping it safe and private.
used for creating and managing SSl?TSl certificates
used for generating cryptographic keys

``` Shell
openssl command [option]
```

### S_client
it helps to connect a remote server securely using SSL/TSL
it can also be interpreted as secure version of `telnet` or `nc`

``` Shell
openssl s_client []
```

###  Nmap (Network Mapper)
free and powerful command_line tool for network exploration and security
used to scan computers on a network
study the physical connectivity of a network
discover devices on the network and their connectivity
designed to rapidly scan large networks, but works fine in single host.
output of nmap is list of scanned targets.
``` Shell
nmap -p <port> 
```
option: `-sV` stands for service version. helps us to determine the what is running and which version in addition to 


#### Ncat and nc
in `nc` SSL/TLS  is not supported and in `ncat` SSL/TLS are supported 
for using ssl we have to use `ncat` 


### Sockets in Computer Network 
sockets in computer network can be defined as the one endpoint of two-way communication network
![[Pasted image 20250721210306.png]]
end point is combination of IP address and a port number
each TCP (transmission control protocol ) can be uniquely identified by using its two end point


### File Transfer Protocol
- FTP stands for File Transfer Protocol
- It is used for remote transfer of files over a network
- Works on a client-server model
- Uses two channels:
- command (control) channel for sending commands and responses
- data channel for transferring data
- The client initiates a connection to the server
- The server verifies login credentials and opens a session
- Once connected, the client can execute FTP commands on the server
- FTP can operate in two modes:
- Active mode: client opens a port and listens, server connects to it
- Passive mode: server opens a port and listens, client connects to it
- Separation of command and data channels allows commands to be sent while data transfers are ongoing
- This improves efficiency during large or slow file transfers
- Technical details and specifications are defined in RFC 959 by the Internet Engineering Task Force (IETF)
- Reference link: [https://www.ietf.org/rfc/rfc959.txt](https://www.ietf.org/rfc/rfc959.txt)
### Enumeration FTP
- Enumeration is essential for attacking network services and protocols.
- Use `nmap` for effective port scanning; consult `tool -h/--help` or `man [tool]` if stuck.
- FTP client required to interact with FTP servers; test by running `ftp` and looking for the `ftp>` prompt.
- If no FTP client is present, install with `sudo apt install ftp`.
- Target: exploit anonymous FTP login to access files that may enable shell access.
- Anonymous FTP access can expose sensitive files and lead to privilege escalation or shell pop.
- Some FTP servers reveal home-directory existence via `cwd` responses issued before authentication. (Change Working Directory)
- Legacy `in.ftpd` and similar servers may show different `cwd` responses for existing vs. non-existing home directories.
- Pre-auth `cwd` probing can indicate user accounts on vulnerable/legacy systems.
- The `cwd` pre-auth vulnerability is documented: Exploit-DB exploit #20745.
- Always check FTP server responses and available files after anonymous login for potential exploits.

### Exploiting FTP
- FTP command and data channels are unencrypted; traffic can be intercepted and read.
- Man-in-the-middle attacks (e.g., ARP poisoning) can capture FTP credentials and data.
- JSCape demonstrates ARP-poisoning to intercept FTP traffic.    
- Weak or default passwords on FTP servers are a common exploitation avenue.
- From enumeration: FTP server found and a possible username discovered.
- Next step: brute-force the FTP password using an online password-cracking tool.
- Hydra is a fast online password-cracking tool supporting 50+ protocols (including FTP).
- Example Hydra command: `hydra -t 4 -l dale -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp`
- `hydra` — runs the Hydra tool.
- `-t 4` — number of parallel connections per target.
- `-l [user]` — specifies the username to attack.
- `-P [path]` — path to the password dictionary file.
- `-vV` — very verbose mode; shows each login+password attempt.
- `[machine IP]` — target machine IP (example: `10.10.10.6`).
- `ftp` — specifies the protocol to attack.
- Run Hydra responsibly and only against systems you have permission to test.