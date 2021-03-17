## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2015.PNG)

## Documentação

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-00       | NIC       | 192.168.20.3            | 255.255.255.0   | 192.168.20.1            |
| PC-01       | NIC       | 192.168.20.4            | 255.255.255.0   | 192.168.20.1            |
| PC-02       | NIC       | 192.168.10.3            | 255.255.255.0   | 192.168.10.1            |
| SW-00       | F0/1-2    | ---                     | ---             | ---                     |
| SW-01       | F0/1-3    | ---                     | ---             | ---                     |
| SW-02       | F0/1-2    | ---                     | ---             | ---                     |
| SW-03       | F0/1-2    | ---                     | ---             | ---                     |
| RT-01       | F0/0      | 192.168.100.1           | 255.255.255.0   | ---                     |
| RT-01       | F0/1      | 192.168.200.1           | 255.255.255.0   | ---                     |
| RT-01       | E0/0/0    | 192.168.10.1            | 255.255.255.0   | ---                     |
| RT-01       | E0/1/0    | 192.168.20.1            | 255.255.255.0   | ---                     |


## Comandos:

~~~~

R1(config)# ip access-list standard File_Server_Restrictions
R1(config-std-nacl)# permit host 192.168.20.4
R1(config-std-nacl)# deny any
R1(config)#exit
R1(config)#int f0/0
R1(config-if)# ip access-group File_Server_Restrictions out

~~~
