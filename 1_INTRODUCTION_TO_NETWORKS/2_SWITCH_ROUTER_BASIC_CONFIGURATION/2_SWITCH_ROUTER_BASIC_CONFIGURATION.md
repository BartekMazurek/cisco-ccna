## SWITCH & ROUTER BASIC CONFIGURATION

***

#### 1) SET IPv4 ON PC0 192.168.1.3 AND IPv6 2001:db8:acad:1::3/64

#### 2) SET IPv4 ON PC1 192.168.0.2 AND IPv6 2001:db8:acad::3/64

#### ROUTER CONFIGURATION:

#### 3) SET ROUTER NAME

- configure terminal
- hostname router0

#### 4) TURN OFF DNS LOOKUP

- no ip domain-lookup

#### 5) SET EXEC PASSWORD

- enable secret <password>

#### 6) SET CONSOLE PASSWORD

- line console 0
- password <password>
- login
- exit

##### 7) SET VTY PASSWORD & TURN ON SSH LOGIN

- line vty 0 4
- password <password>
- login
- transport input ssh

#### 8) ENCRYPT STORED PASSWORDS

- service password-encryption

#### 9) SETUP IP ON ROUTER INTERFACES

- configure terminal
- interface gig0/0/0
- description Route to LAN 1
- ip address 192.168.1.1 255.255.255.0
- ipv6 address 2001:db8:acad:1::1/64
- no shutdown

- interface gig0/0/1
- description Route to LAN 2
- ip address 192.168.0.1 255.255.255.0
- ipv6 address 2001:db8:acad::1/64
- no shutdown
- exit

#### 10) TURN ON IPV6 ROUTING

- configure terminal
- ipv6 unicast-routing

#### 11) SET RUNNING CONFIG AS STARTUP CONFIG

- copy running-config startup-config

#### 12) VERIFY INTERFACES CONFIGURATION

- show ip interface brief 
- show ipv6 interface brief


#### SWITCH CONFIGURATION

#### 13) SET SWITCH NAME

- configure terminal
- hostname <name>

#### 14) TURN OFF DNS LOOKUP

- no ip domain-lookup

#### 15) CONFIGURE & ACTIVATE VLAN 1 INTERFACE

- interface vlan 1
- ip address 192.168.1.2 255.255.255.0

#### 16) SETUP DEFAULT GATEWAY

- ip default-gateway 192.168.1.1
