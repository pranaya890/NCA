in cisco packet tracker inside ip address DHCP is dynamic ip addressing
### switch:
- networking device used to connect multiple devices within LAN
- generally operates in data link layer of OSI model
- reduces network collision and improves performances
- supports VLANs and sometime operate on  Layer 3 for routing function
#### Modes of switch:
- User EXEC mode( switch>): initial mode,  used for basic commands like `ping` or `show` no configuration changes can be made
- Privileged EXEC Mode (switch#): excess to more powerful commands like `show running-config` or `copy`. we can enter configure mode from here
- Global Configuration Mode (switch(config#)): used to configure system-wide settings like hostname, interfaces or VLANs, commands entered here determines switch  behaviour and services

#### Switch in CISCO
- when the switch in cisco is clicked it opens a configuration tab
- `CLI` in configuration tab allows us to configure the switch
- it opens in user mode by default 
- we can run basic commands 
- we can use `?` to see the commands that can be ran in the user mode
- we can also use shortcut of commands like `sh` for `show` and `int` for `interface`
- `Tab` key can also be used for completion
### Changing Mode
- we can use `en` command to change mode to enable mode which is privileged mode
- we can change to global configuration mode using `config t` 
- limitation of switch: it works on LAN only and it does not perform routing
- to work on layer 3 either we have to use multi-layer switch or router
 Note: Router and switch have same modes
### Setting up gateway on Routers
- change the mode to enable mode using `en` then go to configuration mode using `config t`
- `Gig0/0/0` is giga port and `Fa0/1` these are fast ethernet port #reseach_topics
- then change to giga port interface using `interface gig 0/0/0` or `int gig 0/0/0`
- this will change the mode to (config -if)#
- then we will input the ip address of gateway using `ip add 192.168.1.1 255.255.255.0` i.e. in general `ip add ip_address_of_gateway subnet_mask`
- then we turn on the port using `no shut` command
- then we do it for the different gateways
- then we ping another pc but at first the output is request time out or failed
- it is because it is the first time sending data packets the data will reach the switch but not the device
- the switch uses ARP so it has to maintain MAC address table
- the first packet is then lost then other are sent 