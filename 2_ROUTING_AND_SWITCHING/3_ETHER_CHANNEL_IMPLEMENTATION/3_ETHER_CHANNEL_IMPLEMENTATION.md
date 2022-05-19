#### ETHER CHANNEL IMPLEMENTATION

***

#### ASSUMPTIONS:
**S1** - VLAN 10, 192.168.10.11 255.255.255.0
**S2** - VLAN 10, 192.168.10.12 255.255.255.0
**PC0** - VLAN 20, 192.168.20.3 255.255.255.0
**PC1** - VLAN 20, 192.168.20.4 255.255.255.0

**VLAN 10** - MANAGEMENT
**VLAN 20** - S1/S2 Fa0/3
**VLAN 99** - S1/S2 Fa0/4-24

#### 1) S1/S2 - SET DEVICE NAME

- enable
- configure terminal
- hostname <name>

#### 2) S1/S2 - TURN OFF DNS LOOKUP ON SWITCH

- no ip domain-lookup

#### 3) S1/S2 - SET EXEC MODE PASSWORD

- enable secret <password>

#### 4) S1/S2 - SET CONSOLE PASSWORD

- line console 0
- password <password>
- login
- exit

#### 5) S1/S2 - SET VIRTUAL TERMINAL PASSWORD

- line vty 0 4
- password <password>
- login
- transport input ssh

#### 6) S1/S2 - ENCRYPT DEVICE PASSWORDS

- service password-encryption

#### 7) S1/S2 - SET DEVICE BANNER

- banner motd #MessageContent#

#### 8) S1/S2 - SAVE RUNNING CONFIG AS STARTUP CONFIG

- exit
- copy running-config startup-config

#### 9) S1 - CREATE VLAN, ASSIGN FA0/3 INTERFACE INTO VLAN 20, MOVE NOT USED INTERFACES INTO SEPARATED VLAN 99 & DEACTIVATE THEM, SET MANAGEMENT VLAN IP

- configure terminal
- vlan 10
- name VLAN10
- exit

- vlan 20
- name VLAN10
- exit

- vlan 99
- name VLAN99
- exit

- interface fa0/3
- switchport mode access
- switchport access vlan 20
- exit

- interface range fa0/4 - 24
- switchport access vlan 99
- shutdown
- exit

- interface vlan 10
- ip address 192.168.10.11 255.255.255.0
- no shutdown
- exit

#### 10) S2 - CREATE VLAN, ASSIGN FA0/3 INTERFACE INTO VLAN 20, MOVE NOT USED INTERFACES INTO SEPARATED VLAN 99 & DEACTIVATE THEM, SET MANAGEMENT VLAN IP

- vlan 10
- name VLAN10
- exit

- vlan 20
- name VLAN10
- exit

- vlan 99
- name VLAN99
- exit

- interface fa0/3
- switchport mode access
- switchport access vlan 20
- exit

- interface range fa04 - 24
- switchport access vlan 99
- shutdown
- exit

- interface vlan 10
- ip address 192.168.10.12 255.255.255.0
- no shutdown
- exit

#### 11) S1/S2 - SET ETHER CHANNEL (PORT CHANNEL GROUP 1) FOR FA0/1 & FA0/2 INTERFACES

- interface range Fa0/1 - 2
- channel-group 1 mode active
- exit

#### 12) S1/S2 - SET PORT CHANNEL INTERFACES (FA0/1 & FA0/2) AS TRUNK, ALLOW VLAN 10/20 FRAMES FOR TRUNK LINK

- interface port-channel 1
- switchport mode trunk
- switchport trunk allowed vlan 10, 20
- no shutdown
- exit

#### 13) SPRAWDZAMY POPRAWNOŚĆ KONFIGURACJI
- show interfaces port-channel 1
- show etherchannel summary
- show interfaces trunk
