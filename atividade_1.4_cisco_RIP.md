### Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%204.PNG)

### Documentação:


| DISPOSITIVO | INTERFACE | ENDEREÇO IP     | MÁSCARA         | GATEWAY PADRÃO |
|-------------|-----------|-----------------|-----------------|----------------|
| PC-00       | NIC       | 192.168.50.190  | 255.255.255.161 | 192.168.50.190 |
| PC-01       | NIC       | 192.168.40.1    | 255.255.255.0   | 192.168.30.254 |
| PC-02       | NIC       | 192.168.10.129  | 255.255.255.128 | 192.168.10.254 |
| PC-03       | NIC       | 192.168.20.65   | 255.255.255.192 | 192.168.20.126 |
| PC-04       | NIC       | 192.168.30.117  | 255.255.255.240 | 192.168.30.190 |
| PC-04       | NIC       | 192.168.60.193  | 255.255.255.248 | 192.168.60.198 |
| SW-SSP      | F0/24     | ---             | ---             | ---            |
| SW-SJUG     | F0/24     | ---             | ---             | ---            |
| SW-SSAN     | F0/24     | ---             | ---             | ---            |
| SW-SJUN     | FO/24     | ---             | ---             | ---            |
| SW-SITU     | F0/24     | ---             | ---             | ---            |
| SW-SITA     | F0/24     | ---             | ---             | ---            |
| RT-RSP      | G0/0/0    | 192.168.50.190  | 255.255.255.224 | ---            |
| RT-RSP      | S0/1/0    | 10.0.0.5        | 255.255.255.252 | ---            |
| RT-RSP      | S0/1/1    | 10.0.0.19       | 255.255.255.252 | ---            |
| RT-RJUG     | G0/0/0    | 192.168.40.254  | 255.255.255.0   | ---            |
| RT-RJUG     | S0/1/0    | 10.0.0.6        | 255.255.255.252 | ---            |
| RT-RJUG     | S0/1/1    | 10.0.0.13       | 255.255.255.252 | ---            |
| RT-RSAN     | G0/0/0    | 192.168.10.254  | 255.255.255.128 | ---            |
| RT-RSAN     | S0/1/0    | 10.0.0.14       | 255.255.255.252 | ---            |
| RT-RSAN     | S0/1/1    | 10.0.0.1        | 255.255.255.252 | ---            |
| RT-RJUN     | G0/0/0    | 192.168.20.126  | 255.255.255.192 | ---            |
| RT-RJUN     | S0/1/0    | 10.0.0.2        | 255.255.255.252 | ---            |
| RT-RJUN     | S0/1/1    | 10.0.0.9        | 255.255.255.128 | ---            |
| RT-RITU     | G0/0/0    | 192.168.30.190  | 255.255.255.240 | ---            |
| RT-RITU     | S0/1/0    | 10.0.0.10       | 255.255.255.252 | ---            |
| RT-RITU     | S0/1/1    | 10.0.0.21       | 255.255.255.252 | ---            |
| RT-RITA     | G0/0/0    | 192.168.60.198  | 255.255.255.248 | ---            |
| RT-RITA     | S0/1/0    | 10.0.0.22       | 255.255.255.252 | ---            |
| RT-RITA     | S0/1/1    | 10.0.0.18       | 255.255.255.252 | ---            |

### Codigo:

~~~
RT-RSP>enable
RT-RSP#config terminal
RT-RSP(config)int g0/0/0
RT-RSP(config-if)ip add 192.168.50.190 255.255.255.224
RT-RSP(config-if)no shutdown
RT-RSP(config-if)int s0/1/1
RT-RSP(config-if)ip add 10.0.0.19 255.255.255.252
RT-RSP(config-if)no shutdown
RT-RSP(config-if)int s0/1/0
RT-RSP(config-if)ip add 10.0.0.5 255.255.255.252
RT-RSP(config-if)no shutdown
RT-RSP(config-if)router rip
RT-RSP(config-router)version 2
RT-RSP(config-router)network 192.168.50.0
RT-RSP(config-router)network 10.0.0.4
RT-RSP(config-router)network 10.0.0.16
RT-RSP(config-router)no auto-summary
RT-RSP(config-router)passive-interface g0/0/0

