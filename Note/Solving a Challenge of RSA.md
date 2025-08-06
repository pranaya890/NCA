Question:
A suspicious message sent from our server to a public key `115698027965884253679338276941738696579` and here is the cipher `58368403079454930605344558159623799130` and e `65537`.

Can you find what was the message ?

Approach: 

Given: we have been given a public key message cipher and exponent number

Decoding approach:
public key is denoted by `n` in RSA which is the multiple of p and q which is a large prime number `n=p*q`

at first we have to find two prime factor of n
of number `n` for that we can use [dcode.fr](https://www.dcode.fr/decomposition-nombres-premiers)

then we have to calculate a totient function phi which is the product of `p-1` and `q-1` mathematically 
`phi= (p-1)*(q-1)`
 then after that we have to calculate `d`
 which is the modular multiplicative inverse
 i.e modulating the inverse of exponient
  Example if we have to calculate the modular multiplicative inverse of `e` with respect to totient function then we can calculate 
   `d*e=mod phi`
   `d=e^-1 mod phi`
   which can be calculated using `pow()` function in python 
   ```Python
   pow(e,-1,phi)
   
```
d can also be calculated using the inverse function of `from Crypto.Util.number import inverse`
``` Python
from Crypto.Util.number import inverse
d=inverse(e,phi)
```
hence the gained output `d` data type is long int
then we can find the long int representation of message by using formula `msg=ci^d mod n`
which can also be written as `msg=ci^d %n`
```Python
msg=pow(ci,d,n)
```
hence calculated long int representation of message should be converted to bytes

for the next step after finding `p,q and d`
we can directly find the bytes of message using the function `long_to_bytes` from the library `Crypto.Util.number` 
```Python
from Crypto.Util.number import long_to_bytes
message=long_to_bytes(d)
```
hence found message is the required decoded message
![[Pasted image 20250715223304.png]]



### Encoding a message using RSA 
Steps:
- generate a public key 
- write the message
- encode it using public key
#### Generating a Public key
first what is a public key made up of?
public key is the multiple of two large prime numbers so for generating a public key we need to generate two prime number which can be generated using `getPrime()` function of  `Crypto.Util.number` of `1024` or `2048` byte
``` Python 
from crypto.Util.Number import getPrime
p=getPrime(1024)
q=getPrime(1024)

```

![[Pasted image 20250715224039.png]]
then we have to multiply both number `p and q ` to get the value of n
```Python
n=p*q
```
we can use multiple prime number to make a public key for more visit [this site](https://medium.com/@zeroair41/unlocking-the-secrets-of-rsa-encryption-a-beginners-guide-with-wanictf2024-4f4259ac35d4)

#### Making a message to encrypt
we can make the message in bytes simply by using `var_name=b'message'`
``` Python
m=b'message' #converts the message to bits
```
then we can use `bytes_to_long` function by importing from `Crypto.Util.number` to convert the message to long. 
``` Python
from Crypto.Util.number import bytes_to_long
msg=bytes_to_long(m) #converts message bytes to long
```
then we can encode the message using the pow(m,e,n) which is equal to `pow(m,e)mod `
![[Pasted image 20250716134325.png]]

