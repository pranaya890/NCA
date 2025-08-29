For subnet:
Formula: $2^{subnet bits}$ 

for valid host:
$2^{no of host bits}$ -2
`-2` is for reducing network address and broadcast address from total valid host

Example:
Subnet:192.168.1.0 with subnet mask of 255.255.255.240 (/28) or we can write it as:
*11111111.11111111.11111111.1111* 0000 #italics are network bits and non italics are host bits for notation only  host bits  is used to make host ip address

Q. Subnet 192.168.1.0/28 and find the number of possible subnets and valid hosy
Solution
Note: to find subnet mask of `/28` search in google
subnet of /28 is 255.255.255.240

for subnet: $2^{4}$ =16 i.e.no of subnet bits which is network bits
Alternatively, $2^{32-28}=16$ possible subnets

for valid hosts:
$2^{4}$  -2= 14 possible usable host


Q. subnet 150.150.0.0 /30 and find the number of subnets and valid hosts
subnet mask of /30 = 255.255.255.252
which is class B ip address and its default subnet mask is 255.255.0.0
now the subnet m,ask of /30 in binary is `11111111.11111111.11111111.11111100`
now counting the subnet bits counting the bits from last 16 bits
subnet bits=14
host bits =2

subnets= $2^{14}$ =16384 possible subnet
host= $2^2$-2=2 possible subnet host per subnet 
