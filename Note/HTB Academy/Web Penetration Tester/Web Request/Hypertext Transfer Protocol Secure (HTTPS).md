-  a drawback of HTTP is the data are transferred in clear text 
- anyone between source to destination can perform a Man-in-the-Middle (MiTM) attack to view the transferred data
- to counter this issue HTTPS was created in which all communication are transferred in encrypted format
- if the third party does intercept the request they would not be able to extract data out of it
- HTTPS has become mainstream scheme for websites on the internet 
- HTTP are being phased out and soon most web browser will not allow visiting HTTP websites

https://datatracker.ietf.org/doc/html/rfc2660

### HTTPS Overview
- if we examine HTTP request we can see the data sent are sent in plain text and we can easily intercept and see it
- ![[Pasted image 20260508154339.png]]
- the login credentials from above example can be reused for malicious purpose
---
- But if we analyse the HTTPS request we can see the data is transferred as a single encrypted system
- which makes it difficult for anyone to capture information as credentials
![[Pasted image 20260508154550.png]]

---
- websites that use HTTPS can be recognized through `https://` in their URL
- or else we can see the lock icon in the web browser to the left of URL
![[Pasted image 20260508154730.png]]
- if we visit those sites  all traffic would be encrypted
>[!Note]
>	Although the data transferred through the HTTPS protocol may be encrypted, the request may still reveal the visited URL if it contacted a clear-text DNS server. For this reason, it is recommended to utilize encrypted DNS servers (e.g. 8.8.8.8 or 1.1.1.1), or utilize a VPN service to ensure all traffic is properly encrypted.


### HTTPS Flow
![[Pasted image 20260508154921.png]]
- if we type `http://` instead of `https://` to visit a website that enforces HTTPS
- the browser attempts to resolve the domain and redirects the user to the webserver hosting the target website
- a request is sent to port `80` first which is the unencrypted HTTP protocol 
- the server detects and redirects the client to secure HTTP ports `433` instead
- this is done via `301 Moved Permanently`

>[!Note] 
>301 Moved permanently shows that the resource has been moved to a  new URL permanently
> it is a HTTP status code

- the client ( web browser ) sends a `client hello` packet giving information about itself 
- then server replies with `server hello` 
- followed by a key exchange to exchange SSL certificate
- the client verified the key/certificate and send one of its own
- then an encrypted handshake is initiated to confirm whether the encryption and transfer are working correctly
- after the handshake is completed normal HTTP communication is continued which is encrypted after that

>[!Note]
>Depending on the circumstances, an attacker may be able to perform an HTTP downgrade attack, which downgrades HTTPS communication to HTTP, making the data transferred in clear-text. This is done by setting up a Man-In-The-Middle (MITM) proxy to transfer all traffic through the attacker's host without the user's knowledge. However, most modern browsers, servers, and web applications protect against this attack.

### cURL for HTTPS
- cURL should automatically handle all the HTTPS communication standard and perform a secure handshake and then encrypt and decrypt data automatically 
- if we ever contact a website with invalid SSL certificate or an outdated one, then cURL by default would not proceed with the communication to protect against the MITM attack
![[Pasted image 20260508202309.png]]
- modern web browser would warn the user against visiting a website with invalid SSL certificate
- we may face those issue while testing a local web application or a web application hosted for practice purpose
- as such web application may not yet have implemented a valid SSL certificate
- to skip such certificate check we can use `-k` flag 
![[Pasted image 20260508202559.png]]

