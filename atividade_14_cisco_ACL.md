## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2014.PNG)

## Documentação:

**Rede 192.168.10.0/24**

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 192.168.10.10           | 255.255.255.0   | 192.168.10.1            |
| PC-02       | NIC       | 192.168.10.11           | 255.255.255.0   | 192.168.10.1            |
| SW-01       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/0      | 192.168.10.1            | 255.255.255.0   | ---                     |


**Rede 192.168.11.0/24**

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-03       | NIC       | 192.168.11.10           | 255.255.255.0   | 192.168.11.1            |
| SW-02       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/1      | 192.168.11.1            | 255.255.255.0   | ---                     |

**Rede 192.168.30.0/24**

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-04       | NIC       | 192.168.30.12           | 255.255.255.0   | 192.168.30.1            |
| SW-03       | G0/1      | ---                     | ---             | ---                     |
| RT-02       | G0/1      | 192.168.30.1            | 255.255.255.0   | ---                     |

**Rede 192.168.31.0/24

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| SERVER      | NIC       | 192.168.31.12           | 255.255.255.0   | 192.168.31.1            |
| SW-04       | G0/1      | ---                     | ---             | ---                     |
| RT-02       | G0/1      | 192.168.31.1            | 255.255.255.0   | ---                     |


## Comandos:

~~~~

R1(config)#int s0/0/0
R1(config-if)#no ip access-group 11 out
R1(config-if)exit
R1(config)no access-list 11
R1(config)do show access-list

~~~~
