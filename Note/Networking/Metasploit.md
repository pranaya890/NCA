- metasploit is the exploitation framework that supports all phases of penetrating testing from information gathering to post exploitation
- two main versions: metasploit pro( GUI based)  and metasploit framework( CLI based)
- metasploit framework is the set of tools that can be used for information gathering, scanning exploitation, exploit development, post-exploration and  vulnerability research
- its primary use focuses on penetration testing domains 
- Main Components:
		- msfconsole: CLI
		- Modules: supporting modules such as payloads, exploits and scanners
		- Tools:  stand alone tools for vulnerability research, vulnerability assesment or pentesting, some tools are `msfvenom`, `pattern_create`, `pattern_offset`


------

- Metasploit Framework is primarily used through the Metasploit console (`msfconsole`).
- we can launch the console with the `msfconsole` command from the terminal.
- The console is the main interface to interact with Metasploit modules.
- Modules are small components in Metasploit designed to perform specific tasks.
- Common module tasks include: exploiting vulnerabilities, scanning targets, and brute-forcing services.
- Vulnerability: a flaw in design, code, or logic on the target system.
- Exploit: code that takes advantage of a vulnerability on the target system.
- Exploitation of vulnerabilities can disclose confidential information or allow code execution.
- Payload: the code that runs on the target system after successful exploitation.
- Exploit + payload = practical effect (e.g., gain access, read sensitive data).
- we interact with all these components (exploits, payloads, auxiliary modules, etc.) via `msfconsole`.
- Metasploit modules are organised into categories (exploits, payloads, scanners, brute-force, etc.) for different purposes.

### Auxiliary 
- supporting modules such as  scanners, crawlers and fuzzers  can be found here
```
tree -L 1 auxillary/
```
>[! note]  
>crawlers: an automated program that systematically browses the internet to discover,
collect, and index content from websites for search engines and other applications. 

>[!note] 
>fuzzers:a software testing tool used to identify vulnerabilities and bugs in computer programs by inputting large amounts of random, unexpected, or malformed data and observing how the program reacts.



![[Pasted image 20251117202530.png]]

### Encoders
- allows us to encode the exploit and payload in the hope that a signature-based antivirus  solution may miss them
- signature- based antivirus  and security solution have a database of known threat 
- they detect threat by compairing  suspicious file  to the database and raise an alert if there is a match
- thus encoders can have a limited success rate as antivirus solutioncan perform additional checks

![[Pasted image 20251117202631.png]]


### Evasion
- while encoders will encode the payload  they should not be considered to evade antivirus software 
- "evasion" model will try that 
![[Pasted image 20251117202835.png]]
