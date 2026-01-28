- most essential component of internet that allows us to interact with internet
- provides naming system for computer services on internet
- operates on Client/Server model
- DNS provides name resolution  service to network endpoints
- translates URL or domain name  to corresponding IP
- converts human friendly name of websites to machine readable  IP address
![[Pasted image 20260127181926.png]]
- it initially used UDP but due to reliability security and privacy  it transferred to TCP
- most common types of record: IP address( A and AAAA), 
							: SMTP mail exchanger( MX)
							: name server( NS)
							: pointer for reverse DNS lookup ( PTR)
							: domain name aliases( CNAME)

#### Working of DNS
1. Human friendly domain name:  anything  that we type in web browser address bar
2. DNS lookup: BTS, browser doesnt know what the human friendly domain name means, 
			: until it then resolves it into IP
			: when we hit enter  our browser inititiates DNS lookup to translate domain name to IP
3. DNS Query Process; 
			: checks local DNS cache to see if it already knows the IP, if it does it uses cached Ip to load website
			: if not in cache  browser sends a request to recursive DNS resolver this is provided by ISP or public resolver like google(8.8.8.8) and cloudflare(1.1.1.1)
			: then resolver checks in its cache if not it will go to DNS hiearchy to find authorative DNS server for domain
			: the resolver queries root DNS server which responds with address of Top Level Domain server( TLD) like .com, .xyz etc
			:TLD then responds with  address id authorative DNS server this is final stop where actual DNS record for domain is stored
			: the authorative DNS server  responds with corresponding IP address of domain
			: finally the DNS  resolver sends that IP address  back to browser 
4. DNS caching: after IP address is returned browser and resolver will cache the result for specific amount of time called Time to Live ( TTL) so that subsequent request for domain  wont go through subsequent request process
### Basic DNS Record
- these record are instruction that tell DNS server how to handle request for specific domain 
1. A record ( Address Record):
	- most common DNS record 
	- maps domain to IPv4
	- tells DNS resolver what IP address is associated with  a domain name
	- when a domain is searched it looks up for the A record  to find IP address of the website
	- ![[Pasted image 20260128185243.png]]
	-  in real world  A record is crucial for routing traffic to correct server hosting website or service
	- if `pranayshrestha8.com.np` is hosted on a server  with IP `111.12.13.1` A record will point to that
2.  CNAME Record ( Canonical Name Record): 
- used to alias(an additional name ) one domain to other  
>[!note] Canonical: Standard way of presenting the object as mathematical Expression 
> it provides simplest representation of an object and allows it to be identified in unique way

- used when we want multiple domain name to point to the same website or service
- ![[Pasted image 20260128191052.png]]
- in real world using CNAME record is very common 
- www is typically a CNAME pointing to root domain
3. MX Record ( Mail Exchange Record): 
- used to specify the mail server responsible for receiving email messages for domain 
- if we are sending an email to `@pranayashrestha.com.np` the sending server needs to know where to deliver an email
- ![[Pasted image 20260128191451.png]]
- in real world  companies often have multiple MX record for redundancy 
- if one mail server goes down the the email can be routed to another server  with higher priority number
4. TXT record ( Text record):
- used to store arbitrary text data
- often used for SPF (Sender Policy Framework), which helps to reduce email spoofing by verifying email is coming form authorised server
- TXT record can also be used for  domain verification in services like Google Search Console  or email services
- ![[Pasted image 20260128192149.png]]
- in real world TXT record are  critical for email authentication and security 
- helping to prevent fraud and phishing attack
### Real World Scenario 
 ![[Pasted image 20260128192638.png]]
### Summary
- essential to navigate through internet, allowing us to use easy to remember domain rather than complex IP
- helps to understand behind the scene magic of working of internet
- whether it is web traffic, emails  or security configuration, DNS record help everything run smoothly  and securely
