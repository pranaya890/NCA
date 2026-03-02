- they are bidirectional, full duplex communication protocol initiated over HTTP
- commonly used in modern web application for streaming data and other asyncronous traffic
- Virtually any web security vulnerability that arises with regular HTTP can also arise in relation to WebSockets communications

![[Pasted image 20260225103027.png]]


### Difference  between HTTP and WebSocket

![[Pasted image 20260225100932.png]]

### How connection are established?
- connected using client-side JavaScript.
``` Javascript
  var ws = new WebSocket("wss://normal-website.com/chat");
```

>[!note] The `wss` protocol establishes a WebSocket over an encrypted TLS connection, while the `ws` protocol uses an unencrypted connection.

- To establish the connection, the browser and server perform a WebSocket handshake over HTTP
- The browser issues a WebSocket handshake request like the following:
``` HTTP
GET /chat HTTP/1.1 
Host: normal-website.com 
Sec-WebSocket-Version: 13 
Sec-WebSocket-Key: wDqumtseNBJdhkihL6PW7w== 
Connection: keep-alive, Upgrade 
Cookie: session=KOsEJNuflw4Rd9BDNrVmvwBF9rEijeE2 
Upgrade: websocket
```

- then server accepts request by
``` HTML
HTTP/1.1 101 Switching Protocols
Connection: Upgrade
Upgrade: websocket 
Sec-WebSocket-Accept: 0FFP+2nmNIf/h+4BP36k9uzrYGk=
```
- now at this point, the network connection remains open and can be used to send WebSocket message in either direction
>[!note] Several features of the WebSocket handshake messages are worth noting:
> - The `Connection` and `Upgrade` headers in the request and response indicate that this is a WebSocket handshake.
> - The `Sec-WebSocket-Version` request header specifies the WebSocket protocol version that the client wishes to use. This is typically `13`.
> -  The `Sec-WebSocket-Key` request header contains a Base64-encoded random value, which should be randomly generated in each handshake request. 
> - The `Sec-WebSocket-Accept` response header contains a hash of the value submitted in the `Sec-WebSocket-Key` request header, concatenated with a specific string defined in the protocol specification. This is done to prevent misleading responses resulting from misconfigured servers or caching proxies.

### What do WebSocket message look like?
- after establishing connection, message can be send asyncronously in either direction by the client or server
- simple message can be sent from browser using client side JavaScript :
		`ws.send(" Hello World")`
- web socket can contain any content or data format 
- in modern application, it is common for JSON to be used to send structured data within WebSocket message 

### Manipulating WebSocket traffic
- finding of this vulnerability involves manipulating them in they ways that the application does not expect
- we can intercept and modify the websocket message using intercept edit the request
- As well as intercepting and modifying WebSocket messages on the fly, you can replay individual messages and generate new messages
-  it is sometimes necessary to manipulate the WebSocket handshake that establishes the connection.
- There are various situations in which manipulating the WebSocket handshake might be necessary:
		-  It can enable you to reach more attack surface.
		- Some attacks might cause your connection to drop so you need to establish a new one.
		- Tokens or other data in the original handshake request might be stale and need updating.

### WebSocket security vulnerability
- User-supplied input transmitted to the server might be processed in unsafe ways, leading to vulnerabilities such as SQL injection or XML external entity injection.
- Some blind vulnerabilities reached via WebSockets might only be detectable using out-of-band (OAST) techniques.
- If attacker-controlled data is transmitted via WebSockets to other application users, then it might lead to XSS or other client-side vulnerabilities.


###  Manipulating WebSocket messages to exploit vulnerabilities
 - the majority of input-based bulnerability affecting web socket can be found and exploited by tampering the content of web socket message
 Example:
 Sent web socket message: `{"message": "hello Carlos"}`
 rendered message: `<td>hello Carlos</td>`
 in this situation attacker can perform a proof of concept XSS attack by submitting the following web Socket
 `{"message":"<img src=1 onerror='alert(1)'>"}`
 generates error message

###  Manipulating the WebSocket handshake to exploit vulnerabilities
- some web sockets  can only be found and exploited by manipulating the web socket handshake
- these vulnerability tend to involve design flaws
	- Misplaced trust in HTTP headers to perform security decisions, such as the `X-Forwarded-For` header
	-  Flaws in session handling mechanisms, since the session context in which WebSocket messages are processed is generally determined by the session context of the handshake message.
	- Attack surface introduced by custom HTTP headers used by the application

