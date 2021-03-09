### topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%205.PNG)

### Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|-------------|-----------|-------------------------|-----------------|-------------------------|
| PC-20       | NIC       | 2001:DB8:5EA1:B2B2::1   | /64             | 2001:DB8:5EA1:B2B2::128 |
| PC-30       | NIC       | 2001:DB8:5EA1:B3B3::1   | /64             | 2001:DB8:5EA1:B3B3::128 |
| SW-02       | G0/1      | ---                     | ---             | ---                     |
| SW-03       | G0/1      | ---                     | ---             | ---                     |
| RT-01       | G0/0/0    | 2001:DB8:5EA1:B3B3::128 | /64             | ---                     |
| RT-01       | S0/1/1    | 2001:DB8:DA:2::1        | /64             | ---                     |
| RT-02       | G0/0/0    | 2001:DB8:5EA1:B2B2::128 | /64             | ---                     |
| RT-02       | S0/1/1    | 2001:DB8:DA:2::2        | /64             | ---                     |

### Codigo:
~~~
RT-01>ena
RT-01#config t
RT-01(config-if)#int g0/0/0
RT-01(config-if)#ipv6 add 2001:db8:5ea1:b2b2::128/64
RT-01(config-if)#ipv6 rip ntw enable
RT-01(config-if)#no shutdown

RT-01(config-if)#int S0/1/1
RT-01(config-if)#ipv6 add 2001:db8:da:2::1/64
RT-01(config-if)#ipv6 rip ntw enable
RT-01(config-if)#no shutdown

RT-01>ena
RT-02#config t
RT-02(config-if)#int g0/0/0
RT-02(config-if)#ipv6 add 2001:db8:5ea1:b3b3::128/64
RT-02(config-if)#ipv6 rip ntw enable
RT-02(config-if)#no shutdown

RT-02(config-if)#int S0/1/0
RT-02(config-if)#ipv6 add 2001:db8:da:2::2/64
RT-02(config-if)#ipv6 rip ntw enable
RT-02(config-if)#no shutdown
 ~~~
