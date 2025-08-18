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
it is 




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
