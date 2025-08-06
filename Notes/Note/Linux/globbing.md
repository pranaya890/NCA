globbing is the way of matching or expanding the specific types of patterns
same as `%a` in python that will search in the file the word ending with a
same in linux we can use different symbol to match or expand specific type of pattern
![[Pasted image 20250723222734.png]]

### wildcard 
#### `*` wildcard
whenever `*` is encountered in an argument then the shell treats it as wildcard it expands or matches the pattern
![[Pasted image 20250723222924.png]]
here in the example the  wildcard will search a file/directory starting from `dem`

![[Pasted image 20250723224606.png]]
this is the example of wildcard used in shell to go to `/challenge` directory and run it using wildcard. this is the challenge of linux lumarium/ file globbing in pwn.college

#### `?` wildcard
it is same as `*` wildcard but compares only one character after it
![[Pasted image 20250723225037.png]]
in linux-lunarium/globbing/working with `?` we can use this 
![[Pasted image 20250723225305.png]]

#### `[]` wildcard
this wildcard compares the wildcard with the dictionary included in it
```Shell
ls Deskto[pqr] #it matches `pqr` with the last letter and prints
```

##### matching  path with `[]`
![[Pasted image 20250723230352.png]]
##### exclusionary globbing
it is used when we have to filterout some pattern suppose `filea`, `fileb`, `filec` if i want to exclude the file name ending from a i can use `!' or '^'
``` Shell
echo File: file[!a] #it prints Look: fileb and Look filec
```