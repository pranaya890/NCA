- My friend Harka Sampang has been learning Python for 6 months. He now has wizard-like skills and can print `'Hello World'` in multiple ways! Damn!
``` Python
#main.py

from functools import reduce

chars = [72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100]
  
hello_world = ''.join(map(lambda x: chr(x), chars)) # ​‌​‌​‌‌‌​‌‌​‌​​‌​‌​​​​‌‌​‌​‌​​‌‌​‌‌‌‌​‌‌​‌‌‌‌​​‌​​‌‌​​​​​​‌‌​​​​​​‌‌​​​​​​‌‌‌‌‌‌​​‌‌‌‌‌‌​‌​‌‌‌‌‌​​‌‌​‌‌‌​‌​​‌​​​​​‌‌​​​‌​​‌‌​‌​‌​​‌‌​‌​‌​‌​‌‌‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌‌​‌​‌​‌​‌‌‌‌‌​‌‌​‌‌‌​​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​‌‌‌​‌​‌‌‌‌‌​‌‌​​‌‌​​​‌‌​‌​​​​‌‌​‌​​​​‌‌​​​‌​​‌‌​​​‌​‌‌‌​​‌​​‌​‌​​‌​​‌‌‌​​‌​​‌‌‌​​‌​​‌​‌‌‌‌‌​​‌‌​‌‌​​‌‌‌​‌​‌​‌​‌‌​​‌​​‌‌​‌​‌​​‌‌​‌​‌​​‌​​​​‌​​‌​​​​‌​‌‌‌‌‌​‌

output = reduce(lambda a, b: a + b, [hello_world])
print(output)
```

# Solution
- here we can see that there is a comment in `hello_world` variable but it cannot be seen
- that means there lies a non printable character
- Option 1: we can use the `cat -v` to see the non printable character
![[Pasted image 20251127211418.png]]


- Option 2: https://www.soscisurvey.de/tools/view-chars.php
![[Pasted image 20251127211607.png]]

- Option 3(simplest) : we can copy the comment and paste it in terminal to see the non printable characters
![[Pasted image 20251127212117.png]]


then we found the non printable characters and we can observe the patterns in it.
from that we can guess `<200c>` is either 1 or 0 and same for `<200b>`

then we can convert it to binary in 2 variables by replacing <200c> with either 0 or 1 and same for <200b>

now we got the possible flag in binary then we can convert the binary to sting using `unbits` from `pwn`

