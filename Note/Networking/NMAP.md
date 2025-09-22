- while performing security audits the first and foremost thing is mapping the given system 
- i.e we have to know what things are running in target
Domain Controller is the server computer that respond to security authentication request within windows domain
- first stage is establishing the map of the landscape called port scanning 
- when computer runs a network service the computer opens a path called port to receive connection


- `nmap` will connect to each port of target in turn
- depending on the response of port the port can be considered open closed or filtered( usually by firewall)
- by using `nmap` we can enumerate which services are running on each port manually or by using `nmap`
- can be accessed in terminal by using keyword `nmap` followed by some of switches or command argument 
- help menu for `nmap` is `nmap -h` or `man nmap`