## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2021.PNG)

## Documentação:

| DISPOSITIVO  | INTERFACE | ENDEREÇO IP             | MÁSCARA         | GATEWAY PADRÃO          |
|--------------|-----------|-------------------------|-----------------|-------------------------|
| PC-00        | NIC       | 200.1.0.1               | 255.255.255.0   | 200.1.0.254             |
| server-pt    | NIC       | 200.0.0.1               | 255.255.255.0   | 200.0.0.254             |
| RT-tim       | g0/0/0    | 200.1.0.254             | 255.255.255.0   | ---                     |
| RT-tim       | S0/1/0    | 189.190.190.1           | 255.255.255.252 | ---                     |
| RT-vivo      | s0/1/0    | 189.190.190.2           | 255.255.255.252 | ---                     |
| RT-vivo      | S0/1/1    | 189.190.191.1           | 255.255.255.252 | ---                     |
| RT-vivo2     | S0/1/1    | 189.190.191.2           | 255.255.255.252 | ---                     |
| RT-vivo2     | S0/1/0    | 189.190.192.1           | 255.255.255.252 | ---                     |
| RT-cli       | s0/1/0    | 189.190.192.2           | 255.255.255.0   | ---                     |
| RT-cli       | g0/0/0    | 200.0.0.254             | 255.255.255.252 | ---                     |

## Comandos:

~~~~
router tim
Router>ena
Router#config t
Router(config)#int g0/0/0
Router(config-if)#ip add 200.1.0.254 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#int s0/1/0
Router(config-if)#ip add 189.190.190.1 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#exit
Router(config)#router bgp 13200
Router(config-router)#network 200.1.0.0 mask 255.255.255.0
Router(config-router)#network 189.190.190.0 mask 255.255.255.252
Router(config-router)#neighbor 189.190.190.2 remote-as 13201


router vivo1
Router>ena
Router#config t
Router(config)#int s0/1/0
Router(config-if)#ip add 189.190.190.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#int s0/1/1
Router(config-if)#ip add 189.190.191.1 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#router bgp 13201
Router(config-router)#network 189.190.190.0 mask 255.255.255.252
Router(config-router)#network 189.190.191.0 mask 255.255.255.252
Router(config-router)#neighbor 189.190.190.1 remote-as 13200
Router(config-router)#neighbor 189.190.191.2 remote-as 13202



vivo2
Router>ena
Router#config t
Router(config)#int s0/1/0
Router(config-if)#ip add 189.190.192.1 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#int s0/1/1
Router(config-if)#ip add 189.190.191.2 255.255.255.252
Router(config-if)#no shutdown
Router(config)#router bgp 13202
Router(config-router)#network 189.190.191.0 mask 255.255.255.252
Router(config-router)#network 189.190.192.0 mask 255.255.255.252
Router(config-router)#neighbor 189.190.191.1 remote-as 13201
Router(config-router)#neighbor 189.190.192.2 remote-as 20000

vivo cli
ena
Router#config t
Router(config)#int s0/1/0
Router(config-if)#ip add 189.190.192.2 255.255.255.252
Router(config-if)#no shutdown
Router(config-if)#int g0/0/0
Router(config-if)#ip add 200.0.0.254 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit
Router(config)#router bgp 20000
Router(config-router)#network 189.190.192.0 mask 255.255.255.252
Router(config-router)#network 200.0.0.0 mask 255.255.255.00
Router(config-router)#neighbor 189.190.192.1 remote-as 13202 
~~~~
