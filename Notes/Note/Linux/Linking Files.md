Linking a file is making a symbolic connection or pointer to a file that allows us to excess the same file from different location.
files can be linked in two ways hard link and soft link
file is basically an address that hold the location of the content of the file.

`Hard link` is the original location of file where the file content original address is linked.
sound simpler but has implementation issues
`Softlink` is the way of linking the address of the file to the hard linked file. sound complex but easier and simpler method of linking

![[Pasted image 20250723203442.png]]



`ln` command can be used to create a link between the file. 
`-p` creates a hard  link and `-s` creates the soft link instead of hard link

``` Shell
ln -s <source> <destination>
```


![[Pasted image 20250723205248.png]]


symlink file can be identified using `file` command and `ls -ahsl` 
`-a` includes all file and not to ignore anything
`-h` is to include human readable file only
`-s` for printing the size
`-l` if for links of the file

![[Pasted image 20250723205328.png]]
