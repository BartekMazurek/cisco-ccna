## SWITCH BASIC CONFIGURATION

***

#### 1) SET IP ON PC0

- 192.168.1.10/24
- 2001:db8:acad::3/64
- fe80::3

#### 2) SET OPTION TO ASSIGN IPv4 & IPv6 INTO SVI (SWITCH VIRTUAL INTERFACE) ON S1

- show sdm prefer
- configure terminal
- sdm prefer dual-ipv4-and-ipv6 default
- end
- reload

#### 3) TURN OFF DNS LOOKUP ON SWITCH

- enable
- configure terminal
- no ip domain-lookup

#### 4) CHANGE SWITCH OS NAME

- hostname S1

#### 5) ENCRYPT PASSWORDS STORED ON SWITCH

- service password-encryption

#### 6) SET EXEC PASSWORD

- enable secret <password>

#### 7) SET BANNER MESSAGE

- banner motd #MessageContent#

#### 8) CREATE VLAN 99 FOR MANAGEMENT

- vlan 99
- name VLAN99
- exit

#### 9) ASSIGN ALL PORTS INTO VLAN 99

- interface range fa0/1 - 24
- switchport access vlan 99
- exit

#### 10) SET SVI ON VLAN 99 , ADD IPv4 & IPv6

- interface vlan 99
- ip address 192.168.1.2 255.255.255.0
- ipv6 address FE80::2 link-local
- ipv6 address 2001:DB8:ACAD::2/64
- ip default-gateway 192.168.1.1
- exit

#### 11) CHECK VLAN 99 CONFIGURATION

- show interface vlan 99
- show vlan

#### 12) CLEAR MAC TABLE & ADD STATIC RECORD FOR PC

- clear mac address-table dynamic
- configure terminal
- mac address-table static 0001.4277.dd7e vlan 99 interface FastEthernet0/5
- exit
- show mac address-table
