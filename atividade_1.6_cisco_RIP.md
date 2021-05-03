## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%206.PNG)

## Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 192.168.1.10            | 255.255.255.0   | 192.168.1.1             |
| PC-02       | NIC       | 192.168.3.10            | 255.255.255.0   | 192.168.3.1             |
| PC-03       | NIC       | 192.168.5.10            | 255.255.255.0   | 192.168.5.1             |
| SW-01       | G0/1      | ---                     | ---             | ---                     |
| SW-02       | G0/1      | ---                     | ---             | ---                     |
| SW-03       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/0      | 192.168.1.1             | 255.255.255.0   | ---                     |
| RT-01       | S0/0/0    | 192.168.2.1             | 255.255.255.0   | ---                     |
| RT-01       | S0/0/1    | 209.165.200.225         | 255.255.255.252 | ---                     |
| RT-02       | G0/0/0    | 192.168.3.1             | 255.255.255.0   | ---                     |
| RT-02       | S0/0/0    | 192.168.2.2             | 255.255.255.0   | ---                     |
| RT-02       | S0/0/1    | 192.168.4.2             | 255.255.255.0   | ---                     |
| RT-03       | G0/0/0    | 192.168.5.1             | 255.255.255.0   | ---                     |
| RT-03       | S0/0/0    | 192.168.4.1             | 255.255.255.0   | ---                     |


## Codigo:
~~~
RT-01>ena
RT-01#config t
R1(config)#ip route 0.0.0.0 0.0.0.0 S0/0/1
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#no auto-summary
R1(config-router)#network 192.168.2.0
R1(config-router)#network 192.168.1.0
R1(config-router)#default
R1(config-router)#default-information ori
R1(config-router)#default-information originate 
R1(config-router)#passive
R1(config-router)#passive-interface g0/0
R1(config-router)#

R2>ena
R2#config t
R2(config)#router rip
R2(config-router)#version 2
R2(config-router)#no 
R2(config-router)#no auto
R2(config-router)#no auto-summary 
R2(config-router)#network 192.168.4.0
R2(config-router)#network 192.168.2.0
R2(config-router)#network 192.168.3.0
R2(config-router)#passive
R2(config-router)#passive-interface g0/0

R3>ena
R3#config t
R3(config)#router rip
R3(config-router)#version 2
R3(config-router)#no aut
R3(config-router)#no auto-summary 
R3(config-router)#net
R3(config-router)#network 192.168.5.0
R3(config-router)#network 192.168.4.0
R3(config-router)#passive
R3(config-router)#passive-interface g0/0
R3(config-router)#

~~~


