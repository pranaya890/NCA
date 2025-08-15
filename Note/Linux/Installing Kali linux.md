we are learning to install kali linux in our hypervisor i.e the virtual machine
## Hypervisor
Hypervisor is the software that allows us to create and manage vritual machine
it is bridge between physical hardware and virtual environment
it allows us to manage multiple  operating system in single system

### Type 1: Bare Metal Hypervisor
it runs directly on physical hardware without requiring an underlying OS
it provides better performance, efficiency and security
commonly used in enterprise environment, data centers and  cloud computing
Ex: Vmware ESXi - for enterprise virtualisation
Microsoft hyper V - solution for windows server
Xen- for cloud platforms like AWS

### Type 2: Hosted Hypervisor
runs on top of exisisting operating system
relies on host os for hardware resources
easier to install but has slightly lower performance
used for personal testing and development purpose
Eg: Virtual Box
VM ware workstation
Parallel Desktop
