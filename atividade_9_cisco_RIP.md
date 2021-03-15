### Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%209.PNG)

### Documentação:

https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2011.PNG

### Comandos:

~~~~

RT-SP

RT-SP>
RT-SP>ena
RT-SP#config t
RT-SP(config)#int g0/0
RT-SP(config-if)#ip add 192.168.1.1 255.255.255.0
RT-SP(config-if)#no shutdown
RT-SP(config-if)#
RT-SP(config-if)#int g0/1
RT-SP(config-if)#ip add 10.0.0.1 255.255.255.252
RT-SP(config-if)#no shutdown
RT-SP(config-if)#
RT-SP(config-if)#router rip
RT-SP(config-router)#version 2
RT-SP(config-router)#no auto-summary
RT-SP(config-router)#network 192.168.1.0
RT-SP(config-router)#network 10.0.0.0
RT-SP(config-router)#passive-interface g0/0
RT-SP(config-router)#

RT-RIO

RT-RIO>ena
RT-RIO#config t
RT-RIO(config)#int g0/0
RT-RIO(config-if)#ip add 10.0.1.1 255.255.255.252
RT-RIO(config-if)#no shutdown

RT-RIO(config-if)#
RT-RIO(config-if)#int g0/1
RT-RIO(config-if)#ip add 10.0.0.2 255.255.255.252
RT-RIO(config-if)#no shutdown

RT-RIO(config-if)#
RT-RIO(config-if)#router rip
RT-RIO(config-router)#version 2
RT-RIO(config-router)#no auto-summary
RT-RIO(config-router)#network 10.0.1.0
RT-RIO(config-router)#network 10.0.0.0

RT-MG

Router>ena
Router#config t
Router(config)#hostname RT-MG
RT-MG(config)#int g0/1
RT-MG(config-if)#ip add 10.0.1.2 255.255.255.252
RT-MG(config-if)#no shutdown

RT-MG(config-if)#
RT-MG(config-if)#int g0/0
RT-MG(config-if)#ip add 10.0.2.1 255.255.255.252
RT-MG(config-if)#no shutdown

RT-MG(config-if)#
RT-MG(config-if)#router rip
RT-MG(config-router)#version 2
RT-MG(config-router)#no auto-summary
RT-MG(config-router)#network 10.0.1.0
RT-MG(config-router)#network 10.0.2.0

RT-BA

Router>
Router>ena
Router#config t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#hostname RT-BA
RT-BA(config)#int g0/1
RT-BA(config-if)#ip add 10.0.2.2 255.255.255.252
RT-BA(config-if)#no shutdown

RT-BA(config-if)#
RT-BA(config-if)#int g0/0
RT-BA(config-if)#ip add 192.168.0.1 255.255.255.0
RT-BA(config-if)#no shutdown

RT-BA(config-if)#
RT-BA(config-if)#router rip
RT-BA(config-router)#version 2
RT-BA(config-router)#no auto-summary
RT-BA(config-router)#network 192.168.0.0
RT-BA(config-router)#network 10.0.2.0
RT-BA(config-router)#passive-interface g0/0
RT-BA(config-router)#

~~~~


