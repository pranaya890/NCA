- is web-security vulnerability that allows the attacker to interfere with that queries that an application makes to its database
- allows attacker to view the data that are normally unavailable to retrive
- includes data that belong to other user or any restricted/private data
- an attacker can edit or modify data, causing persistent changes to application content or behavior
- can be used sometimes to compromise the underlying services or backend infrastructure
- can be used to perform Denial of Service (DoS) attack

### Impact of Successful SQL injection attack
- can result in unauthorized access to sensitive data: passwords, credit card details and personal user information
- used for many high profile data breaches over the years
- causes reputation damage and regulatory fines
- some cases: attacker can find a persistence backdoor into organization system, leading to a long term compromise that can go unnoticed for extended period

### Detecting SQL injection vulnerabilities
- can be detected manually using systematic test against every entry point in application
- we can typically submit:
	- the single quote character `'`  and look for error anomalies
	- Some SQL-specific syntax that evaluates to the base (original) value of the entry point, and to a different value, and look for systematic differences in the application responses.
	- boolean conditions such as `OR 1=1` and `OR 1=2` and look for difference in the application response
	- payloads designed to trigger time delays  when executed within a SQL query and look for difference in time taken to respond
	- OAST (Out-of-band Application Security Testing) payloads designed to trigger an out-of-band network interaction when executed within a SQL query, and monitor any resulting interactions.

### SQL injection in different part of the query
most of SQLi vulnerability occurs within `WHERE` clause of `SELECT` query
most experienced tester are familiar with this type of SQL injection
However, SQL injection vulnerabilities can occur at any location within the query, and within different query types
Some of them are:
- In `UPDATE` statements, within the updated values or the `WHERE` clause.
- In `INSERT` statements, within the inserted values.
- In `SELECT` statements, within the table or column name.
- In `SELECT` statements, within the `ORDER BY` clause.

### SQL injection Examples 
### Retriving hidden data 
#### Subverting application logic

