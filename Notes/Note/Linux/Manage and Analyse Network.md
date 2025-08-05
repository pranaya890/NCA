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