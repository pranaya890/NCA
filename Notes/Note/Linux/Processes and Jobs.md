`ps` command can be used to list the current running processes 
it stands for process snapshot or  process status
it list the process running in my terminal
![[Pasted image 20250725202935.png]]

`PID` is process id helps us to identify the process uniquely
TTY is `teletypewriter` which shows the terminal in which the process is running 
and TIME shows the time in hh:mm:ss second and 
CMD shows the shell running we have `zsh`  shell i.e. Z-Shell and `ps` process running in terminal
 this`ps` command is basic and we can use specific argument to extract more information
Basically there is two ways of specifying argument

- "Standard" syntax : we can specify `-e` for every process and `-f` for full format process snapshot
	![[Pasted image 20250725204308.png]]
	
- BSD syntax : we can use  `a` to list all `u` for user-readable output and `x` for listing process that is not running in terminal
		![[Pasted image 20250725204330.png]]
basically these commands display same column 

we can `kill` command to kill a process using `pid`
this command will terminate a process 
![[Pasted image 20250725210010.png]]
![[Pasted image 20250725210027.png]]


![[Pasted image 20250725210215.png]]

### suspending, interruption and resuming a process
we can use `Ctrl+C` to interrupt the current process
we can suspend the process using `Ctrl+Z`  which suspend the process and send it to background and
we can resume the process using `fg` command
which stands for foreground and brings the suspended process back and resumes
we can also use `bg` command to resume the process in background
and we can use `&` command to directly run the command in background
![[Pasted image 20250725215822.png]]


### some deeper details in suspending,  interruption and resuming process
![[Pasted image 20250725214459.png]]
here we first suspended the process sleep then we watched the process snapshot
we see T there it means suspended then R is running and + is in foreground
Ss here means sleeping and waiting for input

![[Pasted image 20250725214746.png]] 
 here we continued sleep in background then it shows S  in stat which means sleeping and there is no + sign so we come to know it is running in background


### exit code
every command in shell has its exit code we can see the exit code of recently run code by using `?` with `$` before it.
![[Pasted image 20250725220648.png]]
command that run successfully return `0` and that doesnot run will return `1` or nonzero

![[Pasted image 20250725220833.png]]
