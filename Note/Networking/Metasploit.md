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
### Exploits
- ![[Pasted image 20251117203406.png]]
### NOPs
- NOPs (NO OPeration) do nothing
- they are represented in intel `*86`  CPU family with 0x90 following which cpu wont do anything for one cycle
- often used as buffer to  achieve consistence payload sizes
![[Pasted image 20251117203732.png]]
### Payloads 
- codes that will run on the target system
- exploit will leverage a vulnerability on target system but to achieve desired result we need a payload
- examples: getting a shell, loading a malware or backdoor to the target system, running a command or launching `calc.exe` as a proof of concept to add the penetration test report 
- starting the calculator  on target system remotely by launching  the calc.exe application is benign ( harmless)  way to show that  we can run command on  the target system
- metasploit offers ability to send different payload that can open shell on the target system
![[Pasted image 20251117205311.png]]

#### Directories of payload
- Adapters: wraps single payloads to convert them into different formats. 
	-  Example: a normal staged payload can be  wrapped inside a Powershell adapter which will make a single powershell command that will execute the payload
- Singles: Self-contained payloads (add user, launch notepad.exe, etc.) that do not need to download an additional component to run.
- Stagers: Responsible for setting up a connection channel between Metasploit and the target system.
	- Useful when working with staged payloads. “Staged payloads” will first upload a stager on the target system then download the rest of the payload (stage)
	- This provides some advantages as the initial size of the payload will be relatively small compared to the full payload sent at once
-  Stages: Downloaded by the stager. allows us to use larger sized payloads.


- metasploit has a subtle (difficult to detect) way to identify single (inline) and staged payloads
		- generic/shell_reverce_tcp
		- windows/x64/shell/reverse_tcp
- both are reverse windows shell 
- the former is the inline (or single) payload as indicated by  '_ ' between "shell" and  "reverse" 
- where as the staged  payload is indicated by "/" between "shell" and "reverse"

### Post
- post model will be useful on the final stage of the pentesting process 
![[Pasted image 20251117211925.png]]

> [!Note]
>  to familiarize  further with these modules, we can find them under the modules folder of  Metasploit installation


### MSF console
- we can launch msf console using `msfconsole` command
- we can use msfconsole  like other command line tool
![[Pasted image 20251119211807.png]]
 here we ping `8.8.8.8` single time using `-c 1` command
 - it support most of linux command including `clear`
 - but it does not support output redirection
 ![[Pasted image 20251119212240.png]]
- `help` command can be useful on its own or for specific command
![[Pasted image 20251119212503.png]]
- we can use `history` command to see the history of the command we typed earlier
![[Pasted image 20251119212556.png]]

- important feature of msfconsole is tab completion
- - Metasploit modules work in their own context
- Settings like RHOSTS apply only to the current module
- Switching modules resets settings unless they are global
- `setg` makes a variable global across modules
- EternalBlue is an exploit targeting SMBv1 on Windows
- SMB is used for file and printer sharing
- The NSA originally created EternalBlue
- The Shadow Brokers leaked it in 2017
- WannaCry ransomware used the EternalBlue vulnerability to spread worldwide
- module to be used can also be selected with the `use` command followed by the number at the beginning of the search result line.
- ` use exploit/windows/smb/ms17_010_eternalblue`
- ![[Pasted image 20251120205341.png]]
- we can normally use other commands like `ls` 
- this will tell context set in which we will work on
- we can see context set by using `show options` command
- ![[Pasted image 20251120205630.png]]
- the `show` command can be used  in any context by a module type ( auxilliary, payload, exploit etc). to list available modules 
- ![[Pasted image 20251120210114.png]]
- we can leave the context using `back` command
- ![[Pasted image 20251120210203.png]]
- further information of any module can be obtained by typing the info command within its context
- ![[Pasted image 20251120210423.png]]

- or we can use info command followed by module path `info windows/smb/ms17_010_eternalblue`

### Search command
- this command will search metaspolit framework database for modules relevant to given search parameter 
- we can conduct searches using CVE number, exploit name (eternal blue, heartbleed) etc or target system
>[! Note] 
>CVE: Common vulnerabilities and Exposures

