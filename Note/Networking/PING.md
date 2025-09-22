ping command is used to check if a host is reachable across a network and to measure round-trip time for messages sent from the source to a destination
``` Shell
ping <target>
ping google.com
```
- **-i** : specifies the interval (in seconds) between each ICMP echo request. For example, `ping -i 5 example.com` sends a packet every 5 seconds instead of the default 1 second. Useful for long monitoring sessions without overwhelming the network.
- **-4** : forces the command to use the IPv4 protocol even if the system prefers IPv6. This is helpful when you need to test or troubleshoot IPv4 connectivity specifically.
- **-v** : enables verbose mode, displaying additional details about the operation, such as packet headers and routing information, which can aid in troubleshooting network issues.
![[Pasted image 20250919213411.png]]



## Traceroute
- traceroute maps the path a request takes to a target machine
- the internet consists of many servers and endpoints connected together
- to reach content, requests pass through multiple intermediate servers
- traceroute displays each intermediate step between your computer and the resource
- basic Linux syntax: `traceroute <destination>`
- Windows `tracert` uses ICMP by default; Unix `traceroute` uses UDP by default
- protocol can be changed with command-line switches
![[Pasted image 20250919213645.png]]


- example traceroute to google.com showed 10 hops from the router (_gateway) to 142.250.182.110

## Whois
- **Whois** is a protocol/tool used to look up information about who owns or manages a domain name or IP address.
- It provides details such as the registrar, registration and expiration dates, and contact information.
- Data availability depends on privacy laws and the registrar’s settings.
- In regions with stricter privacy rules (e.g., Europe’s GDPR), personal details are usually hidden or redacted.
- In other regions, Whois may display registrant names, emails, phone numbers, and administrative/technical contacts.
- Useful for checking domain ownership, investigating cyber incidents, or confirming registration details.


## Domain
- Domain names replace IP addresses so users don’t have to remember numerical addresses.
- A domain translates into an IP address for easy access (e.g., tryhackme.com instead of its IP).
- Domains are leased through companies called Domain Registrars.
- To obtain a domain, you register with a registrar and lease it for a set period.
- Whois is a tool that queries who a domain name is registered to.
- In Europe, personal details in Whois records are redacted.
- Outside Europe, Whois searches can reveal significant registrant information.
## Domain Name System
- - DNS (Domain Name System) is a TCP/IP protocol that converts a URL into an IP address a computer can use.
- When requesting a website, the computer first checks its **Hosts File** for a manual IP→Domain mapping.
- If not found, it checks the **local DNS cache** for a stored IP address.
- If still unresolved, it queries a **recursive DNS server**, whose details are stored in the router/computer (e.g., ISP, Google, OpenDNS).
- The recursive server checks its own cache; if absent, it forwards the request to a **root name server**.
- Root name servers (originally 13 IP addresses) direct the query to the correct **Top-Level Domain (TLD) server** based on the domain extension (e.g., .com, .co.uk).
- The TLD server forwards the request to the relevant **Authoritative name server**, which stores the domain’s DNS records.
- The authoritative server responds with the domain’s IP address, enabling the computer to connect.
- This entire process is automatic when visiting a website.
- **TTL (Time To Live)** in the answer specifies how long the DNS record remains valid in the cache (measured in seconds).

## Dig 
- - dig is a command-line tool for querying DNS servers.
- Syntax: dig @ (the @server part is optional if you want to use your system’s default DNS server).
- Sends a manual DNS request to a specified or default recursive DNS server.
- Returns detailed DNS response sections: QUESTION, ANSWER, AUTHORITY, and ADDITIONAL.
- The ANSWER section shows the domain’s IP address (A record) and status of the query.
- Displays the record’s TTL (Time To Live), indicating how long the DNS information remains valid in cache.
- Useful for troubleshooting network/DNS issues, verifying DNS changes, and inspecting specific record types (e.g., dig example.com MX for mail records).
- Supports querying different record types: A, AAAA, MX, TXT, NS, etc.
- Can target a specific DNS server for testing propagation or server behavior.