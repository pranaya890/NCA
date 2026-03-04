- web- security vulnerability  that allows attacker to cause the server side application to make request to unintended location
- the attacker might cause the server to make a connection to internal-only services within the organization's infrastructure
- they may be able to force the server to connect to arbitrary external systems
- his could leak sensitive data, such as authorization credentials

### Impact of SSRF
- result in unauthorized actions or access to data within the organization
- the SSRF vulnerability might allow an attacker to perform arbitrary command execution
- An SSRF exploit that causes connections to external third-party systems might result in malicious onward attacks
- These can appear to originate from the organization hosting the vulnerable application

### Common SSRF attack
- exploit trust relationship to escalate an attack from the vulnerable application and perform unauthorized actions
- These trust relationships might exist in relation to the server, or in relation to other back-end systems within the same organization

### SSRF attack against the server
- in SSRF attack against the server the attacker causes the application to make an HTTP request back to the server that is hosting the application using  its loopback network interface
- This typically involves supplying a URL with a hostname like `127.0.0.1` (a reserved IP address that points to the loopback adapter) or `localhost` (a commonly used name for the same adapter)
- 