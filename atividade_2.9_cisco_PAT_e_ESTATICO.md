## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_19.PNG)

## Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 192.168.10.10           | 255.255.255.0   | 192.168.10.1            |
| PC-03       | NIC       | 192.168.30.10           | 255.255.255.0   | 192.168.30.1            |
| PC-04       | NIC       | 209.165.201.14          | 255.255.255.240 | 209.165.201.1           |
| cisco.pka   | NIC       | 209.165.201.30          | 255.255.255.240 | 209.165.201.17          |
| local.pka   | NIC       | 192.168.20.254          | 255.255.255.240 | 192.168.20.1            |
| SW-01       | f0/0      | ---                     | ---             | ---                     |
| SW-02       | f0/0      | ---                     | ---             | ---                     |
| SW-03       | f0/0      | ---                     | ---             | ---                     |
| RT-01       | f0/0      | 192.168.10.1            | 255.255.255.0   | ---                     |
| RT-01       | S0/0/0    | 10.1.1.1                | 255.255.255.252 | ---                     |
| RT-02       | f0/0      | 192.168.20.1            | 255.255.255.0   | ---                     |
| RT-02       | S0/0/0    | 10.1.1.2                | 255.255.255.252 | ---                     |
| RT-02       | S0/0/1    | 10.2.2.1                | 255.255.255.252 | ---                     |
| RT-02       | S0/1/0    | 200.165.200.225         | 255.255.255.240 | ---                     |
| RT-03       | f0/0      | 192.168.30.1            | 255.255.255.0   | ---                     |
| RT-03       | S0/0/1    | 10.2.2.2                | 255.255.255.252 | ---                     |

## Comandos:

~~~
R2>
R2>
R2>ena
R2#config t	
R2(config)#int s0/1/0
R2(config-if)#ip nat outside
R2(config-if)#int s0/0/0
R2(config-if)#ip nat inside
R2(config-if)#int s0/0/1
R2(config-if)#ip nat inside
R2(config-if)#int f0/0
R2(config-if)#ip nat inside
R2(config-if)#exit
R2(config)#ip access-list standard R2NAT
R2(config-std-nacl)#permit 192.168.10.0 0.0.0.255
R2(config-std-nacl)#permit 192.168.20.0 0.0.0.255
R2(config-std-nacl)#permit 192.168.30.0 0.0.0.255
R2(config-std-nacl)#exit
R2(config)#ip nat pool R2POOL 209.165.202.129 209.165.202.129 netmask 255.255.255.252
R2(config)#ip nat inside source list R2NAT pool R2POOL overload
R2(config)#ip nat inside source static 192.168.20.254 209.165.202.130 
R2(config)#

~~~~



