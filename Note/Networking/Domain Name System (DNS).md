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