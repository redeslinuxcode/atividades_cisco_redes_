## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/CENARIO_PKA_AULAS_42_43.png)

## Documentação:


| DISPOSITIVO  | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|--------------|-----------|-------------------------|-----------------|-------------------------|
| PC-00        | NIC       | 172.16.0.1              | 255.255.252.0   | 172.16.3.254            |
| PC-01        | NIC       | 172.16.7.97             | 255.255.255.240 | 172.16.7.110            |
| PC-02        | NIC       | 172.16.6.1              | 255.255.255.0   | 172.16.6.254            |
| PC-03        | NIC       | 172.16.7.1              | 255.255.255.192 | 172.16.7.62             |
| PC-04        | NIC       | 172.16.7.65             | 255.255.255.224 | 172.16.7.94             |
| PC-05        | NIC       | 172.16.4.1              | 255.255.254.0   | 172.16.5.254            | 
| R-ITQ        | G0/0/0    | 172.16.3.254            | 255.255.252.0   | ---                     |
| R-ITQ        | S0/1/0    | 172.16.7.113            | 255.255.255.252 | ---                     |
| R-SM         | G0/0/0    | 172.16.7.110            | 255.255.255.240 | ---                     |
| R-SM         | s0/1/1    | 172.16.7.121            | 255.255.255.252 | ---                     |
| R-ITA        | G0/0/0    | 172.16.6.254            | 255.255.255.0   | ---                     |
| R-ITA        | S0/1/0    | 172.16.7.118            | 255.255.255.252 | ---                     |
| R-BX         | G0/0/0    | 172.16.7.62             | 255.255.255.192 | ---                     |
| R-BX         | s0/1/0    | 172.16.7.125            | 255.255.255.252 | ---                     |
| R-LEME       | g0/0/0    | 172.16.7.94             | 255.255.255.224 | ---                     |
| R-LEME       | S0/1/0    | 172.16.7.134            | 255.255.255.252 | ---                     |
| R_PONTAL     | G0/0/0    | 172.16.5.254            | 255.255.254.0   | ---                     |
| R-PONTAL     | S0/1/0    | 172.16.7.130            | 255.255.255.252 | ---                     |
| R-SUL        | S0/2/0    | 172.16.7.126            | 255.255.255.252 | ---                     |
| R-SUL        | S0/2/1    | 172.16.7.133            | 255.255.255.252 | ---                     |
| R-SUL        | S0/1/0    | 172.16.7.129            | 255.255.255.252 | ---                     |
| R-SUL        | S0/1/1    | 10.0.0.18               | 255.255.255.252 | ---                     |
| R-RJ         | S0/1/0    | 10.0.0.17               | 255.255.255.252 | ---                     |
| R-RJ         | S0/1/1    | 10.0.0.14               | 255.255.255.252 | ---                     |
| R-SP         | S0/1/0    | 10.0.0.13               | 255.255.255.252 | ---                     |
| R-SP         | S0/1/1    | 10.0.0.12               | 255.255.255.252 | ---                     |
| R-LESTE      | S0/2/0    | 172.16.7.117            | 255.255.255.252 | ---                     |
| R-LESTE      | S0/1/1    | 172.16.7.122            | 255.255.255.252 | ---                     |
| R-LESTE      | S0/1/0    | 172.16.7.114            | 255.255.255.252 | ---                     |
| R-LESTE      | S0/2/1    | 10.0.0.21               | 255.255.255.252 | ---                     |




### R_BX
~~~~
en
conf t 
hostname R_BX
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.7.62 255.255.255.192
no shutdown
interface s0/1/0 
ip add 172.16.7.125 255.255.255.252
no shutdown
exit
router ospf 60
network 172.16.7.0 0.0.0.63 area 40
network 172.16.7.124 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~

### R_LEME

~~~
en
conf t 
hostname R_LEME
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.7.94 255.255.255.224
no shutdown
interface s0/1/0 
ip add 172.16.7.134 255.255.255.252
no shutdown
exit
router ospf 50
network 172.16.7.64 0.0.0.31 area 50
network 172.16.7.132 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~

### R_PONTAL

