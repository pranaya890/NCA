### Task 1
linux creator : linus torvalds
type of kernel used by linux : monolithic
core component of linux: kernel
unix based os by apple : macOS
liscencing model of unix : proprietary
default shell of linux:bash
text based interface to interact with linux : terminal
Linux distribution is known for its rolling release model and is popular among advanced users: arch linux
advantage of linux being open source is : customisation
linux distribution beside kali for pentesting : parrotOS
unix was developed in : AT&T bell labs

### Task 2
hypervisor that runs directly on software - type 1
type 2 hypervisor that is free and open source - virtualbox
file format used for pre configured kali images in virtual box - .ova
default username and password for pre-configured Kali Linux VM - kali:kali
open source type 1 hypervisor for aws cloud computing : Xen
package manager to install virtual box in debian: apt
additional software that must be installed in VirtualBox to enable fullscreen mode in Kali Linux: Guest Addition
command is used to update package lists before installing software in Kali Linux: sudo apt update
Why does the terminal not display any characters when entering a password in Linux : shoulder surfing

### Task 3
representing root directory in linux : /
directory that contains command binary: /bin
directory used for storing temporary files thatr deletes on reboot: /tmp
config file for network setting : /etc
directory for mounting external hard drive: /mnt
directory typically storing user-specific files: /home
home directory for root user: /root
logr are stored in /var/log
linux directory equivalent ti C:/ProgramFiles is /opt
default directory for admin tools : /usr/sbin
You need to check the system logs for failed login attempts. Which directory should you look in? /var/log
After rebooting, a file you saved is missing. You suspect it was stored in a temporary location. Where was it likely saved? /tmp
You plug in a USB drive, but it doesn’t show up under `/mnt/`. Which directory should you check instead? /media
A system administrator needs to reboot the machine but cannot find the `reboot` command. Which directory should they check? /sbin
directory for cpu information: /proc
You need to install a web server, and the configuration files must be edited. Which directory will these files most likely be in? /etc
A script needs access to device information like hard drives and terminals. Which directory should it reference? /dev
You want to check which kernel modules are loaded on your system. Where should you look? /sys
Which shell does Kali Linux use by default? :zsh
command-line interface does Kali Linux provide for running scripts and security tools: terminal
unprevilleged user indicating: $
~ sign represents home directory
windows command-line tool is considered more powerful than CMD: powershell
What feature of Zsh provides command history-based suggestions? auto-suggestions
What does the `#` symbol indicate in the Linux shell prompt? root user
What Linux distributions often lack a GUI by default, requiring terminal usage? ubuntu server

### Task 4
At first i downloaded the ova file then i imported it to vm of my pc
then i set the network to bridge adapter
then i stasted ubuntu machine
and logged in there using `john` as username and `john123` as password
then i watched ip address of both machines using `ip a` then
i pinged the ubuntu server from kali vm using `ping` command then i checked the ping from ubuntu server using `sudo tcpdump -i eth0 icmp` command 
`tcpdump` is **packet capture tool** that lets us see real-time network traffic. 
`-i eth0` tells `tcpdump` to listen on the `eth0` network interface
`icmp` tells `tcpdump` to filter and only show ICMP packets  these include ping requests

``` Shell
ping 192.168.1.75
```

then i use `netdiscover` tool to find live host on network
```Shell
sudo netdiscover -r 192.168.1.0/24
```

![[Pasted image 20250815203055.png]] then i used ssh to connect to the machine using `ssh john@192.168.1.75` and john123 as password


### Task 5
to know the kernel version we can navigate to `/proc/version`
![[Pasted image 20250815204231.png]] 

![[Pasted image 20250815204322.png]]



![[Pasted image 20250815204609.png]]
![[Pasted image 20250815204623.png]]

![[Pasted image 20250815204815.png]]
![[Pasted image 20250815204843.png]]
![[Pasted image 20250815205824.png]]


![[Pasted image 20250815211519.png]]

for the last question i used find command with `-group` and `-perm` command for finding the file with test group and with permission `444`
``` Shell
find / -group test -perm 444 2>/dev/null
```
