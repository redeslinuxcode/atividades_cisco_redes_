### Topologia:
![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/TOPOLOGIA%203.PNG)

### Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP     | MÁSCARA         | GATEWAY PADRÃO |
|-------------|-----------|-----------------|-----------------|----------------|
| PC-00       | NIC       | 192.168.10.1    | 255.255.255.128 | 192.168.10.126 |
| PC-01       | NIC       | 192.168.30.65   | 255.255.255.128 | 192.168.30.126 |
| PC-02       | NIC       | 192.168.50.194  | 255.255.255.192 | 192.168.50.254 |
| SW-SSP      | F0/24     | ---             | ---             | ---            |
| SW-SRJ      | FO/24     | ---             | ---             | ---            |
| SW-SANTOS   | F0/24     | ---             | ---             | ---            |
| RT-RSP      | G0/0/0    | 192.168.10.126  | 255.255.255.128 | ---            |
| RT-RSP      | S0/1/0    | 10.0.0.1        | 255.255.255.252 | ---            |
| RT-RSP      | S0/1/1    | 10.0.0.26       | 255.255.255.252 | ---            |
| RT-RINT-A   | S0/1/1    | 10.0.0.2        | 255.255.255.252 | ---            |
| RT-RINT-A   | S0/1/0    | 10.0.0.5        | 255.255.255.252 | ---            |
| RT-RINT-B   | S0/1/1    | 10.0.0.6        | 255.255.255.252 | ---            |
| RT-RINT-B   | S0/1/0    | 10.0.0.9        | 255.255.255.252 | ---            |
| RT-RINT-C   | S0/1/1    | 10.0.0.13       | 255.255.255.252 | ---            |
| RT-RINT-C   | S0/1/0    | 10.0.0.10       | 255.255.255.252 | ---            |
| RT-RINT-D   | S0/1/1    | 10.0.0.17       | 255.255.255.252 | ---            |
| RT-RINT-D   | S0/1/0    | 10.0.0.14       | 255.255.255.252 | ---            |
| RT-RJJ      | G0/0/0    | 192.168.30.126  | 255.255.255.128 | ---            |
| RT-RJJ      | S0/1/1    | 10.0.0.21       | 255.255.255.252 | ---            |
| RT-RJJ      | S0/1/0    | 10.0.0.18       | 255.255.255.252 | ---            |
| RT-RSANTOS  | S0/1/1    | 10.0.0.22       | 255.255.255.252 | ---            |
| RT-RSANTOS  | S0/1/0    | 10.0.0.25       | 255.255.255.252 | ---            |


### Codigo:
~~~~
### RT-RST:
RT-RSP>enable
RT-RSP#config terminal
RT-RSP(config)interface g0/0/0
RT-RSP(config-if)ip add 192.168.10.126 255.255.255.128
RT-RSP(config-if)no shutdown
RT-RSP(config-if)interface s0/1/0
RT-RSP(config-if)clock rate 2000000
RT-RSP(config-if)ip add 192.168.10.126 255.255.255.128
RT-RSP(config-if)no shutdown
RT-RSP(config-if)interface s0/1/1
RT-RSP(config-if)ip address 10.0.0.26 255.255.255.252
RT-RSP(config-if)no shutdown
RT-RSP(config-if)router rip
RT-RSP(config-router)version 2
RT-RSP(config-router)no auto-summary
RT-RSP(config-router)passive-interface g0/0/0
RT-RSP(config-router)network 192.168.10.0
RT-RSP(config-router)network 10.0.0.0
RT-RSP(config-router)network 10.0.0.24


###RINT-A
RT-RINT-A>enable
RT-RINT-A#config terminal
RT-RINT-A(config)int s0/1/1
RT-RINT-A(config-if)ip add 10.0.0.2 255.255.255.252
RT-RINT-A(config-if)ip add 10.0.0.2 255.255.255.252
RT-RINT-A(config-if)int s0/1/0
RT-RINT-A(config-if)clock rate 2000000
RT-RINT-A(config-if)ip add 10.0.0.5 255.255.255.252
RT-RINT-A(config-if)no shutdown
RT-RINT-A(config-if)router rip
RT-RINT-A(config-router)version 2
RT-RINT-A(config-router)network 10.0.0.0
RT-RINT-A(config-router)network 10.0.0.4

