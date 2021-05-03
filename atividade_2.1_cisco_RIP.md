
### Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%202.PNG)

### Documentação:


| DISPOSITIVO | INTERFACE  | ENDEREÇO IP     | MÁSCARA         | GATEWAY PADRÃO |
|-------------|------------|-----------------|-----------------|----------------|
| PC-00       | NIC        | 192.168.10.10   | 255.255.255.128 | 192.168.10.126 |
| PC-01       | NIC        | 192.168.0.10    | 255.255.255.192 | 192.168.0.1    |
| SW-00       | F0/24-G0/0 | ---             | ---             | ---            |
| SW-01       | FO/24-G0/0 | ---             | ---             | ---            |
| RT-RSP      | G0/0/0     | 192.168.10.126  | 255.255.255.128 | ---            |
| RT-RSP      | S0/1/0     | 10.0.0.9        | 255.255.255.252 | ---            |
| RT-RSP      | S0/1/1     | 10.0.0.17       | 255.255.255.252 | ---            |
| RT-RINTB    | S0/1/0     | 10.0.0.13       | 255.255.255.252 | ---            |
| RT-RINTB    | S0/1/1     | 10.0.0.10       | 255.255.255.252 | ---            |
| RT-RRJ      | G0/0/0     | 192.168.0.1     | 255.255.255.0   | ---            |
| RT-RRJ      | S0/1/0     | 10.0.0.14       | 255.255.255.252 | ---            |
| RT-RRJ      | S0/1/1     | 10.0.0.1        | 255.255.255.252 | ---            |
| RINTA       | S0/1/0     | 10.0.0.18       | 255.255.255.252 | ---            |
| RINTA       | S0/1/1     | 10.0.0.2        | 255.255.255.252 | ---            |

### Codigo:
~~~
### RT-RST:
RT-RSP>enable
RT-RSP#config terminal
RT-RSP(config)interface g0/0/0
RT-RSP(config-if)ip address 192.168.10.126 255.255.255.128
RT-RSP(config-if)no shutdown
RT-RSP(config-if)interface s0/1/0
RT-RSP(config-if)clock rate 2000000
RT-RSP(config-if)ip address 10.0.0.9 255.255.255.252
RT-RSP(config-if)no shutdown
RT-RSP(config-if)interface s0/1/1
RT-RSP(config-if)ip address 10.0.0.17 255.255.255.252
RT-RSP(config-if)no shutdown
RT-RSP(config-if)router rip
RT-RSP(config-router)version 2
RT-RSP(config-router)no auto-summary
RT-RSP(config-router)passive-interface g0/0/0
RT-RSP(config-router)network 192.168.10.0
RT-RSP(config-router)network 10.0.0.16
RT-RSP(config-router)network 10.0.0.8

### RT-RINTB:
RT-RINTB>enable
RT-RINTB#config terminal
RT-RINTB(config-if)interface s0/1/1
RT-RINTB(config-if)ip address 10.0.0.10 255.255.255.252
RT-RINTB(config-if)no shutdown
RT-RINTB(config-if)interface s0/1/0
RT-RINTB(config-if)ip address 10.0.0.13 255.255.255.252
RT-RINTB(config-if)no shutdown
RT-RINTB(config-if)router rip
RT-RINTB(config-router)version 2
RT-RINTB(config-router)no auto-summary
RT-RINTB(config-router)network 10.0.0.8
RT-RINTB(config-router)network 10.0.0.12

### RT-RRJ:
RT-RRJ>enable
RT-RRJ#config terminal
RT-RRJ(config)interface g0/0/0
RT-RRJ(config-if)ip address 192.168.0.1 255.255.255.0
RT-RRJ(config-if)no shutdown
RT-RRJ(config-if)interface s0/1/0
RT-RRJ(config-if)clock rate 9600
RT-RRJ(config-if)ip address 10.0.0.14 255.255.255.252
RT-RRJ(config-if)no shutdown
RT-RRJ(config-if)interface s0/1/1
RT-RRJ(config-if)ip address 10.0.0.1 255.255.255.252
RT-RRJ(config-if)no shutdown
RT-RRJ(config-if)router rip
RT-RRJ(config-router)version 2
RT-RRJ(config-router)no auto-summary
RT-RRJ(config-router)passive-interface g0/0/0
RT-RRJ(config-router)network 192.168.0.0
RT-RRJ(config-router)network 10.0.12.0
RT-RRJ(config-router)network 10.0.0.0


### RT-RINTA:
RT-RINTA>enable
RT-RINTA#config terminal
RT-RINTA(config-if)interface s0/1/0
RT-RINTA(config-if)clock rate 9600
RT-RINTA(config-if)ip address 10.0.0.18 255.255.255.252
RT-RINTA(config-if)no shutdown
RT-RINTA(config-if)interface s0/1/1
RT-RINTA(config-if)ip address 10.0.0.1 255.255.255.252
RT-RINTA(config-if)no shutdown
RT-RINTA(config-if)router rip
RT-RINTA(config-router)version 2
RT-RINTA(config-router)no auto-summary
RT-RINTA(config-router)network 10.0.16.0
RT-RINTA(config-router)network 10.0.0.0

~~~~


### teste de ping:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/ping%202.1.PNG) ![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/ping%202.2.PNG)

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/ping%202.3.PNG) ![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/ping%202.4.PNG)


