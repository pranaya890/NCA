## Basic Linux Commands

`whoami` is used to display the current user's username
```shell
whoami
```
Output
```shell
pranaya
```

###  printing a message

`echo` is used for displaying a message or writing a message same as `printf` and `print`
we are writing hello kali on hello.txt
``` shell
echo "Hello Kali" > hello.txt
echo "Hello Kali" # for displaying a message
pd=55
echo $pd #prints the value of pd
```

watchout:
``` Shell
echo >(man) #shows the location of 
```
### Creating a new file
``` Shell
touch filename.txt
```

### Make Directory
``` Shell
mkdir myfolder
```
### Remove a file/Directory
```Shell
rm filename.txt
rm -r foldername #removes folder and content inside it
```

### Printing Current Directory
pwd -print current working directory
print the path of current working directory
``` shell
pwd
```

### Copying the file or folder
```Shell
cp source.txt destination.txt
cp -r source_folder destination_folder
```

### Copying a file using relative and absolute path
``` 
/home/honi/
|--notes
| |--file.txt
|__backup/
```
Suppose this is my file structure and i am currently in home/honi
``` 
cp notes/file.txt backup/ #to copy file.txt from notes/ to backup
```
The above example  shows the example to copying a file using relative path i.e. i am currently in home/honi and with relative to my current location i can copy it
```
cp /home/honi/notes/file.txt home/hero/backup
```
the above example shows the file is copies using path from root `/` directory

### Moving a file/folder
``` Shell
mv oldname.txt newname.txt #for renaming a file
mv file.txt /home/location # for moving a file to another location
```

### Viewing File Content
`cat` is used to view the entire content of a file. Below code reads and prints the content of a file `hello.txt`
```shell
cat hello.txt
```
`less` command is used to view large page by page. opens file in scrollable view by down and up arrow
```
less filename.txt
```
`head` is used to view the top of a file
```
head filename.txt
head -n 20 filename.txt # shows the first 20 lines 
```
`tail` is used to view bottom of a file
```
tail filename.txt
```


### Path 
Location of a file in a system
Absolute path: Full path from root directory

Relative path: Path of a file relative to current directory
### navigating  in terminal
`cd` -Change directory
used for changing directory
```shell
cd <filename>

```
`cd ..` - returning to previous directory ( <- )
``` shell
cd ..
cd ~ # returning to  home directory 
cd / # return to home directory
~ #can be used to know the home directory
~/~ #can be used to go to /home/pranaya/~ rather than /home/pranaya/home/pranaya that is it will create a `~` directory in home directory
```

![[Pasted image 20250722215233.png]]


ls -list
used for listing all files of a directory
``` shell
ls
ls -l #list with details
ls -a #list hidden files
ls -la #both
```
### Getting Help
 `help` can be used to get list of commands in help 
 but if stuck in the command syntax then we can use help command for figuring the thing out
 ``` shell
 <command-name> --help
 #Example:
 ls --help
 cat --help
```
### Hidden Files
`.hidden_file` are not included in ls so we can use `ls -la`
``` shell
ls -la # for listing alll files including the hidden files
```

to open a hidden file use `cat .filename`
notice the number of dot before a filename single dot (.) is before the file name
if more than one (.) is before hidden file its a trap

![[Pasted image 20250708215630.png]]



### Manual Command
`man` command can be used to find the manual of a certain command 
``` shell
man <command_name>
#example
man ls
man ls -i #  ls -i for finding the index number of file
```

### Cheat Commands

``` shell
curl cht.sh/<command_name>
```


### Tree command
`tree` help to show the file structure of tree
``` shell
tree
```


### I/O Control Command
```
-i #for case insesitive search
-n # for shwoing line numbers in output
-r #recursive search inside directories
```
### Searching in a file

`grep` Command can be used for  searching and displaying particular string in a files.
``` shell
grep "pattern" filename
grep "hello" hello.txt
cat hello.txt | grep "Hello" #searches the word hello in hello.txt
#we can combine command with pipe |
grep -v "pattern" filename #is used to get the line that doesnot match the pattern i.e works reverse of grep
```
displays the full line in which the data is stored
![[Pasted image 20250709213904.png]]
like this
![[Pasted image 20250709213925.png]]

