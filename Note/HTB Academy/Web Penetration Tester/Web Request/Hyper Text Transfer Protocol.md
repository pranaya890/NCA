- majority of application in this time constantly interact with internet both web and mobile application
- most internet communication are made with web request through HTTP protocol
- HTTP is application level protocol  used to access World Wide Web resources
- the term `hypertext` stands for text containing links to other resources and text that reader can easily interpret
- application level protocol for distributed, collaborative, hypermedia(non-linear medium of information that includes graphics, audio, video, plain text and hyperlinks) information system
- it is generic, stateless protocol which can be used for many task beyond its use for hypertext such as name server and distributed object management system, through extension of its request method, error codes and headers
- a feature of HTTP is the typing and negotiation of data representation  allowing system to be built independently of data being transferred
Reference: https://datatracker.ietf.org/doc/html/rfc2616

- HTTP communication consist of a client and a server, where the client request the server for its resources
- server processes the request and returns the requested resources
- default port for HTTP communication is `80`
- but it can be changed to any other port depending on web server configuration
- same request are utilized when we use internet to visit different websites
- we enter `Fully Qualified Domain Name (FQDN)` as a `Uniform Resource Locator(URL)` to reach desired website

### Uniform Resource Locator (URL)
- resources over HTTP are accessed via URL
- which offers many more specifications than simply specifying a website we visit
![[Pasted image 20260508115640.png]]

| **Component**  | **Example**          | **Description**                                                                                                                                                                       |
| -------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Scheme`       | `http://` `https://` | This is used to identify the protocol being accessed by the client, and ends with a colon and a double slash (`://`)                                                                  |
| `User Info`    | `admin:password@`    | This is an optional component that contains the credentials (separated by a colon `:`) used to authenticate to the host, and is separated from the host with an at sign (`@`)         |
| `Host`         | `inlanefreight.com`  | The host signifies the resource location. This can be a hostname or an IP address                                                                                                     |
| `Port`         | `:80`                | The `Port` is separated from the `Host` by a colon (`:`). If no port is specified, `http` schemes default to port `80` and `https` default to port `443`                              |
| `Path`         | `/dashboard.php`     | This points to the resource being accessed, which can be a file or a folder. If there is no path specified, the server returns the default index (e.g. `index.html`).                 |
| `Query String` | `?login=true`        | The query string starts with a question mark (`?`), and consists of a parameter (e.g. `login`) and a value (e.g. `true`). Multiple parameters can be separated by an ampersand (`&`). |
| `Fragments`    | `#status`            | Fragments are processed by the browsers on the client-side to locate sections within the primary resource (e.g. a header or section on the page).                                     |
- all components are not required to access a resource 
- mandatory are scheme and host

### HTTP Flow
![[Pasted image 20260508115959.png]]
- when user enters the URL into the browser it sends a request to DNS system to resolve the domain to get IP
- the DNS server looks up the IP for the  domain name in URL 
- all domain name need to resolve this way as server cannot communicate without IP address.
>[!note] 
> Our browsers usually first look up records in the local '`/etc/hosts`' file, and if the requested domain does not exist within it, then they would contact other DNS servers. We can use the '`/etc/hosts`' to manually add records to for DNS resolution, by adding the IP followed by the domain name.
- after the ip address linked to domain name is obtained it sends get request to default HTTP port asking for the `/` root path
- then web server receives the request and processes it 
- by default server is configured to return a index file when a request `/` is received
- the content of `index.html`  are read and returned by the web server as an HTTP response
- the response also contains a status code (eg 200 OK) which indicates that the request was successfully processed
- then the content of `index.html` is rendered and presented to user by browser

### client URL (cURL)
- we can send web request through two of the most important tools for any penetration tester a web browser like chrome, firefox and the `cURL` command line tool
- `cURL` is a command-line tool  and library that primarily supports  HTTP along with many other protocol
- this makes it good candidate for script as well as automation, making it essential for sending various type of web request from command line , which is necessary for many types of web penetration testing
- we can send basic HTTP request by
![[Pasted image 20260508130440.png]]

- we can see `cURL` does not render the HTML/JavaScript/CSS code unlike a web browser but prints it in raw format
- as a penetration tester we are mainly interested in the request and response context
- which usually becomes much faster and convenient  than a web browser
- we can also use cURL to download a page or a file and output the content into a file using `-O` flag
- if we want to specify the output file name, we can use `-o` flag  and specify the name
- `-O` flag will use the remote file name
![[Pasted image 20260508131225.png]]
![[Pasted image 20260508131241.png]]

- in above case output was not printed it was saved to `index.html`
- but it still printed some status while processing the request  which can be silenced using `-s` flag 
 ![[Pasted image 20260508131452.png]]
- in this case the status was made silent and output was saved in `index.html`
- we can use `-h` flag to see the other options
- we can also use `--help all` to print more detailed help menu or `--help category`
- ![[Pasted image 20260508131717.png]]
- we can also use manual page `man curl`
