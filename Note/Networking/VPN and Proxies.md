- VPNs and Proxies are crucial tool for privacy, security and bypassing restrictions
- helps to mask our identity and route our traffic through another server

### Virtual Private Network (VPN)
- technology that creates secure encrypted tunnel between our device and  a remote server
- tunnel protects our data from prying (interested in a person's private affairs) eyes such as ISPs, hackers  or government survelliance
- allows us to access resources as if i were in another location
#### How VPN works?
- ![[Pasted image 20260202204301.png]]
- we connect to a VPN server using VPN client
- our data is encrypted before leaving our devices
- the encrypted service is sent back to VPN server, when it is decrypted
- VPN server forwards the request to  the destination website or service
- the response follows the same path back, encrypted all the way back to device
#### Why VPN is useful in Real life scenarios
- Privacy and  Anonymity
- Bypassing geological restriction
- securing public wifi : protect from Man in the MIddle (MITM) attach on open WIFI
- accessing private network: for remote workers  to access internal company network
- Hiding Network Activity From ISP: ISPs can no longer monitor or throttle internet speed based on my usage


![[Pasted image 20260202205148.png]]
### Proxy Server
- a proxy server acts as an intermediary between our device and internet
- instead of connecting device directly to internet our traffic goes through the proxy server first
#### How proxies work?
![[Pasted image 20260202205454.png]]

![[Pasted image 20260202205512.png]]
- we send a request to access a resource say website
- proxy server receives the request and forwards it to the destination
- the server responds to proxy server instead of me
- the proxy server sends the response back to the host
- since the website sees the ip address of proxy server the host ip is hidden

#### Types of proxies and their usage
1. Forward Proxy (Regular Proxy):
	- used by individual user to hide the IP or bypass restriction
	- Eg: using a public proxy to access blocked website
2.  Reverse Proxy:
	- sits in front of server to filter incoming request
	- used by companies to protect server from direct attacks and load balance traffic
3. SOCKS Proxy( SOCKS5)
	- works at Layer 5 (session layer ), meaning it can handle more than just web traffic
	- used for gaming, P2P and secure traffic routing
4. Transparent Proxy
	 - users are unaware of its presence ( often used in schools and companies )
	 - used for content filtering and monitoring

### Difference between VPNs and Proxies
![[Pasted image 20260202210449.png]]

### Summary
Both **VPNs and proxies** help you stay anonymous online, but they serve different purposes.
- **VPNs** encrypt **all your traffic** and provide privacy, security, and access to restricted networks.
- **Proxies** only change your **IP address** for specific applications but don’t encrypt traffic.