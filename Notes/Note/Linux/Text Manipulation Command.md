Text manipulation is the collective name for reading, writing, deleting, and editing text

#### Viewing Files
`/etc/passwd` file is a critical system file in linux that stores user account information
 above directory has `username:password` stored in /etc/shadow` #shadow directory lai sudo permission chainxa
 ![[Pasted image 20250707213415.png]]
 `root:x:0:0:root:/root:/bin/bash` describes the root user with UID 0, home directory `/root` and `/bin/bash`

### Filtering text
Filtering is narrowing the data on required condition.
Important because it takes less space in terminal and terminal does not look messy
Easier to read and find the thing needed
#### More Command
displays the content of file but one full page at a time 
primitive way of filtering
limitation: backward  navigation unavailable
```
more /etc/ssh/ssh_config
```
![[Pasted image 20250707214919.png]]
 we can directly scroll to bottom by clicking down key
 `space` can be used to move to next page
#### LESS command
`less` is more advanced and versatile tool
allows backward and forward navigation
supports searching
memory efficient
```
less /etc/ssh/sshd_config
```
can be navigated through `up_arrow` and `down_arrow`
`j` and `k` can also be used for navigating up and down
`space` can be used for going to next page and `b` for back page
`/<searchitem>` is used for search forward
`?<searchitem>` to search backward
After searching `n`  jumps to next match and `N` to previous
`g` to go to start of file
`G` to go to end of the file

![[Pasted image 20250707222848.png]]
#### Head Command
displays first few lines of a file
deafult 10
`head -n 5 /etc/passwd` #displays first 5 lines
![[Pasted image 20250707223246.png]]

#### Tail Command
Displays last few lines of file
default 10
`tail -n 5 /etc/passwd` #displays last 5 lines
![[Pasted image 20250707223820.png]]
#### Cut command
Used to extract specific columns fields or characters
` cut -d':' -f1 /etc/passwd` 
here `-d` is delimiter i.e specific symbol that separates the data and `-c` can be used for character
':' is a delimiter
-f1 is first column
![[Pasted image 20250707224555.png]]

#### Word count
In order to count lines, characters and word using `wc` command
`-l` `-w` `-c` can be used to count lines word and character respectively
`wc -l /etc/passwd`
![[Pasted image 20250707224942.png]]

#### sed, sort, awk, tr, and column command

#### Sort 
`sort` command is used to alphabetically sort lines of text file 
```
sort /etc/passwd #displays alphabetically
sort -t: -k3n /etc/passwd #sort user by uid i.e. 3rd field
```
-t: tells sort to use : as delimiter
-k3n sorts numerically by the 3rd field
![[Pasted image 20250707230507.png]]

#### awk

`awk` is used for pattern scanning and processing
```
awk -F: '{print $1,$7}' /etc/passwd
#prints first and 7th column
awk -F: '$7== "/bin/bash" {print $1 }' /etc/passwd
# prints those username whose 7th column ins /bin/bash

awk -F: '$3=="0" {print $1}' /etc/passwd
#print the username if column 3 is 0

