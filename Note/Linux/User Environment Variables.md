Sure! Here's the **single-topic summary in bullet points** for easy note-taking:

---

### **Environment Variables in Linux – Key Points**

- Environment variables are **key-value pairs** used to configure the behavior of the operating system, applications, and processes.
- They provide **dynamic configuration** without hardcoding values in scripts or programs.
- Used to store information like:
- File paths
#### **Common Examples:**

- `PATH`: Directories where the system searches for executable files.
- `HOME`: Current user's home directory.
- `USER`: Current user's username.

#### **Uses and Benefits:**

- **Customization**: Adjust system or application behavior per user or environment.
-  **Security**: Store sensitive data outside of code to reduce exposure.
-  **Scripting**: Scripts can access and use environment-specific data.
- **Portability**: Ensures cross-platform compatibility for applications.
- **Flexibility**: Easily update configurations without modifying code or scripts.
- Overall, environment variables make Linux systems more **secure**, **configurable**, and **user-friendly**.
## Viewing and Modifying Environment Variables
- Use the `env` or `printenv` command to **list all current environment variables**.
- Both commands display variables in the format: `KEY=value`.
- The output shows system-defined variables like `SHELL`, `HOME`, `PATH`, etc.
- Environment variable names are conventionally written in **uppercase**.
- These commands **do not show user-defined shell variables** (local to the shell session).
- To see all shell variables, including user-defined ones, use the `set` command (note: it shows more than just environment variables).
- You can also use `echo $VARIABLE_NAME` to **view the value** of a specific variable.
- Environment variables can be **temporarily modified** in the shell by using `VARIABLE=value` syntax before a command or by exporting it.
- To **permanently modify environment variables**, add export statements to configuration files like:
- `~/.bashrc` (for bash shell)
- `~/.zshrc` (for zsh shell)
- `~/.profile` or `/etc/environment` (for login shells)
![[Pasted image 20250820002233.png]]
![[Pasted image 20250820002308.png]]

## Filtering for Particular Variables
- The `set` command lists all shell and environment variables, but the output can be overwhelming.
- To make it more readable, use `set | more` for **paged output**, allowing you to scroll through results.
- For **faster and more precise searching**, use the `grep` command to filter for a specific variable.
- Example: To find the `PATH` variable, use `set | grep PATH` or `printenv | grep PATH`.
- This method quickly locates variables without manually scanning through a long list.
- The `PATH` variable:
- Contains a **colon-separated list** of directories.
- These directories are searched **in order** when you run a command.
- It **does not store commands**, only **directories where commands may exist**.
- The **first matching executable** found in the listed directories is the one that gets executed.
![[Pasted image 20250820002507.png]]
This will filter the output of `set` to display only the lines containing the `PATH` variable, making it easier to locate and inspect.

## Understanding and Modifying Your PATH Variable
- The `PATH` variable is one of the **most important environment variables** in a Linux system.
- It defines the **directories the shell searches** for executable commands when you type a command.
- Common commands like `cd`, `ls`, and `echo` are found by checking the directories listed in `PATH`.
- These directories are **searched in order**, from left to right (first match is used).
- Typical directories in `PATH` include:
- `/usr/local/sbin`
- `/usr/local/bin`
- `/usr/sbin`
- `/usr/bin`
- `/sbin`
- `/bin`

- If a command exists but is **not located in any directory listed in `PATH`**, the shell will return:
- `command not found`
- This error occurs even if the command **does exist**, just not in a `PATH`-included directory.
- Modifying `PATH` allows you to:
- **Add custom script locations**
- **Prioritize certain tools or versions** of commands
- Temporary changes can be made in the current shell using:
- `export PATH=/new/directory:$PATH`
- Permanent changes should be made in configuration files such as:
- `~/.bashrc`, `~/.zshrc`, or `~/.profile`
![[Pasted image 20250820002811.png]]
These are the directories where  terminal searches for commands. For instance, when we type `ls`, the system checks each of these directories in order, finds the `ls` executable, and runs it. Each directory in the `PATH` is separated by a colon (`:`)
## Adding a Directory to Your PATH Variable

