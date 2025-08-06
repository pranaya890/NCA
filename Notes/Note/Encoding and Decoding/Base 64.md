that encoded string that represents binary data to ASCII
we can use `base64` command to encode or decode a text in base64
``` Shell
base64 [option] [file]
# -d option for decode 

base64 -d data.txt
```
![[Pasted image 20250709235858.png]]

## ROT13
it is the way of encrypting the message by replacing a letter with thirteen letter after it
![[Pasted image 20250710000509.png]]
 Interesting fact discovered: rot 13 is symmetric A--> N same way N-->A
 let x be the thing to be translated
 ROT13(ROT13(x))=x
 technique of translating: shifting the letter by 13th letter after it.
 spaces, symbols 


### Hex Dump
 Hex dump is textual hexadecimal view of computer data
 used in debugging, reverse engineering and forensics
 in hex dump each byte of data is represented by two digit hexadecimal number.
 ####  Hexadecimal
it is the positional numeral system the represents a number using base 16 
Example:
A is 10
B is 11
up to F 15
used by  developers and designers because they provide a convenient representation of binary-coded values.

` xxd` command can be used to create a hex dump file or reverse it. 
``` Shell
xxd [option] [filename]
xxd -r hello.txt # reverses the hex dump file
xxd -r hello.txt > out # redirecting the output to out

```



