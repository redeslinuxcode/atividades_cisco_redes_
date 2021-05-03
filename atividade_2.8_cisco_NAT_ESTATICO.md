## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_18.PNG)

## Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-01       | NIC       | 10.0.37.205             | 255.255.255.0   | 10.0.37.1               |
| L-01        | NIC       | 192.168.95.108          | 255.255.255.0   | 192.168.95.1            |
| SR-01       | NIC       | 172.16.16.1             | 255.255.255.240 | 172.16.16.14            |
| SW-01       | G0/0      | ---                     | ---             | ---                     |
| RT-01       | S0/0/0    | 192.168.95.108          | 255.255.255.0   | ---                     |
| RT-01       | S0/1/0    | 172.16.16.14            | 255.255.255.240 | ---                     |

## Comandos:

~~~
R1(config)#int s0/0/0
R1(config-if)#ip nat outside
R1(config-if)#int g0/0
R1(config-if)#ip nat inside
R1(config-if)#exit
R1(config)#ip nat inside source static 172.16.16.1 64.100.50.1
~~~