~~~~
en
conf t 
hostname R_PONTAL
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.5.254 255.255.254.0
no shutdown
interface s0/1/0 
ip add 172.16.7.130 255.255.255.252
no shutdown
exit
router ospf 40
network 172.16.4.0 0.0.1.255 area 60
network 172.16.7.128 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~

### R_ITA
~~~~
en
conf t 
hostname R_ITA
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.6.254 255.255.255.0
no shutdown
interface s0/1/0 
ip add 172.16.7.118 255.255.255.252
no shutdown
exit
router ospf 30
network 172.16.6.0 0.0.0.255 area 30
network 172.16.7.116 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~
### R_SM
~~~~
en
conf t 
hostname R_SM
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.7.110 255.255.255.240
no shutdown
interface s0/1/1 
ip add 172.16.7.121 255.255.255.252
no shutdown
exit
router ospf 20
network 172.16.7.96 0.0.0.15 area 20
network 172.16.7.120 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~
### R_ITQ
~~~~
en
conf t 
hostname R_ITQ
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
conf t
interface g0/0/0 
ip add 172.16.3.254 255.255.252.0
no shutdown
interface s0/1/0 
ip add 172.16.7.113 255.255.255.252
no shutdown
exit
router ospf 10
network 172.16.0.0 0.0.3.255 area 10
network 172.16.7.112 0.0.0.3 area 0
passive-interface gigabitEthernet 0/0/0
~~~~
### R_LESTE
~~~~
en
conf t 
hostname R_LESTE
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
exit
int s0/2/0
ip add 172.16.7.117 255.255.255.252
no shutdown
int s0/1/1
ip add 172.16.7.122 255.255.255.252
no shutdown
int s0/1/0
ip add 172.16.7.114 255.255.255.252
no shutdown
int s0/2/1
ip add 10.0.0.21 255.255.255.252
no shutdown
router ospf 80
network 172.16.7.116 0.0.0.3 area 0
network 172.16.7.112 0.0.0.3 area 0
network 172.16.7.120 0.0.0.3 area 0
network 10.0.0.20 0.0.0.3 area 0
redistribute bgp 13201 metric 30 subnets
router bgp 13201
network 10.0.0.20 mask 255.255.255.252
neighbor 10.0.0.22 remote-as 13202
reditribute ospf 80
~~~~
### R_SP
~~~~
en
conf t 
hostname R_SP
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
exit
int s0/1/1
ip add 10.0.0.22 255.255.255.252
no shutdown
int s0/1/0
ip add 10.0.0.13 255.255.255.252
no shutdown
router bgp 13202
network 10.0.0.20 mask 255.255.255.252
network 10.0.0.12 mask 255.255.255.252
neighbor 10.0.0.21 remote-as 13201
neighbor 10.0.0.14 remote-as 13203
~~~~
R_RJ
~~~~
en
conf t 
hostname R_RJ
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
exit
int s0/1/1
ip add 10.0.0.14 255.255.255.252
no shutdown
int s0/1/0
ip add 10.0.0.17 255.255.255.252
no shutdown
router bgp 13203
network 10.0.0.16 mask 255.255.255.252
network 10.0.0.12 mask 255.255.255.252
neighbor 10.0.0.18 remote-as 13204
neighbor 10.0.0.13 remote-as 13202
~~~~
R_SUL
~~~~
en
conf t 
hostname R_SUL
enable secret senai@132
service password-encryption
exit
conf t
line console 0
password senai@132
exit
line vty 0 4
password senai@132
exit
int s0/2/0
ip add 172.16.7.126 255.255.255.252
no shutdown
int s0/1/1
ip add 10.0.0.18 255.255.255.252
no shutdown
int s0/1/0
ip add 172.16.7.129 255.255.255.252
no shutdown
int s0/2/1
ip add 172.16.7.133 255.255.255.252
no shutdown
router ospf 70
network 172.16.7.124 0.0.0.3 area 0
network 172.16.7.132 0.0.0.3 area 0
network 172.16.7.128 0.0.0.3 area 0
network 10.0.0.16 0.0.0.3 area 0
redistribute bgp 13204 metric 30 subnets
router bgp 13204
network 10.0.0.16 mask 255.255.255.252
neighbor 10.0.0.17 remote-as 13203
reditribute ospf 70
~~~~




