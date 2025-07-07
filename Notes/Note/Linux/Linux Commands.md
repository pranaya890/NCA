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
head -n 2- filename.txt # shows the first 20 lines 
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
```

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
```

### Find Command
`find` is the powerful command used in linux. it helps to find a specific thing in a file or find a file.
```shell
find / -name 'hello.txt'
```

