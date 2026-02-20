# Subnetting_dual-network_in_ciscopackettracer
A classic inter-subnet routing setup with two local networks connected via a 2911 router.

Config (IOS) Command Line Interface
Router>enable
Router#conf t
Enter configuration commands, one per line. End with CNTL/Z.
Router (config) #hostname R1
R1(config)#enable password pass@123
R1(config)#username nit password pass@123
R1(config)#exit
R1#enable
R1#exit

R1>enable
Password: ****
R1#config t
R1(config) #int g0/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0 
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#exit
R1#write

R1>enable
Password: ****
R1#config t
R1(config) #int g0/1
R1(config-if)#ip address 192.168.2.1 255.255.255.0 
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#exit
R1#write

PC0 configuration - ip address: 192.168.1.2 , subnet mask: 255.255.255.0 , Default Gateway: 192.168.1.1
ping 192.168.1.11 

PC1 configuration - ip address: 192.168.1.11 , subnet mask: 255.255.255.0 , Default Gateway: 192.168.1.1
ping 192.168.1.2

PC2 configuration - ip address: 192.168.2.7 , subnet mask: 255.255.255.0 , Default Gateway: 192.168.2.1
ping 192.168.2.3

PC3 configuration - ip address: 192.168.2.3 , subnet mask: 255.255.255.0 , Default Gateway: 192.168.2.1
ping 192.168.2.7

VERIFICATIONS:
1.  In router IOS -CLI
R1>en
R1#show ip route

2.  Turn on simulation mode

3. Check the connectivity through VPCs --> pinging network-1 to network-2

