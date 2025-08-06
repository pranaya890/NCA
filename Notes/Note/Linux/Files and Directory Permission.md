every linux files has the permission that determine who can read write and execute
![[Pasted image 20250718205514.png]]
 here in `drwxrwxr` the `d` stands for directory in other the first declaration is unspecified.
 `rwx` means read write and execute permission
 `rw` means read and write
 `r` means read permission

### Chmod
`chmod` or change mode is a linux command used to change the permission of files and directory.
``` Shell
chmod [option] [mode]
```

we can change the mode of the file by using `+` for adding a permission and `- ` for removing the permission
we can use `u` , `g` and `o` for user group and others permission respectively and `a` for all
and `r` for read
`w` for write and `x` for execute
``` Shell
chmod a+wrx hello.txt
chmod u=rwx,g=r hello.txt #sets permission of user to rwx and g to r
chmod u=- hello.txt #to remove all permission from user
chmod u+s [program] #gives executable permission with set user id {SUID}
```
![[Pasted image 20250726003413.png]]
example of  perceiving permission of linux-luminarium
### Changing mode with decimal notation
file permission in linux can be changed by decimal notation also called octal notation
there is numeric way to  represent permission read=4 write=2 and execute =1
this value is added to notate a specific permission 
for example for a file to read and write we can use `4+2=6`
example for mode `732` 
7: for owner the permission are  read write and execute
3: for group the permission are write and execute
1: for  others only execute

### setuid  and setgid command
it is the command in linux used to execute an executable file with the file system permission for owner and group.
it is also used to change the behaviour of executable in the directory
used to allow user to run an executable with temporary eleveted previlege to perform a specific task

setuid is short for set user identity  and setgid is short for set group identity
`setuid` and `setgid` used 4 and 2  respectively in higher order octal digit of file mode.
suppose `6711` has both `setuid` and `setgid` `4+2` and has `7=4+2+1` permission for owner `1` execute permission for group and `1` for other



### Changing ownership of a file
we can change the ownership of file using `chown` command
``` Zshell
chown [username] [file]
```
it can typically be invoked by root user
![[Pasted image 20250725231121.png]]

### changing the group of file
we can  change the group ownership by using `chgrp` command
``` Shell
chgrp [username] [file]
chgrp hacker hello.txt
```


### cracking password via john the ripper
all the passwords are stored in `/etc/passwd` but it is global readable file
so it is shifted to `/etc/shadow`  the hashed password can be cracked using john the ripper
suppose we have a copy file of `/etc/shadow` as `shadow-leak`
 we have to first change the directory to the directory to shadow-leak
 then 
 ``` Shell
 johb ./shadow-leak
```
![[Pasted image 20250726005014.png]]