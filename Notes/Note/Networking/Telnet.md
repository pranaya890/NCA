it is a command line tool that lets us connect to another computer over a network, like internet  similar to ssh
its like making remote phone call to computer
but it can only receive and transfer plain text from my computer to a remote computer.
mostly replaced by ssh
it is not very secure because its services can be exploited and it can send and receive text and every body can read.
``` Shell
telnet [options] [host] [port]

```

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
