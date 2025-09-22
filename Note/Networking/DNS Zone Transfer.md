- A DNS zone is a portion of the Domain Name System (DNS) namespace that’s managed as a single administrative unit.
![[Pasted image 20250922101424.png]]
- A DNS zone transfer is a process used to replicate DNS database information from a primary DNS server to one or more secondary DNS servers,
- it ensures  that all servers have consistent and up-to-date records for a specific domain zone
- This replication is crucial for maintaining redundancy and reliability in DNS services
- The transfer is initiated by the secondary server and uses the Transmission Control Protocol (TCP) for transport, which is preferred over UDP due to the risk of packet loss or spoofing
- follows client server architecture
- The client requesting a zone transfer may be a secondary server requesting data from a primary server

Full Zone Transfer( AXFR): copies the entire DNS zone file from the primary server to the secondary server

Incremental Zone Transfer (IXFR): it only transfers the changes (additions, deletions, or modifications) to the zone data since the last update, based on the serial number in the Start of Authority (SOA) record