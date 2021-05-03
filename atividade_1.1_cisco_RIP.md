## Aula-03 (atividade 01)

### Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_1.PNG)


### Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP     | MÁSCARA         | GATEWAY PADRÃO |
|-------------|-----------|-----------------|-----------------|----------------|
| PC-00       | NIC       | 192.168.0.1     | 255.255.255.0   | 192.168.0.254 |
| PC-01       | NIC       | 172.16.255.1    | 255.255.255.0   | 192.168.255.254|
| SW-00       | F0/24     | ---             | ---             | ---            |
| SW-01       | FO/24     | ---             | ---             | ---            |
| RT-RSP      | G0/0/0    | 192.168.0.254   | 255.255.255.0   | ---            |
| RT-RSP      | S0/1/0    | 10.0.0.1        | 255.255.255.252 | ---            |
| RT-RINT     | S0/1/1    | 10.0.0.2        | 255.255.255.252 | ---            |
| RT-RINT     | S0/1/0    | 10.0.0.5        | 255.255.255.252 | ---            |
| RT-RJJ      | G0/0/0    | 172.16.255.254  | 255.255.255.0   | ---            |
| RT-RJJ      | S0/1/0    | 10.0.0.6        | 255.255.255.252 | ---            |


### Codigo:
~~~
### RT-RST:
RT-RSP>enable
RT-RSP#config terminal
RT-RSP(config)interface g0/0/0
RT-RSP(config-if)ip address 192.168.0.254 255.255.255.0
RT-RSP(config-if)no shutdown
RT-RSP(config-if)interface s0/1/0
RT-RSP(config-if)ip address 10.0.0.1 255.255.255.252
RT-RSP(config-if)router rip
RT-RSP(config-router)version 2
RT-RSP(config-router)no auto-summary
RT-RSP(config-router)network 192.168.0.0
RT-RSP(config-router)network 10.0.0.0

### RT-RINT:
RT-RINT>enable
RT-RINT#config terminal
RT-RINT(config)interface S0/1/1
RT-RINT(config-if)ip address 1O.0.0.2 255.255.255.252
RT-RINT(config-if)no shutdown
RT-RINT(config-if)interface s0/1/0
RT-RINT(config-if)ip address 10.0.0.5 255.255.255.252
RT-RINT(config-if)router rip
RT-RINT(config-router)version 2
RT-RINT(config-router)no auto-summary
RT-RINT(config-router)network 10.0.0.4
RT-RINT(config-router)network 10.0.0.0

### RT-RJJ:
RT-RJJ>enable
RT-RJJ#config terminal
RT-RJJ(config)interface G0/0/0
RT-RJJ(config-if)ip address 172.16.255.254 255.255.255.0
RT-RJJ(config-if)no shutdown
RT-RJJ(config-if)interface s0/1/0
RT-RJJ(config-if)ip address 10.0.0.6 255.255.255.252
RT-RJJ(config-if)router rip
RT-RJJ(config-router)version 2
RT-RJJ(config-router)no auto-summary
RT-RJJ(config-router)network 10.0.0.4
RT-RJJ(config-router)network 172.17.255.0


~~~








