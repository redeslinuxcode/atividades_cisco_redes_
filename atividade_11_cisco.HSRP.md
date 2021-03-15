## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2011.PNG)

## Documentação:

| DISPOSITIVO  | INTERFACE | ENDEREÇO IP   | MASCARA         | GATEWAY PADRÃO | HSRP          |
|--------------|-----------|---------------|-----------------|----------------|---------------|
| PC-00        | NIC       | 192.168.0.1   | 255.255.255.0   | 192.168.0.254  | 192.168.0.250 |
| PC-01        | NIC       | 192.168.0.2   | 255.255.255.0   | 192.168.0.253  | 192.168.0.250 |
| SW-00        | G0/1      | ---           | ---             | ---            | ---           |
| SW-01        | G0/1      | ---           | ---             | ---            | ---           |
| RT-PRINC     | G0/0      | 192.168.0.254 | 255.255.255.0   | ---            | ---           |
| RT-PRINC     | s0/1/0    | 10.0.0.1      | 255.255.255.252 | ---            | ---           |
| RT-OPERADORA | S0/1/1    | 10.0.0.5      | 255.255.255.252 | ---            | ---           | 
| RT-OPERADORA | S0/1/0    | 10.0.0.2      | 255.255.255.252 | ---            | ---           |
| RT-BKP       | G0/0      | 192.168.0.253 | 255.255.255.0   | ---            | ---           | 
| RT-BKP       | S0/1/1    | 10.0.0.6      | 255.255.255.252 | ---            | ---           |
| RT-BKP       | S0/1/1    | 10.0.0.5      | 255.255.255.252 | ---            | ---           |

## Comandos:

~~~
RT-PRINC
Router>
Router>ena 
Router#config t
Router(config)#hostname RT-PRINC
RT-PRINC(config)#int g0/0
RT-PRINC(config-if)#ip add 192.168.0.254 255.255.255.0
RT-PRINC(config-if)#standby version 2
RT-PRINC(config-if)#standby 1 ip 192.168.0.250
RT-PRINC(config-if)#standby 1 priority 150
RT-PRINC(config-if)#no shutdown
RT-PRINC(config-if)#
RT-PRINC(config-if)#int s0/1/0
RT-PRINC(config-if)#ip add 10.0.0.1 255.255.255.252
RT-PRINC(config-if)#no shutdown
RT-PRINC(config-if)#
RT-PRINC(config-if)#router rip
RT-PRINC(config-router)#version 2
RT-PRINC(config-router)#no auto-summary
RT-PRINC(config-router)#network 10.0.0.0
RT-PRINC(config-router)#network 192.168.0.0
RT-PRINC(config-router)#passive-interface g0/0


RT-BKP
Router>
Router>ena
Router#config t
Router(config)#ena 
Router(config)#config t
Router(config)#hostname RT-BKP
RT-BKP(config)#int g0/0
RT-BKP(config-if)#ip add 192.168.0.253 255.255.255.0
RT-BKP(config-if)#standby version 2
RT-BKP(config-if)#standby 1 ip 192.168.0.250
RT-BKP(config-if)#no shutdown
RT-BKP(config-if)#
RT-BKP(config-if)#int s0/1/1
RT-BKP(config-if)#ip add 10.0.0.6 255.255.255.252
RT-BKP(config-if)#no shutdown
RT-BKP(config-if)#
RT-BKP(config-if)#router rip
RT-BKP(config-router)#version 2
RT-BKP(config-router)#no auto-summary
RT-BKP(config-router)#network 10.0.0.4
RT-BKP(config-router)#network 192.168.0.0
RT-BKP(config-router)#passive-interface g0/0

Router>
Router>ena
Router#config t
Router(config)#ena 
Router(config)#config t
Router(config)#hostname RT-OPERADORA
RT-OPERADORA(config)#int S0/1/1
RT-OPEADORA(config-if)#ip add 10.0.0.5 255.255.255.252
RT-OPERADORA(config-if)#int s0/1/0
RT-OPEADORA(config-if)#ip add 10.0.0.2 255.255.255.252
RT-OPERADORA(config-if)#no shutdown
RT-OPERADORA(config-if)#int loopback 1
RT-OPERADORA(config-if)#ip add 209.145.200.1 255.255.255.224
RT-OPERADORA(config-if)ip route 0.0.0.0 0.0.0.0 209.145.200.0 
RT-OPERADORA(config-if)#router rip
RT-OPERADORA(config-router)#version 2
RT-OPERADORA(config-router)#no auto-summary
RT-OPERADORA(config-router)#network 10.0.0.4
RT-OPERADORA(config-router)#network 10.0.0.0
