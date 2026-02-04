- act of exploiting bug , a design or flaw or a configuration oversight in an operating system or software application to gain elevated access to the resources that are normally protected from an application or user
- the result is the user is more privilege than intended by application developer or system administrator can perform unauthorized actions
- ![[Pasted image 20260204182338.png]]

>[!note] privilege is the specific ability of particular user to use the computer system

- privilege escalation means user receive privilege that they are not entitled to 
- these can be used to delete file, view private information , or install unwanted programs such as viruses
- It usually occurs when a system has a bug that allows security to be bypassed or, alternatively, has flawed design assumptions about how it will be used
- occurs in two forms: vertical privilege escalation and horizontal privilege escalation
### Vertical Privilege Escalation
- also known as privilege escalation  where a lower privilege user or application accesses function or content reserved for higher privilege user or application 
- , possibly by performing kernel level operations.
- e.g. Internet Banking users can access site administrative functions or the password for a smartphone can be bypassed

### Horizontal Privilege Escalation
- where normal user access function or content reserved for other normal user 
- e.g. Internet Banking User A accesses the Internet bank account of User B)
- occurs when an application allows the attacker to gain access to resources which normally would have been protected from an application or user
- result is that the application performs actions with the same user but different security context than intended by the application developer or system admin
- this is effectively a limited form of privilege escalation
- specifically, the unauthorized assumption of the capability of impersonating other users
- Compared to the vertical privilege escalation, horizontal requires no upgrading the privilege of accounts. It often relies on the bugs in the system