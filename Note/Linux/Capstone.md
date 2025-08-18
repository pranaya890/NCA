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

in the last question of task 5 there is a file called file22 in folder 5 which will guide to next level
content of file `bob:9f9d51bc70ef21ca5c14f307980a29d8`


### Task 6
- for solving the first  question i have to find the file location we have to login to using bob via ssh then we can use `grep` and its option `-n` to print number of lines
![[Pasted image 20250818202028.png]]
- for second question the first thing is to remove duplicate line we can do it by using ninja technique by sorting the file and printing only unique lines and redirect the output to new file then we can use previously used `grep` command to print the unique lines
![[Pasted image 20250818202723.png]]
- we can send output of one code as input to another cmd using `|`
- for counting the number of lines starting from n we can use `grep` with `-c` and line starting with letter can be denoted using "^Letter" 
![[Pasted image 20250818203256.png]]

- we can count the user by going to home directory and listing all the users and adding +1 on that for root.
![[Pasted image 20250818204929.png]]

- `head` displays first few lines of text
- in command `cut -d':' -f1 /etc/passwd` `:` is delimiter
- text scanning tool for pattern scanning and processing is `awk`
- in next question for finding output of `cut -d " " -f10 random_wordws.txt`, here `-d ` is delimeter and `-f10` is field 10 i.e. it cut out the tenth field
![[Pasted image 20250818210145.png]]
- for output of `awk -F'[:;]' 'NR == 12 {print "My name is", $1, $2}' students.txt` we can directly run or we can use `head -n 12` command to print because it takes 12th line and prints its 12 th input record 
![[Pasted image 20250818215231.png]]
- `-F` in above command is field separator
### Task 7
- the class is C (for more goto IP address note)
- MAC= media access control
-  djfa
- to check connectivity of google.com we can use `ping 8.8.8.8`
- linux file to manually map ip address to hostname is `/etc/hosts`
- number of network interfaces in system: 2 (physical{eth0,wlan} and virtual(docker,lo))
- by manually  mapping ip in `/etc/hosts` we get `nca{y0u_have_mapped_the_1p}`
- file used to modify is `/etc/resolv.conf`
- starting apache service `service apache2 start`
- netstat command to view routing table `netstat -r`
- 