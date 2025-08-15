
## Process
- A process in Linux is an instance of a running program, including code, current activity, and system resources (memory, CPU, file descriptors).
- Each process has a unique Process ID (PID).
- Processes operate independently but can communicate via pipes, signals, or shared memory.
- Processes are created by **forking**, where a parent duplicates itself to create a child process.
- Child processes can execute different programs using the **exec** system call.
- Process management in Linux involves controlling and monitoring processes for efficient operation.
- The kernel handles process scheduling, resource allocation, and state transitions (running, sleeping, stopped, terminated).
- Common tools for viewing/managing processes: `ps`, `top`, `htop`, `pgrep`.
- Commands for process control:
- `kill` and `pkill` to terminate or send signals to processes.
- `nice` to adjust process priorities.
- The **init** process (or systemd) is the root of all processes and manages system startup, shutdown, and orphaned processes.
- Effective process management ensures optimal system performance, resource use, and stability.


### Viewing Process

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

### Filtering the running process
- Viewing all running processes at once can be overwhelming due to large output.
- Filtering helps focus on specific processes or related groups.
- Use `grep` to filter the output of `ps aux` for processes matching a name or keyword.
- This method is useful for monitoring resource-intensive applications or services.
- Example: To check if Apache web server is running and assess its resource usage, filter `ps aux` output for Apache-related processes using grep.
``` Shell
date # shows the date
service apache2 start #starts the apache server
ps aux |grep apache2 
```

![[Pasted image 20250815114610.png]]


### Identifying Resource Intensive Process
we can use `top` command to see the snapshot of resource intensive process
```Shell
top
```

![[Pasted image 20250815114916.png]]
While `top` is running, we can press `H` or `?` to view a list of interactive commands, or press `Q` to exit

### Managing multiple process
- Hackers (or users) may run multiple tools simultaneously, e.g., port scanner, vulnerability scanner, and exploit.
- Running multiple processes requires efficient management to optimize system resources.
- Proper process management ensures tasks complete successfully without overloading the system.
- Effective management includes monitoring resource usage, prioritizing processes, and controlling process execution.

### Services and process management
Services are categorized into two types:
- **Internal Services:**
- Essential for system startup.
- Handle hardware tasks, system initialization, core OS functions.
- Examples: device driver managers, network configuration, system logging.
- Ensure smooth system operation from boot.
- **User-Installed Services:**
- Installed by users to provide specific functions or applications.
- Examples: web servers (Apache, Nginx), database servers (MySQL), remote access tools (SSH).
- Run in the background without direct user interaction.

- Background services are called **daemons**.
- Daemon names typically end with the letter **‘d’** (e.g., `sshd`, `systemd`).
- `sshd`: daemon for SSH service (Secure Shell).
- `systemd`: system management daemon responsible for boot initialization and managing other services.
### Starting a service
```Shell
systemvtl start apache2 # this starts the apache2
```

### Checking service status
```Shell
systemctl status <service_name>

```

![[Pasted image 20250815115551.png]]

### Terminating a process

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



### Controlling processes with signals
- Processes can be controlled by sending **signals** using commands like:
- `kill`
- `pkill`
- `pgrep`
- `killall`
- Signals instruct processes to perform actions such as:
- Terminating
- Pausing
- Restarting
- Each signal has a specific purpose and behavior (e.g., `SIGTERM` for graceful termination, `SIGKILL` for forceful kill).
 we can view the available signals with  `kill -l`
![[Pasted image 20250815115901.png]]

### Common signal and their usage
![[Pasted image 20250815115954.png]]
![[Pasted image 20250815120007.png]]

example usage:
```Shell
ps aux | grep 'nano'
kill -9 25719
```

![[Pasted image 20250815120205.png]]


### exit code
every command in shell has its exit code we can see the exit code of recently run code by using `?` with `$` before it.
![[Pasted image 20250725220648.png]]
command that run successfully return `0` and that doesnot run will return `1` or nonzero

![[Pasted image 20250725220833.png]]



