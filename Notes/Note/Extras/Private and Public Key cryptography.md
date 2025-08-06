## Understanding
- computer understand everything in binary
- ASCII value is used to convert char to int then the integer is converted to binary so that the computer can understand
- ASCII is the standard value used to convert any char to integer
- ASCII value of a is 65
``` Python
ord('A') #can be used to find the ascii value of a char
>>> 65

```
- we can use `chr()` to convert a ASCII value to character
```Python
chr(97)### to convert ASCII 97 to character
>>>a
```
- we can declare the byte type variable directly by using `b''`
``` Python
x=b'hello'
type(x)
>>> <class 'bytes'>
```

### Importing a RSA key
- copy the rsa key from bandit for example
``` Python
from Crypto.PublicKey import RSA #importing the PUblicKey library
key=open('key.txt','rb'),read() #import the RSA key containing file Key.txt in bytes 
#printing key will show b'content'
key_name=RSA.import_key(key_name)


```
- output after importing
![[Pasted image 20250715164154.png]]
key_name.d contains decryption key
key_name.e contains exponent key

the key can be used to convert a data to cipher. suppose a following text
``` Python
m=b'hello how are you?'
```


## Illustration

