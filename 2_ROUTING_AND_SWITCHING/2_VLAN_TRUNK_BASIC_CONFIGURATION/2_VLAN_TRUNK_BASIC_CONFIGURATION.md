## VLAN TRUNK BASIC CONFIGURATION

***

#### 1) SET 192.168.20.13/24 IPv4 ON PC0 & 192.168.30.13/24 IPv4 ON PC1

#### 2) SET DEVICE NAME ON S0

- enable
- configure terminal
- hostname s0

#### 3) TURN OFF DNS LOOKUP ON SWITCH

- no ip domain-lookup

#### 4) ENCRYPT PASSWORDS STORED ON DEVICE

- service password-encryption

#### 5) SET EXEC MODE PASSWORD

- enable secret <password>

#### 6) SET DEVICE BANNER

- banner motd #MessageContent#

#### 7) CONFIGURE VLAN 20 ON SWITCH S0

- vlan 20
- name VLAN20
- exit

#### 8) ASSIGN FA0/6 INTERFACE INTO VLAN 20 ON S0

- interface fa0/6
- switchport mode access
- switchport access vlan 20
- no shutdown
- exit

#### 9) CONFIGURE FA0/1 INTERFACE AS TRUNK

- interface fa0/1
- switchport mode trunk
- no shutdown
- exit

#### 10) SET SVI(SWITCH VIRTUAL INTERFACE) ON S0

- interface vlan 20
- ip address 192.168.20.12 255.255.255.0

#### 11) SET DEVICE NAME ON S1

- enable
- configure terminal
- hostname s1

#### 12) TURN OFF DNS LOOKUP ON SWITCH

- no ip domain-lookup

#### 13) ENCRYPT PASSWORDS STORED ON DEVICE

- service password-encryption

#### 14) SET EXEC MODE PASSWORD

- enable secret cisco

#### 15) SET DEVICE BANNER

- banner motd #MessageContent#

#### 16) CONFIGURE VLAN 30 ON SWITCH S1

- vlan 30
- name VLAN30
- exit

#### 17) ASSIGN FA0/18 INTERFACE INTO VLAN 30 ON S1

- interface fa0/18
- switchport mode access
- switchport access vlan 30
- no shutdown
- exit

#### 18) CONFIGURE FA0/1 INTERFACE AS TRUNK

- interface fa0/1
- switchport mode trunk
- no shutdown
- exit

#### 19) SET SVI(SWITCH VIRTUAL INTERFACE) ON S1

- interface vlan 30
- ip address 192.168.30.12 255.255.255.0