### Find Command
`find` is the powerful command used in linux. it helps to find a specific thing in a file or find a file.
```shell
find / -name 'hello.txt'
find -name <filename> 2>/dev/null #to find a file and redirect the error ro /dev/null
find -name <filename> >op.log 2>err.log #this redirects the standard input and standard error in two diferent files
fine -name 2>&1 | grep "hello" #this is grepping standard error we cannot directly grep standard error we have to use &> operator to change the file descriptor while grepping
```

### Locate Command
 `locate` commands finds files quickly in a system matching given pattern if multiple are given
 ``` Shell
 locate <filename.txt>
 locate hello.txt
```


## To seperate a command
`--` can be used in linux to seperate a command with other

### File command
file is used to determine type of file
`--mime-type` is used to output the mime type
![[Pasted image 20250708224404.png]]

### `uniq` command

`uniq` is used to report or omit repeated lines.  delete repeated line in a file
``` Shell
#syntax
uniq [option] ... [input[output]]
```

`-u` can be used to print unique lines
Note: Uniq  command  works in sorted data only
``` Shell
sort filename | uniq -u
# sorts the file then display only those things which are unique
```
![[Pasted image 20250709221802.png]]

### Strings Command

`strings` is  a standard c library. same as in c it can be used to perform string operations like `strcmp` , `strcat` , `strcpy` 
like this, but the base command `strings` can be used to display data.
Note: its `strings` not string. use plural
![[Pasted image 20250709222932.png]]
 we can use `strings` command pipe lined with grep to print the line with a searched string
``` Shell
strings filename | grep 'search_string'
strings passwd.txt | grep '='
```
![[Pasted image 20250709223241.png]]


### `tar` command
it is an archiving utility.
it can be used to create , delete , append update an archive file
example uses ` tar --create`  `tar --delete` 
`tar` can also be used to extract a data from archive like `tar -xf filename`
`-x` is used for extract and f tells that next argument is filename.s


### `file` command
 it can be used to manipulate file in a directory.`file filename` shows the details of a file 
 ![[Pasted image 20250710231259.png]]
 it shows file type creation date time etc

### look command
`look` command  is used to  display a line beginning with given string
``` Shell
look [option] string [file]
```
![[Pasted image 20250723223850.png]]

### Piping commands
we can combine commands using `|` 
``` Shell
cat hello.txt | grep "Hello" #searches the word hello in hello.txt
#we can combine command with pipe |
```

### Named pipes
`mkfifo` can be used to make named pipes 
`mkfifo hello` 
![[Pasted image 20250728205607.png]]
`p` in permission  says its a pipe
we can control the creation of fifo
any process can write them by path
fifo needs both end  ready both readers and writers
i.e the pipe must be completed
![[Pasted image 20250728210227.png]] 
this process is hanged untill  the reader side is ready 
![[Pasted image 20250728210426.png]]


### `tee` command
tee command can be used to read from standard input and write to standard output and  one or more files
![[Pasted image 20250724211343.png]]

```
echo "hi" | tee pwn college
# this will make three copies of hi one in standard output one in pwn and one in college

```

example of pwn.college/dojos/linux-lunarium/piping 
for duplicating data to a file

![[Pasted image 20250724213225.png]]

### Process substitution
it allows the  a process input or output to take it as a filename.
it is in two form `<(rev)` or `>(rev)`
![[Pasted image 20250724215221.png]]
in above example `>(rev)` is treated as filename
then in second process hi is printed and filename of rev is printed
in  third process the echo hi prints hi then it is piped to std input of (rev) which is treated as filename
then rev is a command then it takes the input and reverses hi then it is shown as an output
![[Pasted image 20250724215757.png]]


example is
![[Pasted image 20250724220808.png]]

ultimate piping test of pwn.college/linux-luminarium/ piping

![[Pasted image 20250724222125.png]]

### Cut command
cut command is used to cut out some chunk of output and display in standard output
``` Shell
#Syntax
cut OPTION [FILE]

```


### chaining commands
#### with `;`
we can chain multiple commands using a `;` 
![[Pasted image 20250728220157.png]]

#### with `&&`
this is  and command in linux which executes second command if the first one is true
this checks if exit code is `0` or not if true it executes else no
``` Shell
command1 && command2
```
![[Pasted image 20250728220732.png]]

#### with || 
this command is similar to or command. this executes  second command it the first command fails
![[Pasted image 20250728221128.png]]

#### Shell script
we can create a shell script file using`.sh` extension
then we can append te command in that file and run it using `bash` command
what it does is, it rather than taking command from user it takes it from file
 