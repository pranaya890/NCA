- language designed for storing and transporting data
- HTML and XML uses a tree like structure of tags and data
- Unlike HTML, XML doesnot uses predefined tags and so tags can be given names that describe the data

### What are XML entities?
- XML entities are a way of representing an item of data within an XML document, instead of using the data itself
- Various entities are built in to the specification of the XML language
- For example, the entities `&lt;` and `&gt;` represent the characters `<` and `>`. 
- These are metacharacters used to denote XML tags, and so must generally be represented using their entities when they appear within data.
## What is document type definition?

- The XML document type definition (DTD) contains declarations that can define the structure of an XML document, the types of data values it can contain, and other items. 
- The DTD is declared within the optional `DOCTYPE` element at the start of the XML document. 
- The DTD can be fully self-contained within the document itself (known as an "internal DTD") or can be loaded from elsewhere (known as an "external DTD") or can be hybrid of the two.
##  What are XML custom entities?

- XML allows custom entities to be defined within the DTD. For example:

`<!DOCTYPE foo [ <!ENTITY myentity "my entity value" > ]>`

- This definition means that any usage of the entity reference `&myentity;` within the XML document will be replaced with the defined value: "`my entity value`"

## What are XML external entities?

- XML external entities are a type of custom entity whose definition is located outside of the DTD where they are declared.
- The declaration of an external entity uses the `SYSTEM` keyword and must specify a URL from which the value of the entity should be loaded. For example:

`<!DOCTYPE foo [ <!ENTITY ext SYSTEM "http://normal-website.com" > ]>`

- The URL can use the `file://` protocol, and so external entities can be loaded from file. For example:

`<!DOCTYPE foo [ <!ENTITY ext SYSTEM "file:///path/to/file" > ]>`

## Exploiting XXE to retrieve files

To perform an XXE injection attack that retrieves an arbitrary file from the server's filesystem, you need to modify the submitted XML in two ways:
- Introduce (or edit) a `DOCTYPE` element that defines an external entity containing the path to the file.
- Edit a data value in the XML that is returned in the application's response, to make use of the defined external entity.
### Exploiting XXE to perform SSRF attack
- other main impact of XXE attacks is that they can be used to perform server-side request forgery (SSRF). 
- This is a potentially serious vulnerability in which the server-side application can be induced to make HTTP requests to any URL that the server can access.
- To exploit an XXE vulnerability to perform an SSRF attack, you need to define an external XML entity using the URL that you want to target, and use the defined entity within a data value
-  If you can use the defined entity within a data value that is returned in the application's response, then you will be able to view the response from the URL within the application's response, and so gain two-way interaction with the back-end system.
- If not, then you will only be able to perform blind SSRF attacks (which can still have critical consequences).
  ``` XML
 <!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://internal.vulnerable-website.com/"> ]>
  ```