```



#### tr (translate)
tr is used to translate or delete character
```
tr "0-9" "*" #replaces digits by asterick
tr -d "0-9 " #removes the digits
```
![[Pasted image 20250707232514.png]]
![[Pasted image 20250707232533.png]]

#### Column 

`column` is used to format text to column
or to columnate i.e to arrange sth in column
column
takes input from a file or std input and arranges the data in column
Default mode: fills column before rows
-x can be used to fill rows before columns
``` Shell
column hrllo.txt
```

![[Pasted image 20250708125501.png]]
we can create table with the help of delimiter to seperate columns
```
column hrllo.txt -t 's "/' #-t for tabel ans -s for defining delimiter
```
![[Pasted image 20250708125830.png]]
this command is really helpful to make a messy data readable


#### Sed 
`sed` command is used for text substitution, deletion or manipulation. 
we can manipulate text files without opening in text editor
make it ideal for automating edits batch files, working with log files and performing fast conversion
Example: log file ma dherai chij hunxa ani tyo log file ko log lai readable banauna ko lagi sed command use garinxa
``` Shell
sed 's/Hello/xyz/2' # replace second Hello of a file by xyz
sed '3 s/Hello/xyx/2' #replace second hello of third line
```
![[Pasted image 20250708123512.png]]

![[Pasted image 20250708123445.png]]

`sed` for deleting a line
``` Shell
#Syntax:
sed 'nd' filename.txt
sed '5d' hrllo.txt # deletes 5th line of hrllo.txt
#$d can be used to delete the last line
```

#### File descriptors and redirections
this allows us to manage input, output for command processes.
numerical identifier that controls where data is read from and written to
0(Standard input), 1(standard output) and 2(standard error)  are standard file descriptors 
redirection allows us to change where the input comes from or where the output goes. simply changing the flow of input and output

##### redirecting standard output
`>` command can to used to redirect  output of a command to a file
``` Shell
ls > hello.txt #redirects the output of ls to hello.txt
```
![[Pasted image 20250708131525.png]]

`>>` can be used to append  output without replacement

![[Pasted image 20250708131821.png]]

`2>` can be used to append  standard error to a file
```Shell
ls /ram 2> error.log # write the error occured to error.log file
ls /sam 2>> error.log
```
![[Pasted image 20250708132241.png]]

`&>` can be used to append both std o/p and error
``` Shell
ls /ram &> op.log #appends the op and error of ls/ram in op.log
```

![[Pasted image 20250708132650.png]]

`<` can be used to take standard input
![[Pasted image 20250708133028.png]]


### Pipes
it is the symbol that connects two or more command directly at input
`|`  = Shift+\
``` Shell
cat password.txt | grep 'ram1234' # displays ram1234 from password.txt
```
![[Pasted image 20250708133311.png]]

### Regular  Expression
 art of expression language to search for patterns in text and files
 can be used to find and replace text analyze data, validate input, perform searches
Sequence of letters and symbols that forms a condition for search pattern
can be created used metacharacters
metacharacters are symbols with no literal meaning 
can be used with grep 
used in google analytics in URL matching
RegEx is implemented in web for validation of user input i.e. to check the RegEx [https://regexr.com/]()

![[Pasted image 20250708135342.png]]
1 expression panel : for writing expression
2 text panel: we write the text to be tested here
3 test panel: allows us to create a suite that can be used to validate my expression
4 replace panel:  replaces the match with a specified string
5: List : lists all the matches found
6:details: displays the match and its details
7: Explain tool: detail breakdown of expression


`RegEx` is case-sensitive tool and can be used with grep command in linux with  `-E` --> `extended-regexp`  
Some rules:
+ can be used to join two condition/expression like AND operation
+ In Linux `RegEx` should be included inside quote ` 'expression' ` 
+ `*` symbol is used for repetition of single character from 1 to infinity


```Shell 
grep -E '[T]+[o*]+[l]' regex.txt #searches To*l in regex.txt can either be Tool, Tol Toool
```
![[Pasted image 20250708142356.png]]


``` Shell 
grep -E '\b[a-z,A-Z,0-9]{32}\b' passwd.txt
#searches for 32 lettered word that contains a-z,A-Z,0-9
```

![[Pasted image 20250709224954.png]]
![[Pasted image 20250709225105.png]]
testing regular expression (practice platform)
![[Pasted image 20250709225152.png]]


### `diff` command
`diff` command is used to find the difference between two file. 
compares two files and print the different lines in both files
``` Shell
diff <file1> <file2>
#this prints the different line of first file then seconf file
```

### `--printfile` argument
this argument tells an `.exe` file to print the content of the file
``` Shell
<.exe file> --printfile <filename>
```

![[Pasted image 20250723213339.png]]
