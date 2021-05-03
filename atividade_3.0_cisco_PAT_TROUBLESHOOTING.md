## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_20.PNG)

## Documentação:


| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 10.4.10.1               | 255.255.255.0   | 10.4.10.254             |
| PC-02       | NIC       | 10.4.10.2               | 255.255.255.0   | 10.4.10.254             |
| L-01        | NIC       | 10.4.11.1               | 255.255.255.0   | 10.4.11.254             |
| L-02        | NIC       | 10.4.11.2               | 255.255.255.0   | 10.4.11.254             |
| SW-01       | f0/1-3    | ---                     | ---             | ---                     |
| SW-01       | g0/1      | ---                     | ---             | ---                     |
| SW-02       | f0/1-2    | ---                     | ---             | ---                     |
| SW-02       | g0/1      | ---                     | ---             | ---                     |
| RT-01       | g0/0      | 10.4.10.254             | 255.255.255.0   | ---                     |
| RT-01       | g0/1      | 10.4.11.254             | 255.255.255.0   | ---                     |
| RT-01       | S0/0/1    | 10.4.1.2                | 255.255.255.252 | ---                     |
| RT-02       | S0/0/0    | 209.165.76.194          | 255.255.255.240 | ---                     |
| RT-02       | S0/0/1    | 10.4.1.1                | 255.255.255.252 | ---                     |

## Comandos:

~~~
R2#
R2#config t
R2(config)#int s0/0/0
R2(config-if)#no ip nat inside
R2(config-if)#ip nat outside
R2(config-if)#int s0/0/1
R2(config-if)#no ip nat outside
R2(config-if)#ip nat inside
R2(config-if)#exit
R2(config)#do show access-list
Extended IP access list 101
 10 permit ip 10.4.10.0 0.0.0.255 any
R2(config)#ip access-list extended 101
R2(config-ext-nacl)#no 10 permit ip 10.4.10.0 0.0.0.255 any
R2(config-ext-nacl)#do show access-list
Extended IP access list 101
R2(config-ext-nacl)#10 permit ip 10.4.10.0 0.0.1.255 any
R2(config-ext-nacl)#
~~~~
