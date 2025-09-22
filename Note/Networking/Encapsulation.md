- data is passed down in each layer of model
- each layer adds information containing detail specific to layer 
- it is process of wrapping data with necessary protocol information as it moves down the layer
- application layer creates the actual message
- transport layer adds a transport header information like TCP/UDP header with port number
- network header adds network header 
- in data link layer the ethernet or WiFi  receives  the IP packet and adds  the proper  header and trailer creating a frame
- At recieving end the reverse process happens called de-encapsulation
- it provides a layer of security as data cant be intercepted and tampered
- can also be used to verify whether the data is corrupted during transmission 
![[Pasted image 20250916212647.png]]
in above diagram  the encapsulated data gets different names in different steps of process
- in layer 7,6 and 5  the data is simply referred as data 
- in transport layer  the encapsulated data is called data segments or datagrams on the basis of TCP or UDP is used 
- in network layer data is referred as packets
- in data link layer it becomes frames
- in stage 7 the data is converted to bits
while reciever recieves the information it reverses the process