###RINT-B
RT-RINT-B>enable
RT-RINT-B#config terminal
RT-RINT-B(config)int s0/1/0
RT-RINT-B(config-if)ip add 10.0.0.6 255.255.255.252
RT-RINT-B(config-if)no shutdown
RT-RINT-B(config-if)int s0/1/1
RT-RINT-B(config-if)clock rate 2000000
RT-RINT-B(config-if)ip add 10.0.0.9 255.255.255.252
RT-RINT-B(config-if)no shutdown
RT-RINT-B(config-if)router rip
RT-RINT-B(config-router)version 2
RT-RINT-B(config-router)network 10.0.0.4
RT-RINT-B(config-router)network 10.0.0.8

###RINT-C
RT-RINT-C>enable
RT-RINT-C#config terminal
RT-RINT-C(config)int s0/1/0
RT-RINT-C(config-if)ip add 10.0.0.10 255.255.255.252
RT-RINT-C(config-if)no shutdown
RT-RINT-C(config-if)int s0/1/1
RT-RINT-C(config-if)clock rate 2000000
RT-RINT-C(config-if)ip add 10.0.0.13 255.255.255.252
RT-RINT-C(config-if)no shutdown
RT-RINT-C(config-if)router rip
RT-RINT-C(config-router)network 10.0.0.12
RT-RINT-C(config-router)network 10.0.0.8

###RINT-D
RT-RINT-D>enable
RT-RINT-D#config terminal
RT-RINT-D(config)int s0/1/0
RT-RINT-D(config-if)ip add 10.0.0.14 255.255.255.252
RT-RINT-D(config-if)no shutdown
RT-RINT-D(config-if)int s0/1/1
RT-RINT-D(config-if)clack rate 2000000
RT-RINT-D(config-if)ip add 10.0.0.17 255.255.255.252
RT-RINT-D(config-if)no shutdown
RT-RINT-D(config-if)router rip
RT-RINT-D(config-router)version 2
RT-RINT-D(config-router)network 10.0.0.12
RT-RINT-D(config-router)network 10.0.0.16

###RJJ
RT-RJJ>enable
RT-RJJ#config terminal
RT-RJJ(config)int g0/0/0
RT-RJJ(config-if)ip add 192.168.30.126 255.255.255.128
RT-RJJ(config-if)no shutdown
RT-RJJ(config-if)int s0/1/0
RT-RJJ(config-if)ip add 10.0.0.18 255.255.255.252
RT-RJJ(config-if)no shutdown
RT-RJJ(config-if)int s0/1/1
RT-RJJ(config-if)clock rate 9600
RT-RJJ(config-if)ip add 10.0.0.21 255.255.255.252
RT-RJJ(config-if)no shutdown
RT-RJJ(config-if)router rip
RT-RJJ(config-router)version 2
RT-RJJ(config-router)network 192.168.30.0
RT-RJJ(config-router)network 10.0.0.16
RT-RJJ(config-router)network 10.0.0.20
RT-RJJ(config-router)passive-interface g0/0/0

###RSANTOS
RT-RSP>enable
RT-RINT-A#config terminal
RT-RINT-A(config)int g0/0/0
RT-RINT-A(config-if)ip add 192.168.50.254 255.255.255.192
RT-RINT-A(config-if)no shutdown
RT-RINT-A(config-if)int s0/1/0
RT-RINT-A(config-if)clock rate 9600
RT-RINT-A(config-if)ip add 10.0.0.25 255.255.255.252
RT-RINT-A(config-if)no shutdown
RT-RINT-A(config-if)int s0/1/1
RT-RINT-A(config-if)ip add 10.0.0.22 255.255.255.252
RT-RINT-A(config-if)no shutdown
RT-RINT-A(config-if)router rip
RT-RINT-A(config-router)version 2
RT-RINT-A(config-router)network 192.168.50.0
RT-RINT-A(config-router)network 10.0.0.24
RT-RINT-A(config-router)network 10.0.0.20
RT-RINT-A(config-router)passive-interface g0/0/0

~~~~


