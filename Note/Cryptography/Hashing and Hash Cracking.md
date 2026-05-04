### Introduction to Hashing
- fundamental concept in cybersecurity
- process of taking input data and running through a hash function  which generates a fixed length string that represents the original input
- the output is called hash or digest
- idea: same input will produce same output, but it is nearly impossible to go backward from output to the input.
- Used to: store password securely, 
	- check whether files have been tampered  with ( using shasum command)
	- detect duplicate files and data
	- support many cryptographical protocols
- More on: https://www.redhat.com/en/blog/hashing-checksums
- unlike encryption, hashing is one way- we cannot decrypt hash
- if original input is lost there is no way to recover it just from hash

### How hash function work?
- a hash function takes input of any size and produces output of fixed size
- it doesnot matter whether the input is short or a long file- the output size remains constant

![[Pasted image 20260317212900.png]]
Good hash function follows these rules:
-  Deterministic: the same input always gives the same output
- Fast to compute: can handle large inputs quickly
- Irreversible: impossible to figure out the original input from hash 
- Collision- resistant: should be extremely unlikely that two different inputs produce same hash
- Avalanche effect: change in one bit of input drastically change the output

### Hash Collision and the pigeonhole principle
- hash collision happens when two inputs produce the same hash
- this is undesirable and secure hash function try to make it unlikely
- But mathematically, collision are unavoidable due to pigeonhole principle
- if there are more possible inputs than outputs, some inputs must share output
- For example, if you have 128 unique inputs but only 96 possible hash outputs, some of those inputs will map to the same output.
- Historically, some older algorithms like **MD5** and **SHA1** have been broken using engineered collisions—attacks where researchers created two different files that hash to the same value
- Reference : https://www.mscs.dal.ca/~selinger/md5collision/
			: https://shattered.io/

- these  hash function are no longer considered secure and should not be used for password storage or file verification

### Why use hashing for password?
- password should not be stored in plaintext
- database breach may expose the password
- Solution: database should store the hash of the password
- Process: enter password-> hash the input -> compare it to stored hash
-  same password= same hash
- this opens up the possibility for attackers to pre-compute list of hashes and corresponding password called rainbow table attacks

### Rainbow Tables
- rainbow table is a precomputed list of hashes for known passwords
- way to reverse hash by simply looking it up in massive database
- ![[Pasted image 20260504211850.png]]
- attacker sees hash in leaked database -> finds the match in rainbow table -> cracks the password 
- Online tools like https://crackstation.net/ and https://hashes.com/en/decrypt/hash use large internal rainbow tables to identify password hashes, specially for beginners

### Defending Against Rainbow Tables with Salts
- salt is a random string added to a password before it is hashed
- salt is different for different user so the final hash will be different for different user
- ![[Pasted image 20260504213645.png]]
- salt is random and unique per user, precomputed random table wont work unless attacker knows the salt
- ![[Pasted image 20260504213757.png]]
- salt are typically stored in the database alongside the hash
- salt  need not  to be secret
- common password-hashing algorithm  like bcrypt, sha512crypt, and argon2 handle salting internally

### Identifying Hash Format
- hash formats include a prefix that helps identify the algorithm used 
- ![[Pasted image 20260504214824.png]]
- in Unix system password hashes are stored in `/etc/shadow`, which is readable by the root user but in older system used `/etc/passwd`
- in windows password hashes are stored in the `SAM(Sequence Alignment Map)` file which is in `NTLM (New Technology LAN Manager)` format based on a weaker algorithm ( a variant of MD4)
- windows attempt to protect these files but tools like `mimikatz` can be used to extract and dump password hashes
- hash recognition tools like `hashID` can attempt to detect the hash type based on the format and length  but are not always accurate

### Cracking Hashes
recovering original password from a hash needs cracking hash
- guess a password ->  hash it (with same algorithm and salt ) -> compare the result to targeted hash -> repeat untill a match found
- for beginners easier way is to use crackstation and hashes.com
- wordlist like `rockyou.txt` to guess common password tools like hashcat or johntheripper

### GPUs and Cracking Speed
- hash function requires lot of math which suits GPU
- GPU cracking is faster than CPU cracking
- algorithms like bcrypt are specially designed to be slow and resist GPU acceleration 
- better for password storage since they slow down attacker

### Hashes for file integrity
- hashes can be used to check that file has been altered or not concept like checksum, CRC and Hamming code
- when a file is hashed  and a known good value is obtained( from developer or software vendor), we can rehash our local copy and compare the values
- if hashes matches file is unchanged 
- if differs the file is tampered, corrupted or replaced
- can be used to find duplicate files by comparing hash

### Summary
- hashing  is most useful tool in cybersecurity 
- allows us to 
	- store password safely
	- detect file tampering
	- find duplicate data
	- verify downloaded file
	