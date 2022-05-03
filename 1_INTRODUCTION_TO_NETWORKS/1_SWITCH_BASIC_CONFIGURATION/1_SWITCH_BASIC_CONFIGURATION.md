## SWITCH BASIC CONFIGURATION

***

#### 1) SET IP 192.168.1.10 ON PC0

#### 2) SET IP 192.168.1.11 ON PC1

#### 3) SET IP ON SWITCH VIRTUAL INTERFACE (SVI) S1 - 192.168.1.2

- enable
- configure terminal
- interface vlan 1
- ip address 192.168.1.2 255.255.255.0
- ip default-gateway 192.168.1.1

#### 4) SET IP ON SWITCH VIRTUAL INTERFACE (SVI) S2 - 192.168.1.3

- enable
- configure terminal
- interface vlan 1
- ip address 192.168.1.3 255.255.255.0
- ip default-gateway 192.168.1.1

#### 5) SET CONSOLE ACCESS PASSWORD ON S1 & S2

- configure terminal
- line console 0
- password <password>
- login
- end

#### 6) SET EXEC MODE PASSWORD ON S1 & S2
- configure terminal
- enable secret <password>
- exit

#### 7) SET VTY SSH PASSWORD ON S1 & S2

- configure terminal
- line vty 0 15
- password <password>
- login
- end

#### 8) ENCRYPT STORED PASSWORDS ON S1 & S2

- configure terminal
- service password-encryption

#### 9) SET DEVICE MESSAGE BANNER ON S1 & S2

- configure terminal
- banner motd #MESSAGE_CONTENT#

#### 10 SET RUNNING CONFIG COPY INTO STARTUP CONFIG ON S1 & S2

- copy running-config startup-config

#### 11) VALIDATE CONFIGURATION

- show running-config
