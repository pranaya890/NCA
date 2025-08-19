Managing network and analysing the network is important part of linux

#### `ifconfig` Command
Interface Command is command line tool in linux
gives information about [[Internet Protocol Address]]
(IP Address),  Media Access Control Address( MAC), netmask(filter to separate ip address into network address and host).
Used for:
	1. View Network Interface Detail
	2. Configure Network Interface
	3. Troubleshoot  Network


![[Pasted image 20250708145157.png]]
this net has `192.168.1.73` IPV4 address an netmask `255.255.255.0` and network is on i.e `UP` and has IPV6 address `2400:1a00:b080:b70:a00:27ff:fe8d:99e8`
it also has `lo` loop back running

### `iwconfig` 
`iwconfig` is used to check wireless network devices
![[Pasted image 20250708150111.png]]
no wireless network devices are connected

### Checking Routing Table

Set of rules used by devices to determine where to send network traffic
contains information about network destination and gateways and interfaces to decide best path for data
![[Pasted image 20250708151332.png]]

routing table shows  how network traffic is directed.
it shows the default gateway is `192.168.1.754` non local traffic are routed through default gateway.  

#### Testing Network connectivity with ping
`ping` is a network  diagnostic tool used to test connectivity between devices using  ICMP echo request.
ICMP echo request checks if a device network is reachable and responsive.

``` Shell
ping google.com
```

### Changing Network Information
changing IP address and other network configuration is a crucial skill, enabling us to access various network while appearing as legitimate device
During penetration testing, ip can be modified to simulate different devices on network to test security measures without revealing true identity
It can also be used in bypassing geo-restriction i.e. accessing the network from different region

#### Changing IP address
we can use `ifconfig` to change the `eth0` configuration.
``` Shell
sudo ifconfig eth0 192.168.1.223 netmask 255.255.255.1  broadcast 192.168.1.255
 
```

### Changing MAC address
- MAC is unique identifier assigned to a device
- spoofing it can avoid us from getting tracked or access network that filter devices using mac address
- if a network block our device we can mimic another mac address and connect to the network
- we can use `macchanger` and `ip` command 
- we can use `ifconfig` and `eth0` command together to change the network information like `ifconfig eth0 down` for disconnect from the `eth0` network using sudo permission
![[Pasted image 20250819200849.png]]
here the `eth0` ethernet was disconnected we can connect using `up` instead of down in above command
- we can change the mac address of our device in 3 steps
		- by shutting down eth0 network interfaces
		- changing the MAC address
		- then enabling eth0 network interface
- we can change mac address by using `ifconfig` with its option `hw`. 
- `hw` here means hardware address `hw ether` means hardware address for ethernet interface
``` Shell
ip ifconfig eth0 hw ether 00:11:22:33:44:55
```
- ![[Pasted image 20250819202138.png]]
### Assigning new ip address from DHCP server
- new ip address can be assigned to our device by using `dhclient` command to remove the current address using its `-r` option then new ip can requested to DHCP server using same dommand
 ```Shell
 sudo dhclient -r eth0 
 sudo dhclient eth0
```





### Manipulating the domain name system
- DNS translates human readable  domain names into ip address
- if hacker modify the DNS they can redirect user to malicious  websites with their knowledge which is called DNS Spoofing or DNS poisioning
- this can lead to malware infection, phising attack  or data breaches
- securing DNS server can be done by encrypted DNS  protocols  like DNS over  HTTPS are essential
#### Dig
- Domain information groper  is linux tool used to query DNS server and  retrive detailed information about domain name,IP address and DNS record
- such as A records (ipv4 addresses) AAAA records (IPv6address), MX records (mail servers), NS records (name servers) and CNAME records (domain aliases)
- example `dig google.com` provides details about google DNS
- it is used for troubleshooting DNS issues, verifying domain configurations and analysing dns responses
- its flexibility and detailed output make it a preferred tool for network administrators and security professionals
#### Changing my DNS server
- DNS server is often changed for enhancing privacy, speed or security 
- we might switch to  DNS services like Google DNS (8.8.8.8) cloudflares DNS (1.1.1.1) for faster and  more secure internet access
- to change dns we can edit `/etc/resolv.conf`
```Shell
sudo nano /etc/resolv.conf
```
![[Pasted image 20250819204352.png]]
- `100.127.255.165` in linux config file the system should use DNS server at that IP  for domain name resolution
- by setting this our system will send all DNS queries to  that IP
- useful in environment where the DNS server provides resolution or filter content
- to add google public DNS to our network we can add following things in `/etc/resolv.conf`
``` Shell
nameserver 8.8.8.8
nameserver 8.8.4.4
```

### Mapping my own IP address
- `/etc/hosts` file in linux allows us to manually map IP addresses and hostnames
- useful for particularly development testing  or blocking specific websites
- we can map domain `mywebsite.local` to our local machine  while devloping website locally by adding line `127.161.100.1 mywebsite.local` to `/etc/hosts` file
- it resolves local server instead of querying external DNS
- we can block websites like`adsite.com`  by mapping `0.0.0.0` effectively redirecting to  an invalid address
- these mapping tools help to control domain resolution  without relying on external DNS server
- to understand further we will use apache server
- `service apache2 start` is used to start apache server
-  `services` command is used for managing system services 
- `apache2` is apache HTTP server  used for open source server
- typically used for hosting websites locally, testing web applications, setting up a development environment
- we can verify it by running `http://10.0.2.15/` in browser or `http://127.0.0.1/`

![[Pasted image 20250819211512.png]]
 - 