![[Pasted image 20251120211139.png]]

- output of search command provides  an overview of each returned model
- we can see module name, type of module ( exploit, auxillary), category of module (scanner, admin,windows, unix )
- we can use any module returned in output followed by number of bwginning of result line
- ![[Pasted image 20251120211553.png]]
- another useful information in output of search is rank column
- it ranks the modules on the basis of reliability 
![[Pasted image 20251120211842.png]]

- we can directly search command using keywords like type and platform
- ![[Pasted image 20251120212400.png]]


### Working with modules
- after entering into the context using `use` command followed by module name we need to set parameter
- it is good practice to use `show options` to see the parameters to be set
- Syntax for setting the parameter is 
``` Shell
set PARAMETER_NAME VALUE
```

-  The msfconsole prompt:msf6 (or msf5 depending on your installed version) is the msfconsole prompt. 
![[Pasted image 20251120213047.png]]

- A context prompt: Once we have decided to use a module and used the set command to chose it, the msfconsole will show the context. we can use context-specific commands (e.g. set RHOSTS 10.10.x.x) here.

![[Pasted image 20251120213105.png]]

- The Meterpreter prompt: Meterpreter is an important payload  . Meterpreter agent was loaded to the target system and connected back to you. You can use Meterpreter specific commands here.
![[Pasted image 20251120213226.png]]

- A shell on the target system: Once the exploit is completed,we may have access to a command shell on the target system. This is a regular command line, and all commands typed here run on the target system.
![[Pasted image 20251120213305.png]]

- we can see `show options` to check the values that are required for exploit
- some are pre-populated
- we can use set command to set the values
- at last we can use show options to  check the value 


### Commonly Used parameters
- RHOSTS:  "remote host" the ip address of the target system 
		single IP address or network range can be set
		this will support CIDR notation (Classless-Inter Domain Routing) [/24, /36 etc]
		or a network range 10.10.10.1-10.10.10.9
		we can also use  files where targets are listed  one target per line using file: /path/of/targetfile.txt
-  RPORT: “Remote port”, the port on the target system the vulnerable application is running on.
- PAYLOAD: The payload you will use with the exploit.
- LHOST:“Localhost”, the attacking machine (your AttackBox or Kali Linux) IP address.
- LPORT: “Local port”, the port you will use for the reverse shell to connect back to. This is a port on your attacking machine, and you can set it to any port not used by any other application.
- SESSION: Each connection established to the target system using Metasploit will have a session ID. You will use this with post-exploitation modules that will connect to the target system using an existing connection.

---
- we can override any set parameter using set command with different values 
- we can also clear any parameter using the `unset` command
- we can clear all set parameter using `unset all`

### setg Command
- `setg` sets a value globally for all Metasploit modules
- `set` sets a value only for the current module
- Global values set with `setg` remain when switching modules
- Global values can be removed using `unsetg`
- Example flow:
- Load the ms17_010_eternalblue exploit
- Set `RHOSTS` using `setg`
- Use `back` to exit the exploit context
- Load an auxiliary scanner module
- `show options` displays `RHOSTS` already filled with the global value

![[Pasted image 20251123204747.png]]

### Using modules
- after setting parameters we can launch module using `exploit` command
- it also supports run command which is alias for exploit command
- `exploit` command can be used  without any parameter  or using `-z` parameter
- it will run the exploit command  and background the session as soon as it opens
![[Pasted image 20251123205912.png]]
- this will return the context prompt from which we have run the exploit
- some module allow `check` option 
- this will check if the target system is vulnerable without exploiting it
### Sessions
- after exploiting vulnerability the session will be created
- this is the communication channel established between the target system and metasploit
- we can use `background` command to background the session prompt and go back to msfconsole
![[Pasted image 20251123210356.png]]
- alternatively `CTRl+Z` can be used to background session
- the `sessions` command can be used from msfconsole or any context  to see the exisisting session

![[Pasted image 20251123212148.png]]
- to interact with the system we can use `sessions -i` followed by desired session number
-  `sessions -i 1`
- 