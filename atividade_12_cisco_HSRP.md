## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/Topologia%2012.PNG)

## Documentação:


| DISPOSITIVO  | INTERFACE | ENDEREÇO IP   | MASCARA         | GATEWAY PADRÃO | HSRP          |
|--------------|-----------|---------------|-----------------|----------------|---------------|
| PC-00        | NIC       | 192.168.0.1   | 255.255.255.0   | 192.168.0.251  | 192.168.0.250 |
| PC-01        | NIC       | 192.168.0.2   | 255.255.255.0   | 192.168.0.252  | 192.168.0.250 |
| PC-03        | NIC       | 192.168.0.3   | 255.255.255.0   | 192.168.0.253  | 192.168.0.250 |
| SERVER       | NIC       | 209.145.200.1 | 255.255.255.224 | 209.145.200.2  | ---           |
| SW-00        | G0/1      | ---           | ---             | ---            | ---           |
| SW-01        | G0/1      | ---           | ---             | ---            | ---           |
| SW-01        | G0/2      | ---           | ---             | ---            | ---           |
| SW-01        | F0/24     | ---           | ---             | ---            | ---           |
| SW-02        | G0/1      | ---           | ---             | ---            | ---           |
| SW-02        | G0/2      | ---           | ---             | ---            | ---           |
| SW-02        | F0/23     | ---           | ---             | ---            | ---           |
| SW-02        | F0/24     | ---           | ---             | ---            | ---           |
| SW-03        | G0/1      | ---           | ---             | ---            | ---           |
| SW-03        | G0/2      | ---           | ---             | ---            | ---           |
| SW-03        | F0/24     | ---           | ---             | ---            | ---           |
| SW-04        | G0/1      | ---           | ---             | ---            | ---           |
| SW-04        | F0/24     | ---           | ---             | ---            | ---           |
| RT-01        | G0/0      | 192.168.0.251 | 255.255.255.0   | ---            | ---           |
| RT-01        | s0/1/0    | 10.0.0.1      | 255.255.255.252 | ---            | ---           |
| RT-02        | g0/0      | 192.168.0.252 | 255.255.255.0   | ---            | ---           | 
| RT-02        | S0/1/0    | 10.0.0.5      | 255.255.255.252 | ---            | ---           |
| RT-03        | G0/0      | 192.168.0.253 | 255.255.255.0   | ---            | ---           | 
| RT-03        | S0/1/0    | 10.0.0.9      | 255.255.255.252 | ---            | ---           |
| RT-04        | S0/0/0    | 10.0.0.2      | 255.255.255.252 | ---            | ---           |
| RT-04        | S0/0/1    | 10.0.0.6      | 255.255.255.252 | ---            | ---           |
| RT-04        | S0/1/0    | 10.0.0.10     | 255.255.255.252 | ---            | ---           |
| RT-04        | S0/1/1    | 10.0.0.14     | 255.255.255.252 | ---            | ---           |
| RT-05        | G0/0      | 209.145.200.2 | 255.255.255.0   | ---            |               |
| RT-05        | S0/1/1    | 10.0.0.13     | 255.255.255.252 | ---            |               |

## Comandos:

~~~~
RT-01
Router>
Router>ena
Router#config t
Router#hostname RT-01
RT-01(config)#int g0/0
RT-01(config-if)#ip add 192.168.0.251 255.255.255.0
RT-01(config-if)#no shutdown
RT-01(config-if)int s0/1/0
RT-01(config-if)#ip add 10.0.0.1 255.255.255.252
RT-01(config-if)#no shutdown
RT-01(config-if)#router rip
RT-01(config-router)#no auto-summary
RT-01(config-router)#network 10.0.0.0
RT-01(config-router)#network 192.168.0.0
RT-01(config-router)#passive-interface g0/0
RT-01(config-router)#exit
RT-01(config)#int g0/0
RT-01(config-if)#standby version 2
RT-01(config-if)#standby 1 ip 192.168.0.250
RT-01(config-if)#standby 1 priority 150

RT-02
Router>
Router>ena
Router#config t
Router#hostname RT-02
RT-02(config)#int g0/0
RT-02(config-if)#ip add 192.168.0.252 255.255.255.0
RT-02(config-if)#no shutdown
RT-02(config-if)int s0/1/0
RT-02(config-if)#ip add 10.0.0.5 255.255.255.252
RT-02(config-if)#no shutdown
RT-02(config-if)#router rip
RT-02(config-router)#no auto-summary
RT-02(config-router)#network 10.0.0.4
RT-02(config-router)#network 192.168.0.0
RT-02(config-router)#passive-interface g0/0
RT-02(config-router)#exit
RT-02(config)#int g0/0
RT-02(config-if)#standby version 2
RT-02(config-if)#standby 1 ip 192.168.0.250
RT-02(config-if)#standby 1 priority 140

RT-03
Router>
Router>ena
Router#config t
Router#hostname RT-03
RT-01(config)#int g0/0
RT-03(config-if)#ip add 192.168.0.253 255.255.255.0
RT-03(config-if)#no shutdown
RT-03(config-if)int s0/1/0
RT-03(config-if)#ip add 10.0.0.9 255.255.255.252
RT-03(config-if)#no shutdown
RT-03(config-if)#router rip
RT-03(config-router)#no auto-summary
RT-03(config-router)#network 10.0.0.8
RT-03(config-router)#network 192.168.0.0
RT-03(config-router)#passive-interface g0/0
RT-03(config-router)#exit
RT-03(config)#int g0/0
RT-03(config-if)#standby version 2
RT-03(config-if)#standby 1 ip 192.168.0.250
RT-03(config-if)#standby 1 priority 130

RT-05
Router>
Router>ena
Router#config t
Router#hostname RT-05
RT-05(config)#int g0/0
RT-05(config-if)#ip add 209.145.200.2 255.255.255.224
RT-05(config-if)#no shutdown
RT-05(config-if)int s0/1/1
RT-05(config-if)#ip add 10.0.0.13 255.255.255.252
RT-05(config-if)#no shutdown
RT-05(config-if)#router rip
RT-05(config-router)#no auto-summary
RT-05(config-router)#network 10.0.0.12
RT-05(config-router)#network 209.145.200.0
RT-05(config-router)#passive-interface g0/0
RT-05(config-router)#exit

RT-04
Router>
Router>ena
Router#config t
Router#hostname RT-05
RT-05(config)#int s0/0/0
RT-05(config-if)#ip add 10.0.0.2 255.255.255.252
RT-05(config-if)#no shutdown
RT-05(config-if)int s0/0/1
RT-05(config-if)#ip add 10.0.0.6 255.255.255.252
RT-05(config-if)#no shutdown
RT-05(config-if)int s0/1/0
RT-05(config-if)#ip add 10.0.0.10 255.255.255.252
RT-05(config-if)#no shutdown
RT-05(config-if)int s0/1/1
RT-05(config-if)#ip add 10.0.0.14 255.255.255.252
RT-05(config-if)#no shutdown
RT-05(config-if)#router rip
RT-05(config-router)#no auto-summary
RT-05(config-router)#network 10.0.0.0
RT-05(config-router)#network 10.0.0.4
RT-05(config-router)#network 10.0.0.8
RT-05(config-router)#network 10.0.0.12
RT-05(config-router)#defaul-information originate
RT-05(config-router)#ip route 0.0.0.0 0.0.0.0 209.145.200.0

~~~~
