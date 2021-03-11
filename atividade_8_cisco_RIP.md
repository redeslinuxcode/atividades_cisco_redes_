### Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2010.PNG)

### Documentação:

| DISPOSITIVO | INTERFACE | ENDEREÇO IP | MASCARA         | GATEWAY PADRÃO |
|-------------|-----------|-------------|-----------------|----------------|
| PC-00       | NIC       | 192.168.1.2 | 255.255.255.0   | 192.168.1.1    |
| PC-01       | NIC       | 192.168.0.2 | 255.255.255.0   | 192.168.0.1    |
| SW-00       | G0/1      | ---         | ---             | ---            |
| SW-01       | G0/1      | ---         | ---             | ---            |
| RT-SP       | G0/0      | 192.168.1.1 | 255.255.255.0   | ---            |
| RT-SP       | G0/1      | 10.0.0.1    | 255.255.255.252 | ---            |
| RT-RIO      | G0/0      | 10.0.1.1    | 255.255.255.252 | ---            |
| RT-RIO      | G0/1      | 10.0.0.2    | 255.255.255.252 | ---            |
| RT-MG       | G0/0      | 192.168.0.1 | 255.255.255.0   | ---            |
| RT-MG       | G0/1      | 10.0.1.2    | 255.255.255.252 | ---            |

### Comandos:

~~~

Router>ena
Router#config t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RT-SP
RT-SP(config)#int g0/0
RT-SP(config-if)#ip add 192.168.1.1 255.255.255.0
RT-SP(config-if)#no shutdown
RT-SP(config-if)#int g0/1
RT-SP(config-if)#ip add 10.0.0.1 255.255.255.252
RT-SP(config-if)#no shutdown
RT-SP(config-if)#router rip
RT-SP(config-router)#version 2
RT-SP(config-router)#no auto-summary
RT-SP(config-router)#network 192.168.1.0
RT-SP(config-router)#network 10.0.0.0
RT-SP(config-router)#passive-interface g0/0


Router>
Router>ena 
Router#config t
Router(config)#hostname RT-RIO
RT-RIO(config)#int g0/1
RT-RIO(config-if)#ip add 10.0.0.2 255.255.255.252
RT-RIO(config-if)#no shutdown
RT-RIO(config-if)#int g0/0
RT-RIO(config-if)#ip add 10.0.1.1 255.255.255.252
RT-RIO(config-if)#no shutdown
RT-RIO(config-if)#router rip
RT-RIO(config-router)#version 2
RT-RIO(config-router)#no auto-summary
RT-RIO(config-router)#network 10.0.0.0
RT-RIO(config-router)#network 10.0.1.0
RT-RIO(config-router)#

Router>
Router>ena
Router#config t
Router(config)#hostname RT-MG
RT-MG(config)#int g0/1
RT-MG(config-if)#ip add 10.0.1.2 255.255.255.252
RT-MG(config-if)#no shutdown
RT-MG(config-if)#int g0/0
RT-MG(config-if)#ip add 192.168.0.1 255.255.255.0
RT-MG(config-if)#no shutdown

RT-MG(config-if)#router rip	
RT-MG(config-router)#version 2
RT-MG(config-router)#no auto-summary
RT-MG(config-router)#network 192.168.0.0
RT-MG(config-router)#network 10.0.1.0
RT-MG(config-router)#passive-interface g0/0
RT-MG(config-router)#

~~~~
