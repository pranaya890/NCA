forking is the process of running process simultaneously on terminal
we can create a fork of ls by
``` Shell 
#in try.sh
#!/bin/bash
ls & ls && echo "done" 
# this runs the ls process simultaneously in background and foreground
# & is used to send process to background
```



![[Pasted image 20250804203243.png]]

this runs the `try.sh` in background and foreground one by one


#### forking a exefile
daring destruction challenge 1 linux luminarium
first we have to create a shell script that runs itself in background twice and this will create a recursion but it will to to infinite loop
and cannot be stopped 
``` Shell
Precaution:do not run in your shell
# in try.sh
#!/bin/bash
./try.sh & ./try.sh &
```

this will recursively call try.sh in background infinitely

### Disk-Space Clogging

we can clog the disk space with different commands one is `yes` command
##### `yes` command
yes command is used to print `y` continuously into a file
``` Shell
yes | head
# this will print y for first 10 lines
# if we dont give condition to stop it runs continuously
```
 solution for linux-luminarium/daring destruction /disk space doomsday
 ![[Pasted image 20250805200625.png]]
 

solution for linux-luminirium/daring destruction / rm -rf 
![[Pasted image 20250805203704.png]]

solution for linux-luminirium/daring destruction / life after rm -rf
![[Pasted image 20250805204514.png]]


solution for linux-luminirium/daring destruction / finding meaning after rm -rf
![[Pasted image 20250805210045.png]]