RT-RJUG>enable
RT-RJUG#config terminal
RT-RJUG(config)int g0/0/0
RT-RJUG(config-if)ip add 192.168.40.254 255.255.255.0
RT-RJUG(config-if)no shutdown
RT-RJUG(config-if)int s0/1/0
RT-RJUG(config-if)ip add 10.0.0.6 255.255.255.252
RT-RJUG(config-if)no shutdown
RT-RJUG(config-if)int s0/1/1
RT-RJUG(config-if)ip add 10.0.0.15 255.255.255.252
RT-RJUG(config-if)no shutdown
RT-RJUG(config-if)router rip
RT-RJUG(config-router)version 2
RT-RJUG(config-router)network 192.168.40.0
RT-RJUG(config-router)network 10.0.0.4
RT-RJUG(config-router)network 10.0.0.12
RT-RJUG(config-router)no auto-summary
RT-RJUG(config-router)passive-interface g0/0/0

RT-RSAN>enable
RT-RSAN#config terminal
RT-RSAN(config)int g0/0/0
RT-RSAN(config-if)ip add 192.168.10.254 255.255.255.128
RT-RSAN(config-if)no shutdown
RT-RSAN(config-if)int s0/1/1
RT-RSAN(config-if)ip add 10.0.0.1 255.255.255.252
RT-RSAN(config-if)no shutdown
RT-RSAN(config-if)int s0/1/0
RT-RSAN(config-if)ip add 10.0.0.14 255.255.255.252
RT-RSAN(config-if)no shutdown
RT-RSAN(config-if)router rip
RT-RSAN(config-router)version 2
RT-RSAN(config-router)network 192.168.50.0
RT-RSAN(config-router)network 10.0.0.0
RT-RSAN(config-router)network 10.0.0.12
RT-RSAN(config-router)no auto-summary
RT-RSAN(config-router)passive-interface g0/0/0



RT-RJUN>enable
RT-RJUN#config terminal
RT-RJUN(config)int g0/0/0
RT-RJUN(config-if)ip add 192.168.20.126 255.255.255.192
RT-RJUN(config-if)no shutdown
RT-RJUN(config-if)int s0/1/1
RT-RJUN(config-if)ip add 10.0.0.9 255.255.255.252
RT-RJUN(config-if)no shutdown
RT-RJUN(config-if)int s0/1/0
RT-RJUN(config-if)ip add 10.0.0.2 255.255.255.252
RT-RJUN(config-if)no shutdown
RT-RJUN(config-if)router rip
RT-RJUN(config-router)version 2
RT-RJUN(config-router)network 192.168.20.0
RT-RJUN(config-router)network 10.0.0.8
RT-RJUN(config-router)network 10.0.0.0
RT-RJUN(config-router)no auto-summary
RT-RJUN(config-router)passive-interface g0/0/0


RT-RITU>enable
RT-RITU#config terminal
RT-RITU(config)int g0/0/0
RT-RITU(config-if)ip add 192.168.30.126 255.255.255.240
RT-RITU(config-if)no shutdown
RT-RITU(config-if)int s0/1/1
RT-RITU(config-if)ip add 10.0.0.21 255.255.255.252
RT-RITU(config-if)no shutdown
RT-RITU(config-if)int s0/1/0
RT-RITU(config-if)ip add 10.0.0.10 255.255.255.252
RT-RITU(config-if)no shutdown
RT-RITU(config-if)router rip
RT-RITU(config-router)version 2
RT-RITU(config-router)network 192.168.30.0
RT-RITU(config-router)network 10.0.0.8
RT-RITU(config-router)network 10.0.0.20
RT-RITU(config-router)no auto-summary
RT-RITU(config-router)passive-interface g0/0/0



RT-RITA>enable
RT-RITA#config terminal
RT-RITA(config)int g0/0/0
RT-RITA(config-if)ip add 192.168.60.198 255.255.255.248
RT-RITA(config-if)no shutdown
RT-RITA(config-if)int s0/1/1
RT-RITA(config-if)ip add 10.0.0.18 255.255.255.252
RT-RITA(config-if)no shutdown
RT-RITA(config-if)int s0/1/0
RT-RITA(config-if)ip add 10.0.0.22 255.255.255.252
RT-RITA(config-if)no shutdown
RT-RITA(config-if)router rip
RT-RITA(config-router)version 2
RT-RITA(config-router)network 192.168.60.0
RT-RITA(config-router)network 10.0.0.16
RT-RITA(config-router)network 10.0.0.20
RT-RITA(config-router)no auto-summary
RT-RITA(config-router)passive-interface g0/0/0

~~~



