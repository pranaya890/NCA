- whenever we visit any URL our browser sends a GET request to obtain the remote resources hosted at that URL
- after receiving initial page  its requesting browser can send other request using various HTTP methods
- this can be viewed  through Network tab

### HTTP Basic Auth
- unlike login forms, which utilize user parameter to validate user credential (e.g. POST request) this type of authentication utilize a `basic HTTP Authentication`
- which is handled by directly by webserver to protect the specific page or directory without directly interacting with web application
- to access a page like that we have to enter our credentials


![[Pasted image 20260512204301.png]]


after adding the credentials we can get the page
![[Pasted image 20260512204345.png]]

now we try to access it using `curl -i`
![[Pasted image 20260512204536.png]]

- in response we can see `WWW-Authenticate: Basic realm="Access denied"` which confirms the page uses basic HTTP auth 
- now we add the credentials for the authorization for that we can use `-u` flag
![[Pasted image 20260512204924.png]]

- we can provide basic HTTP auth credentials directly through URL
![[Pasted image 20260512205201.png]]

![[Pasted image 20260512205242.png]]


### HTTP Authorization Header

![[Pasted image 20260512205555.png]]

- here we are using basic HTTP auth, we can see that our HTTP request sets the Authorization header to  Basic YWRtaW46YWRtaW4= which is base64 encoded value of admin:admin
![[Pasted image 20260512205817.png]]

- if we used modern methods of authentication (e.g. JWT) the authorization would be of type `Bearer` with longer encrypted token
- TRY: we can manually try to set the `Authorization ` without supplying the credentials to see if allows to access the page
![[Pasted image 20260512210207.png]]
- Conclusion : it can be accessed by manually setting the authorization header

>[! Note] 
>most of the modern web application use login form built with backend scripting language (e.g. PHP) which utilize the HTTP POST request to authenticate the user and return the cookie to maintain their authentication
>


### GET Parameter
- once we get to `City Search` function, we can enter search the term and get a list of matching cities
![[Pasted image 20260512210729.png]]

- Analysis: it may be contacting a remote resource to obtain the information and display them on page
- Verification: using network tab in devtool we can enter search term and see the request
- we can use `trash` icon on top left corner to ensure we clear any previous request and only monitor newer request
![[Pasted image 20260512211115.png]]
- Finding: the app is sending a GET request to `search.php` to get a full search result, though it will probably return them in specific format (e.g JSON) without having HTML layout 

 - we can send `curl` request to exact same URL , 
 - GET request place their parameter in the URL
 >[!NOTE] 
 >browser devtool provide more convinient way of getting `curl` command 
 >right-click on request select copy >copy as cURL
 > then we can paste the command in the terminal to execute it
 
![[Pasted image 20260512214128.png]]

>[!Note]
>The copied command will contain all headers used in the HTTP request. However, we can remove most of them and only keep necessary authentication headers, like the `Authorization` header.

- we can repeat the exact request right within browser devtool  by selecting `copy>copy as fetch`
- this will copy the exact same HTTP request using the javascript fetch library
- then we can go to javascript console tab (Shortcut: `CTRL+SHIFT+K`), paste out fetch command and hit enter to send the request

![[Pasted image 20260512214307.png]]


![[Pasted image 20260512214344.png]]


-  the browser sent our request, and we can see the response returned after it
- We can click on the response to view its details, expand various details, and read them.

### Solutioon

![[Pasted image 20260512214539.png]]