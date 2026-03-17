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
