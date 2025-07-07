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
```

### To exit ssh session
```
exit
```

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