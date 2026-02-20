- web security vulnerability that allows an attacker to interfere with an application processing of XML data
- it often allows an attacker to view files on the application filesystem, and to interact with any backend or external system  that the application itself can access
- sometimes it can also be used to  compromise the underlying server or other back-end infrastructure, by leveraging the XXE vulnerability to perform server-side request forgery (SSRF) attacks.

## How does it arise?
- applications use XML format to transmit data between browser and the server
- Applications that do this virtually always use a standard library or platform API to process the XML data on the server
- XXE vulnerabilities arise because the XML specification contains various potentially dangerous features, and standard parsers support these features even if they are not normally used by the application
- XML external entities are a type of custom XML entity whose defined values are loaded from outside of the DTD in which they are declared
- External entities are particularly interesting from a security perspective because they allow an entity to be defined based on the contents of a file path or UR
### Types of XXE attacks
- to retrive files: where an external entity is defined containing the contents of a file, and returned in the application's response
- to perform SSRF( server side request forgery): where an external entity is defined based on a URL to a back-end system
- to exfiltrate(withdraw) data out of band: where sensitive data is transmitted from the application server to a system that the attacker controls
- to retrieve data via error message: where an attacker can trigger a parsing error message containing sensitive data
- 