## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2013.PNG)

## Documentação:

**Rede 192.168.0.0/24**

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 192.168.0.1             | 255.255.255.0   | 192.168.0.30            |
| PC-02       | NIC       | 192.168.0.2             | 255.255.255.0   | 192.168.0.30            |
| PC-03       | NIC       | 192.168.0.3             | 255.255.255.0   | 192.168.0.30            |
| SW-01       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/0      | 192.168.0.30            | 255.255.255.0   | ---                     |
| RT-01       | S0/1/0    | 10.0.0.1                | 255.255.255.0   | ---                     |

**Rede 172.16.0.0/16**

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 172.16.0.1              | 255.255.255.0   | 192.168.0.30            |
| PC-02       | NIC       | 172.16.0.2              | 255.255.255.0   | 192.168.0.30            |
| PC-03       | NIC       | 172.16.0.3              | 255.255.255.0   | 192.168.0.30            |
| SW-01       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/0      | 172.16.0.30             | 255.255.255.0   | ---                     |
| RT-01       | S0/1/0    | 10.0.0.2                | 255.255.255.0   | ---                     |

## Comandos:
~~~~
RT-01>
RT-01>ena
RT-01#config t
RT-01(config)#int g0/0/0
RT-01(config-if)#ip add 192.168.0.30 255.255.255.0
RT-01(config-if)#no shutdown
RT-01(config-if)#int s0/1/0
RT-01(config-if)#ip add 10.0.0.1 255.255.255.252
RT-01(config-if)#no shutdown
RT-01(config-if)#router rip
RT-01(config-router)#version 2
RT-01(config-router)#no auto-summary 
RT-01(config-router)#network 192.168.0.0
RT-01(config-router)#network 10.0.0.0
RT-01(config-router)#passive-interface g0/0/0
RT-01(config-router)#

outer>ena
Router#config t
RT-02(config)#
RT-02(config)#
RT-02(config)#int g0/0/0
RT-02(config-if)#ip add 172.16.0.30 255.255.0.0
RT-02(config-if)#no shutdown
RT-02(config-if)#
RT-02(config-if)#int s0/1/0
RT-02(config-if)#ip add 10.0.0.2 255.255.255.252
RT-02(config-if)#no shutdown
RT-02(config-if)#router rip
RT-02(config-router)#version 2
RT-02(config-router)#no auto-summary
RT-02(config-router)#network 172.16.0.0
RT-02(config-router)#network 10.0.0.0
RT-02(config-router)#passive-
RT-02(config-router)#passive-interface g0/0/0
RT-02(config-router)#exit
RT-02(config)#access-list 10 permit host 192.168.0.1
RT-02(config)#access-list 20 deny any 
RT-02(config)#int s0/1/0
RT-02(config-if)#ip access-group 10 in
~~~~


