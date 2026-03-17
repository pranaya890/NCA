
### Encoding and Decoding
- Encoding is process of converting data into different format for compatibility, storage and transmission
- doesnot involve secrecy or security but ensures that data can be properly processed by different systems
- commonly used in data transmission, file storage and text representation

- Decoding is the process of converting encoded data back into its original form
- it doesnot require a secret key  anyone with knowledge of encoding can decode the data


![[Pasted image 20260317203508.png]]
#### Online Cryptographic Tools 

1. https://gchq.github.io/CyberChef/
2. https://www.dcode.fr/en
3. https://toolkit.ncateam.xyz/
4. https://crackstation.net/  for online password cracking
5. https://hashes.com/en/decrypt/hash online password cracking website


## Encryption
- process of transforming plain text into cipher text using cryptographic algorithm and key 
- goal is to make the unintelligible to anyone who does not have the correct key to decrypt it
- Encryption can be performed using various algorithm, two main types:
1. Symmetric Encryption: 
	- both sender and receiver  use the same key for encryption and decryption
	- main challenge is securely sharing the key between both parties
	- Example: AES ( Advanced Encryption Standard)
2. Asymmetric Encryption: 
	- involves pair of keys: a public key for encryption and a private key used for decryption
	- public key can be freely shared, but the private key remains secret
	- Example: RSA, Elliptic Curve
Tool: https://www.devglan.com/online-tools/aes-encryption-decryption

### Decryption
- reverse process of encryption
-  converts cipher text  back into plaintext using a cryptographic algorithm and key 
- receipent have to use the correct key to decrypt the data and recover  the original message 
- In symmetric encryption, the same key is used for both encryption and decryption
- In asymmetric encryption, the private key is to decrypt data that was encrypted with corresponding public key 


![[Pasted image 20260317204743.png]]

