in linux there is concept of user rules and group
it determines  what the user can perform and what can they access?
the most powerful user is root user also known as superuser
root user has unrestricted access to the system
regular user has limited permission
the separation of privilege is core principle of linux security
i.e. most user operate with controlled environment that minimise the risk of  accidental or intentional damage to the system


### Adding a user
we can add a user to linux system with simple process using Terminal
to do that we need admin privilege in terminal we can use sudo for that
then we can use `adduser` command 
then we can add the information of new user and press enter then the new user will be created
we can check the new user by using `grep username /etc/passwd`

![[Pasted image 20250807201401.png]]


### Groups in linux
in order to simplify user and permission management, linux organizes users in group
group is collection of user who share similar access need

By assigning users to group admin can effectively manage permission instead of individual assignment which increases the consistency and reduces risk of errors with proper system organisation
The groups in linux allows following things
-  it makes the permission management streamlined by organizing the user in group who need similar permission
- it enhances security by limiting access to sensitive files and directory to specific group
- it improves collaboration via resources sharing  
To add group we can use `groupadd` \
![[Pasted image 20250807203025.png]]
we can view group by grepping `/etc/group` file
![[Pasted image 20250807203147.png]]

### Types of group in linux
In Linux, users are associated with both **primary groups** and **secondary groups**, each serving a specific purpose in managing permissions and access. 
#### Primary Group
When a user account is created, it is assigned a **primary group**, which is typically named after the user.
This primary group plays a key role in determining the default group ownership of files and directories created by the user. 
Whenever a user creates a new file or directory, the system automatically assigns the primary group as the group owner of that file or directory. 
user can belong to only one primary group at a time and we can verify it using `/etc/passwd` file

#### Secondary Groups
These are additional groups that provide the user with extra permissions beyond those primary group. 
Secondary groups are particularly useful in environments where users need access to resources shared among multiple teams or roles.
A user can belong to multiple secondary groups, and this information is stored in the `/etc/group` file. 

#### Adding a user to a group
``` Shell
sudo usermod -aG cryptic pranab
```
`usermod` is used to modify the user in linux
`aG` is for append and group
![[Pasted image 20250807210457.png]]



### Granting Permission






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
chmod g= test.txt #removes all permission of group
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



## Setting More Secure Default Permissions with Masks

- The **`umask` (user file-creation mask)** defines the default permission settings for **newly created files and directories**.
- It works by subtracting the mask value from the **base permissions**:
- **Base permissions**:
- Files: `666` (read & write for owner, group, others)
- Directories: `777` (read, write & execute for all)
- A common umask is `022`:
- For files: `666 - 022 = 644`  ->`rw-r--r--`
- For directories: `777 - 022 = 755` → `rwxr-xr-x`
- This ensures:
- **Files** are not executable by default.
- **Group and others** have only necessary access (read or read/execute).
- Umask helps enforce **security best practices** by preventing overly permissive default permissions.
- **Setting `umask`**:
- **Temporarily**: Use the `umask` command in a terminal session.
- **Permanently**: Add `umask <value>` to user shell config files (e.g., `~/.bashrc`, `~/.bash_profile`, or `~/.profile`).
- It is especially important on **multi-user systems** to protect user files and limit unauthorized access.

![[Pasted image 20250815112344.png]]
**Initial File (`test1`)**
- `touch test1` with default `umask` (likely `002`)
- Permissions: `rw-rw-r--` (664)

**Change `umask`**
- `umask 027` → masks group write (2) & all others (7)

**New File (`test2`)**
- `touch test2`
- Permissions: `rw-r-----` (640)

**Summary (`ls -l` Output)**
- `test1`: Less restrictive (664)
- `test2`: More secure (640)

### Special Permission
- Go beyond basic `r`, `w`, `x` permissions
- Provide extra control over **execution** and **file access**
- Three types:
- **SUID** – Run as file owner
- **SGID** – Run or inherit group
- **Sticky Bit** – Restrict deletion in shared dirs

### Granting temporary root permission with `SUID`
- SUID (Set User ID) lets a file run with the **owner’s privileges**, often root.
- Used in cases like the `passwd` command, which needs access to restricted files (e.g., `/etc/shadow`).
- When a user runs a file with SUID, they temporarily get the **file owner's permissions** during execution.
- Does **not** grant full root access—only within the scope of that program.
- To set SUID:  
   `chmod 4755 filename`
- The `4` adds the SUID bit; file shows `s` in the owner's execute field (e.g., `rwsr-xr-x`).
- Should only be set on **trusted programs** to avoid security vulnerabilities.
![[Pasted image 20250815113051.png]]

-  The command `chmod 4644 test1` sets the **SUID bit** on `test1`, resulting in permissions `rwSr--r--`.
- The **`S`** (uppercase) in place of the owner's execute bit means:
- **SUID is set**, but the file is **not executable** by the owner.
- File `test2` has standard permissions `rw-r-----` (read/write for owner, read-only for group).
- No special permissions (like SUID) are set on this file.

### Granting the  Root user  group permission using  SGID
- SGID grants temporary **group-level permissions** when a file is executed, unlike SUID which grants owner-level permissions.
- When set on a **file**, users run it with the permissions of the file’s **group**, even if they aren’t members of that group.
- When set on a **directory**, new files or subdirectories inherit the **directory’s group ownership**, not the creator’s primary group.
- Useful for **collaborative environments** to maintain consistent group access.
- Set SGID by adding a `2` before the permission code:
- Example: `chmod 2644 filename` sets SGID on a file with base permissions 644.

![[Pasted image 20250815113347.png]]

The command `chmod 2644 test2` sets the **SGID bit** on `test2`, changing its permissions to `rw-r-Sr--`.
- The **`S`** in the group’s execute position means:
- SGID is set, but the file is **not executable** by the group (no execute permission).

### Sticky Bit
- The **sticky bit** is a special permission set **only on directories**.
- It restricts file deletion/renaming inside the directory so that only:
- The **file owner**,
- The **directory owner**, or
- The **root user**  can delete or rename files.
- Useful in **shared directories** (e.g., `/tmp`) to prevent users from deleting others’ files.
- Helps improve **security and control** in multi-user environments.


![[Pasted image 20250815113622.png]]
- `mkdir test` creates the directory.
- `chmod +t test` sets the **sticky bit** on it.
- `ls -l` shows `drwxr-x--T` — the uppercase **T** means sticky bit is set but others **lack execute permission**.
- Sticky bit restricts file deletion to owner, directory owner, or root.

### Special Permission and Privilege Escalation

- **Special permissions** like **SUID** can be exploited by attackers to escalate privileges from a normal user to **root or sysadmin** level.
- The **SUID bit** allows executable files to run with the privileges of the file’s owner, often **root**. Attackers can exploit this to run programs with elevated rights temporarily.
- For example, programs that handle password changes often have SUID set to access restricted files like `/etc/shadow`. This makes them potential targets for privilege escalation.
- To find all files with the SUID bit set and owned by root on a Kali Linux system, the `find` command is very effective:
 ``` Shell
 find / -user root -perm -4000 2>/dev/null
```

- This searches the entire filesystem (`/`) for files with SUID permission (`-perm -4000`) owned by root (`-user root`).
- The `2>/dev/null` part **suppresses error messages** (like “Permission denied”), making the output cleaner.    
- This command is useful for auditors, sysadmins, and attackers to identify files that might allow privilege escalation.


![[Pasted image 20250815114107.png]]

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