### Using `crunch`
- crunch is the tool used to generate wordlist  from a character set
- it can create wordlist based on given crieteria
- output can be sent to a file, screen or another program
- Required parameters: min-len, max-len, and charset string
``` Bash
crunch 4 4 ABCDEFGHIJKLMNOPQRSTUVWXYZ -t A,,, -o wordlist.txt
#generate a wordlist starting from A
```
