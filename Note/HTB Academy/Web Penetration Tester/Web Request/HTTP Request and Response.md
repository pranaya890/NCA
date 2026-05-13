- HTTP communication consist of HTTP request and HTTP response
- HTTP request is made by client (e.g. cURL/Browser) and is processed by server
- request contains all the details we require from the server, including the resources(e.g URL, path, parameters), any request data, headers or option we specify and many other options
- after receiving the HTTP  request, server processes it and responds by sending the HTTP response which contains the response code 
- it may contain the resource data if the requester has access to it

### HTTP request

![[Pasted image 20260508203623.png]]
- this shows a HTTP GET request sent to `https://inlanefreight.com/users/login.html`
- the first line of HTTP request shows

|**Field**|**Example**|**Description**|
|---|---|---|
|`Method`|`GET`|The HTTP method or verb, which specifies the type of action to perform.|
|`Path`|`/users/login.html`|The path to the resource being accessed. This field can also be suffixed with a query string (e.g. `?username=user`).|
|`Version`|`HTTP/1.1`|The third and final field is used to denote the HTTP version.|
-  the next set of lines contains HTTP header value pairs like `Host`, `User-Agent`,`Cookie` and other possible headers
- these headers specifies various attributes of a request 
- the header are terminated with a new line, which is necessary for a server to validate the request 
- finally a request may end with the request body and data 
>[!Note]
> HTTP version 1.X sends requests as clear-text, and uses a new-line character to separate different fields and different requests. HTTP version 2.X, on the other hand, sends requests as binary data in a dictionary form.

### HTTP Response

![[Pasted image 20260508204609.png]]

-  first line of HTTP response contains two fields seperated by space 
- first is `HTTP version` and the second is `HTTP Response code`
- response code are used to determine the request status
- the next lines, the response lists its header, similar to HTTP request
- the response may end with response body which is separated by new line after the header
- the response body is usually defined and `HTML` code
- it can also respond with other code type such as `JSON`, website resources such as images, style sheets or scripts, or even a document as a PDF document hosted on the webserver

### cURL
- cURL also allows us to preview the full HTTP request and the full HTTP response which can become very handy when performing web penetration testing or writing exploits 
- to view full HTTP request and response we simply add `-v` i.e. verbose flag
![[Pasted image 20260508210746.png]]

- the request simply sent `GET / HTTP 1.1` along with the host,  user-agent and accept header
- the `-vv` flag gives more detailed output
![[Pasted image 20260508211314.png]]



### Browser DevTools
- modern browser comes with built-in developers tools (DevTools) which are mainly intended for developers to test their web applications
- for penetration tester these tools can be vital  asset in any web assesment we perform 
- As a browser (and its DevTools) are among the assets we are most likely to have in web assesment
- whenever  we visit any website or access any web application, our browser sends multiple web request and handles multiple HTTP response to render final view we see in browser window
- we can open browser dev tool by using `CTRL+SHIFT+I` or simply click `F12` 
- the devtools contains multiple tabs, `Network` tab is responsible for web request
- if we click the Network tab and refresh the page, we should be able to see the list of request sent by the page
![[Pasted image 20260508212703.png]]

- the dev tool showed us at a glance the response code status, the request resources(URL/domain) along with requested path
- we can use `filter URLs` to search for specific request, in case the websites loads too many to go through
- 