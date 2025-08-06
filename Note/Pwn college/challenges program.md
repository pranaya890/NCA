to do this challenge we need to connect to the server using ssh
for doing that we have to first generate the public key pair using `ssh-keygen`
``` Shell
ssh-keygen
```
![[Pasted image 20250722204908.png]]



then if necessary we need to change the file permission
``` Shell
chmod 600 <filename>
```


then we can cat the `.pub` key then copy it then paste it to the setting of profile of pwn.college then add the ssh key in the option
![[Pasted image 20250722204944.png]]

![[Pasted image 20250722205030.png]]

Then we can ssh the server using the `keyfile`
```Shell
ssh -i <keyname> <hostname> # -i for linking index file
ssh -i key hacker@pwn.college
```

then we can go to root folder `/` then search and dive under challenge directory then 
