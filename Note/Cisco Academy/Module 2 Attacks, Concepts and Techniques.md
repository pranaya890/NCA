## Analyzing the Cyber Attack
### Types of Malware
- cybercriminals use different kinds of  malicious software or malware to carry out their activities
- malware is any code that can be used to steal data, bypass access control or cause harm to or compromise a system 

#### Spyware
- designed to track and spy on target
- monitors our online activity  and can log  every key you press on  your keyboard
- and can capture almost any of your data including sensitive personal information
- spyware does this by modifying the security settings on your device
- it often bundles it with legitimate software or Trojan horses

#### Adware

- often installed with some versions of software and designed to automatically deliver  advertisement to a user, most often on a web browser
- it’s hard to ignore when you’re faced with constant pop-up ads on your screen (you know it when you see it)
- its common for adware to come with spyware

#### Backdoor
- type of malware is used to gain unauthorized access by bypassing the normal authentication procedures to access a system. 
- result in  hackers can gain remote access to resources within an application and issue remote system commands
- A backdoor works in the background and is difficult to detect

#### Ransomware
- designed to hold a computer system or the data it contains captive until a payment is made.
- Ransomware usually works by encrypting your data so that you can’t access it.
- e can take advantage of specific system vulnerabilities to lock it down. 
-  often spread through phishing emails that encourage you to download a malicious attachment or through a software vulnerability.

### Scareware
- malware that uses 'scare’ tactics to trick you into taking a specific action. 
-  mainly consists of operating system style windows that pop up to warn you that your system is at risk and needs to run a specific program for it to return to normal operation.
- If you agree to execute the specific program, your system will become infected with malware

#### Rootkit
- designed to modify the operating system to create a backdoor, which attackers can then use to access your computer remotely. 
- Most rootkits take advantage of software vulnerabilities to gain access to resources that normally shouldn’t be accessible (privilege escalation) and modify system files.
-  can also modify system forensics and monitoring tools, making them very hard to detect. 
- In most cases, a computer infected by a rootkit has to be wiped and any required software reinstalled

#### Virus
-  type of computer program that, when executed, replicates and attaches itself to other executable files, such as a document, by inserting its own code. 
- Most viruses require end-user interaction to initiate activation and can be written to act on a specific date or time.
- Viruses can be relatively harmless, such as those that display a funny image. 
- Or  can be destructive, such as those that modify or delete data.
- Viruses can also be programmed to mutate in order to avoid detection.
- Most viruses are spread by USB drives, optical disks, network shares or email.

#### Trojan Horse
- carries out malicious operations by masking its true intent.
- might appear legitimate but is, in fact, very dangerous. 
- Trojans exploit your user privileges and are most often found in image files, audio files or games.
- Unlike viruses, Trojans do not self-replicate but act as a decoy to sneak malicious software past unsuspecting users.

#### Worms
-  replicates itself in order to spread from one computer to another. 
- Unlike a virus, which requires a host program to run, worms can run by themselves. 
- Other than the initial infection of the host, they do not require user participation and can spread very quickly over the network.
- Worms share similar patterns: They exploit system vulnerabilities, they have a way to propagate themselves, and they all contain malicious code (payload) to cause damage to computer systems or networks.
- Worms are responsible for some of the most devastating attacks on the Internet. In 2001, the Code Red worm had infected over 300,000 servers in just 19 hours.

### Symptoms of Malware
- increase in CPU usage slows down the devices
- computer freezing or crashing often
- decrease in web browsing speed
- unexplainable problem with network connections
- modified or deleted files
-  the presence of unknown files, programs or desktop icons
- unknown process running
- programs turning off or reconfiguring themselves
- emails being sent without my knowledge or consent

## Methods of Exploitation
### Social Engineering
- technique of manipulating people into performing actions or divulging confidential information
- rely on people's weakness to be helpful, but also prey on their weakness
- for example: attacker calls authorized employee with urgent problem  that requires network access and appeal to the employees vanity or greed invoke authority by using name-dropping techniques in order to gain this access
#### Common Social Engineering Attacks
- Pretexting: when attacker calls an individual and lies them in an attempt to gain access to privileged data. For Example,pretending to need a person’s personal or financial data in order to confirm their identity
- Tailgating: When an attacker follows an authorized person into a secure physical location
- Something for Something: This is when an attacker request personal information from a person in exchange of something. 

### Denial of Service (DoS)
-  type of network attack that is relatively simple to carry out even by unskilled attacker
- results in some sort of interruption of network service  to user, device or application
#### Main types of DoS
- Overwhelming quantity of service: when the attacker sends enormous amount of data at the rate which a target cannot handle, causes a slowdown in transmission or response, or the device or service to crash
- Maliciously formatted packets: collection of data that flows between a source or receiver  computer or application over a network which the target cant handle. it may cause the target system to run slow or crash

### Distributed DoS
- similar to DoS but originates from multiple, coordinated sources
- An attacker builds a network (botnet) of infected hosts called zombies, which are controlled by handler systems.
- The zombie computers will constantly scan and infect more hosts, creating more and more zombies.
- When ready, the hacker will instruct the handler systems to make the botnet of zombies carry out a DDoS attack.

![[Pasted image 20260306081714.png]]

### Botnet
