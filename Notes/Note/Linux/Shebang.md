shebang or hashbang is  a character sequence consisting of character number determining the type of program
it treats the file as intepreted program and remaining file content as path of interpreter
common types of shebang are
`/bin/bash` for bash script
`/usr/bin/python3` for python script
`/bin/sh` for shell script

### Conditionals in bash
we can use conditions like if condition in bash
``` Bash
# syntax
if [ condition]
then 
operation
fi

```
here `if` is closed by `fi` it acts like `endif` the space after `if` is compulsary

we can use `else` conditional statement for false conditon of if
```Shell
if [condition]
then
	operation
else
	operation
fi
```

we can also use `elif` for multi conditional statement
``` Shell
if [condition]
then
	operation
elif [condition]
then 
	operation
else
	operation
fi

```
then is compulsory after else if condtion
![[Pasted image 20250729205931.png]]
