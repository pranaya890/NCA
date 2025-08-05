SSH is a tool used to access the remote computer safely.
provides a secure channel over an unsecured  network in client-server architecture
Encrypts data to keep connection secure
ssh  (SSH  client)  is a program for logging into a remote machine and for executing commands on a remote machine. 
It is intended to provide secure encrypted communications between two untrusted hosts over an insecure network.  

`ssh user@ip`

### For checking status of ssh server
```
sudo systemctl status ssh
```

### for enabling and starting ssh server
``` 
sudo systemctl enable ssh
sudo systemctl start ssh

```

###  for connecting to the ssh
``` 
ssh username@hostname_or_ip
ssh pranaya@192.168.100.73
ssh username@host -p port
```

### To exit ssh session
```
exit
```


### Private SSH Key
it is the key that helps to login to a server without using password
it is the part of SSH key pair.
 it is combined with public key to  login into the server
 It can be compared to lock key system  the server has a lock (public key ) and i have the key (private key)  only my private key can  open the lock.
 if the key fits the server allows the login
### Public SSH key
it is a type of ssh key that key used to login to the server.
it is called public key because it can be shared without compromising the security.
 it is used in combination of private key to connect to the server.
 it can be used  in server login without password, to secure communication in which data is encrypted, and digital signal to verify identity
 
### to generate a ssh key pair
in order to generate the ssh key pair we can use `ssh-keygen` command
``` Shell
ssh-keygen #to generate the key pair 
ssh-keygen -f key -N ' ' #togenerate a keyfile named key and key.pub
```
`-f`  requests the ssh to go to background before execution to check if ssh asks for password or passphrase
`-N` for forwarding ports i.e. for redirecting network traffic
![[Pasted image 20250722204431.png]]
for simpler sense we can press enter key for no passphrase





### To perform a basic brute force attach on ssh login 
Brute Force is a method used to guess something by trying everything possible option untill you find the right one
Example  if i have 4 digit password brute forcing here is trying every pin from `0000`
 to `9999`
 ``` 
hydra -l username -P /path_to_password.txt_or_server ssh://target_ip
#using hydra
hydra -l username _p /path_to_password -1 ssh://target_ip
#limiting the thread to 1 
```