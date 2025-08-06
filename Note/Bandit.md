n=bandit 0


bandit 1
pw
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If




bandit 13
pw FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

we can login to bandit 14 using `sshkey.private` located in `/etc/bandit_pass/bandit14` by using localhost as hostname and using ssh to login to bandit 14 and  use `-i` to  insert a identity file sshkey.private in which the password is stored
``` Shell
ssh bandit14@localhost -p 2220 -i sshkey.private
```


bandit 14
pw
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

we can connect to the localhost to port 30000 by using the basic netcat command
which will create a tcp connection

``` Shell
nc localhost 30000 # to establish a TCP connection
# then enter the password to login
```
alternatively we can login to bandit 13 then directly login to bandit14 using following command
``` Shell
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

bandit 15
pw
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
``` Shell
cat /etc/bandit_pass/bandit15 | ncat 127.0.0.1 30001
```






bandit 16
pw
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
we can use nmap to determine the open ports. 
```Shell 
nmap -p31000-32000 localhost #displays the open port only
```
![[Pasted image 20250721203701.png]]
we can use nmap with its option `-sV` to know more detail about what is running and which version
``` Shell
nmap -p31000-32000 localhost -sV
```


![[Pasted image 20250721203601.png]]
we have to choose that port which has version `ssl/unknown`
the we can use `ncat` with `--ssl`  to login to the `ssl/unknown` labelled port
```Shell
ncat --ssl localhost 31790
```
the command  says the ncat to use ssl/tls encryption hence the target is encrypted.

we can get rsa key here by using the password of this level 
![[Pasted image 20250721205958.png]]



bandit 17
 to login to this level we have to use the rsa key that we got from previous level
 first we have to see the permission of the txt file we saved in our local device
 
 ![[Pasted image 20250721211123.png]]
 the permission for the owner is to read and write then for  group is read and write then for others is read. if we use it directly we will get the permission error
![[Pasted image 20250721211400.png]]
so we have to change the permission of the key file using chmod
``` Shell
chmod 600 <filename>
```
which changes the file permission to `2+4=8` which is read and write for the owner
``` Shell
ssh -i <keyname> bandit17@bandit.labs.overthewire.org -p 2220
ssh -i sshkey bandit17@bandit.labs.overthewire.org -p 2220
```
for logging into the system



bandit 18

using `diff` command we can solve this level because it extracts the different line from one file to another
``` Shell
diff password.new password.old
```
this command output shows the different line of passwords.new at first and passwords.old thenafter.
![[Pasted image 20250718211919.png]]


bandit 18-19
pw 
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

we can use ls command with regular ssh command to see whether the server is responding to us or not.
``` Shell
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
```
![[Pasted image 20250718215759.png]]

Here the server is responding so we can directly read the file using `cat <filename>`

```Shell
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

![[Pasted image 20250718220043.png]]
bandit 19-20
bandit 19 pw: cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8 
![[Pasted image 20250721220351.png]]
the `s` in permission stands for `setuid` that is the permission






for solving bandit 20 we have to execute the file bandit10-do which is an executable file but the  file permission are tricky bandit19 can execute it other user dont have permission and bandit20 can read and write so we can first use `./bandit20-do ls` to list the files then we can search for specific file `/etc/bandit_pass/bandit20` using the command ` ./bandit20 ls /etc/bandit_pass/bandit20` if we find any of the files there we can read using `cat` command instead of `ls`
``` Shell
./bandit20-d0 ls -l /etc/bandit_pass/bandit20
./bandit20-d0 cat /etc/bandit_pass/bandit20

```
![[Pasted image 20250718222542.png]]
 bandit 20-21
 pw
 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
 the file in the directory named `suconnect` is an executable file
 ![[Pasted image 20250722190443.png]]
 while executing the file `suconnect` it shows its executable syntax `./suconnect <portnumber>`
 ![[Pasted image 20250722190608.png]]
it says `suconnect` will connect the portnumber to the localhost if it receives correct password it will send the next password

to do that we have to first create a server using `nc` with `lnvp` and a port number in another pane of the tmux session
``` Shell
nc -lnvp <portnumber>
nc -lnvp 9006
```
then we can connect it using `.exe` file `suconnect` then from another pane we can receive the password 
``` Shell
./suconnect 9006
```

![[Pasted image 20250722191101.png]]
then we can send the message to `suconnect` from another pane
![[Pasted image 20250722191209.png]]
Bandit 21-22
pw=EeoULMCra2q0dSkYj561DX7s1CpBuOBt
