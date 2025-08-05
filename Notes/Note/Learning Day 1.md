1. Learning of day1 in overthewire
		file name can be anything like
		![[Pasted image 20250708215630.png]]
		'...Hiding-From-You' is a file and it can be opened using `cd '...Hiding=From-You'`

`-mime` command can be used to know if the file is human readable or not.
` file -mime -f filename`
this command can be used to know if the file is readable or not


2. Learning day 2
we can also find the file with ascii text using
``` Shell
file ./*
```
we can use find command with -size combined to find a file of a fixed size
``` Shell
find -size [size]bit/byte/gb # b for byte , c for byte , w for byte, 
find -size 1033c
```
![[Pasted image 20250709205655.png]]
we can use user and group with find command to find a specific file in a file system
![[Pasted image 20250709210209.png]]
here first column of root is user
and second column of root is group
the `drwxr` is permission for user `xr` is for group and `x` for other users
Condition
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size
 ``` Shell
 find /-user username -group group_name -size [size]sizenotation
 
 find /-user bandit7 -group bandit6 -size 33c
```

![[Pasted image 20250709210638.png]] 
this looks messy so we can redirect the standard error(stored in 2) to a /dev/null file 
``` Shell
find /-user bandit7 -group bandit6 -size 33c 2> /dev/null

```
![[Pasted image 20250709211022.png]]

before this i thought grep searches the word only but it searches the word and displays the whole line that has the word when combined with cat
``` Shell
cat data.txt | grep 'millionth'
```
![[Pasted image 20250709214416.png]]

wirh reference to [[Linux Commands#Strings Command]] 
we can also use [[Text Manipulation Command#Regular Expression]] with combination of `grep` to search a fixed length password by analysing their combination
``` Shell
grep -E 'expression' filename
grep -E '\b[A-Z,a-z,0-9]{32}\b' passwrd.txt

```
-E for regular expression [...] for content then {length of expn} \b\b for  word boundary 

![[Pasted image 20250709225730.png]]

when we use grep functions if there is not plain text then it does not show the output. So we can use the command -a which process the binary file as text. then shows the output
By taking example of binary file in bandit 9-10, when we use grep command it doesnot show output because `**data.txt** in one of the few human-readable strings, preceded by several '='` is the hint in question. thats why it treats the human readable as string as binary so it doesnot produce output.
In order to solve this we can use `-a`
![[Pasted image 20250709230905.png]]
  The major learning from this say is we can combine `-E` and `-a` like command in singe unit `-Ea`
  
## Base 64 in bandit
we can decode a base64 text directly by using `base64` command and option `-d` to decode
``` Shell
#syntax
base64 [option] [file
base64 -d data.txt #decodes base64 encoded data of data.txt
```

![[Pasted image 20250710000137.png]]

### Day 3
bandit 11-->12
in case of rot 13 we can use translate `tr` command to translate the content
``` Shell
cat filename | tr 'A-Za-z' 'N-ZA-Mn-za-m' # to encode into or decode ROT13 cipher code
cat hello | tr 'A-Za-z' 'N-ZA-Mn-za-m' 
tr 'A-M,a-m,n-zN-z' 'N-Z,n-z,A-M,a-m' < filename
#we can also use this but it is long anc inconvient to read so its better to use first one
```

Original:
![[Pasted image 20250710205443.png]]
Translation:
![[Pasted image 20250710205419.png]]

### temporary file
we can create temporary file using the command `mktemp -d` to create a temporary directory in root `/` then inside temp folder
![[Pasted image 20250710223122.png]]

Approach for bandit 12-13
Q--> repeatedly compresedfile-->hexdump
solution approach:
rev hexdump --> decompress
again decompress then again decompress till we find the flag
``` Shell
xxd -r filename > filename
file filename
mv filename filename.filetype
gzip filename.gz #if file is gunzip
gzip -d filename.gz # to decompress the gz file
mv filename filename.bz2 # if file is bunzip
bzip2 -d filename.bz2 # to decompress the bunzip file

```
we can repeatedly decompress using this
to get final output
 Bandit 13-14
 