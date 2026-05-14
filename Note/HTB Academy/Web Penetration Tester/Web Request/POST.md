- whenever web applications need to transfer files or move the user parameter from the URL, they utilize `POST` request
- Unlike `HTTP` GET, which use parameters within the URL, HTTP `POST` places user parameter within the HTTP Request body
- Main benefits :
	- Lack of Logging: 
		- it may transfer large files (e.g. file upload), it would not be efficient for the server to log all uploaded files as a part of the requested URL, as would be the case with a file uploaded through a GET request
	- Less Encoding Requirement: 
		- URLs are designed to be shared, which means they need to correspond to the character that can be converted to letters
		- POST request can places data in the body which can accept binary data
		- the only characters that need to be encoded are those that are used to separate parameter
	- More data can be sent: 
		- maximum URL length varies between browser (Chrome/Firefox/IE), web server (IIS, Apache, Nginx), Content Delivery Network (Fastly, Cloudfront, Cloudflare) and even URL Shortners (bit.ly,amzn.to)
		- generally URL length should be kept to below 2000 characters and so they cannot handle a lot of data

### Login Form

-after logging into the login page we get a POST request which can be viewed from the request tab
![[Pasted image 20260513212134.png]]

- now we try to craft same request using `curl`
- we can use `-d` flag 
![[Pasted image 20260513212512.png]]

- if we send the request we do not see the login form instead we see the search bar after login which indicates we are authenticated
>[!Tip]
>Many login forms would redirect us to a different page once authenticated (e.g. /dashboard.php). If we want to follow the redirection with cURL, we can use the `-L` flag.



### Authenticated Cookies
- after we are succesfully authenticated, we have received a cookie so our browsers can persist our authentication and we dont need to login everytime we visit the page
- we can use `-V` or `-i` flags to  view the response
- in response we can see `Set-Cookie` header with our authenticated cookie
- ![[Pasted image 20260513212931.png]]

- with the authenticated cookie, we should now be able to interact with the application without needing to provide our credentials every time
- we can set the cookie with  the `-b` flag in curl
![[Pasted image 20260513213503.png]]

- we can see we are authenticated
- we can specify the cookie as a header
![[Pasted image 20260513213705.png]]

---
##### In Browser
![[Pasted image 20260513214417.png]]

 - we can add new cookie from `+` button and input the previous authenticated cookie 
- we have to name the cookie which is part before `=` ,  i.e. PHPSESSID then we have to put the value
- then we can refresh the page to login
- having valid cookie may be enough to get authenticated into many web applications
- this is very essential part of some web attacks like cross site scripting 

### JSON Data

![[Pasted image 20260514202035.png]]
- while searching we can observe the request sent using Network tab
- we can observe a POST request is sent to search.php with JSON data `search:"Lee"`
- we can analyse that the post request should have specified `Content-Type:application/json`
- we can verify it by `copy>copy request header`

``` 
POST /search.php HTTP/1.1
Host: 154.57.164.69:31433
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: */*
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://154.57.164.69:31433/index.php
Content-Type: application/json 
Content-Length: 16
Origin: http://154.57.164.69:31433
DNT: 1
Connection: keep-alive
Cookie: PHPSESSID=kslp3jis1qjis9sj88jd3cc5mh
Sec-GPC: 1
Priority: u=0
```

- now we try to replicate this using curl
- `curl -X POST -d '{"search":"Lee"}' -b 'PHPSESSID=kslp3jis1qjis9sj88jd3cc5mh' -H 'Content-Type:application/json' http://154.57.164.69:31433/search.php`
![[Pasted image 20260514202712.png]]

- we can see that we can interact with search function directly without login or front-end interaction
- this is essential skill while performing web application assesments or bug bounty excercise
- because it is faster to test application
Excercise:
performing same request without `Content-Type` or `Cookie`
![[Pasted image 20260514202958.png]]

- observation: without specifying content type the supplied content type is unrecognized and without authentication cookie the search.php is not accessible


### Using `fetch`
- steps `copy>copy as fetch`
- paste in console and execute

![[Pasted image 20260514203743.png]]

- then we can see the provided request from network tab
![[Pasted image 20260514203730.png]]


### Exercise
 to search the flag in search.php with valid token
 `curl -X POST -d '{"search":"flag"}' -b 'PHPSESSID=kslp3jis1qjis9sj88jd3cc5mh' -H 'Content-Type:application/json' http://154.57.164.69:31433/search.php`

![[Pasted image 20260514203944.png]]
