## Topologia
![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_17.PNG)

## Codigo

~~~
NAT-DINAMICO
ACME-RT>ena
ACME-RT#config t
ACME-RT(config)#int s0/0/0
ACME-RT(config-if)#ip nat outside
ACME-RT(config-if)#int range g0/0-2
ACME-RT(config-if-range)#ip nat inside
ACME-RT(config-if-range)#exit
ACME-RT(config)#ip access-list standard robert
ACME-RT(config-std-nacl)#permit 192.168.0.0 0.0.0.255
ACME-RT(config-std-nacl)#exit
ACME-RT(config)#ip nat pool intervalo-ips 200.0.0.12 200.0.0.21 netmask 255.255.255.0
ACME-RT(config)#ip nat inside source list robert pool intervalo-ips

PAT
ACME-RT(config)#ip access-list standard robert-1
ACME-RT(config-std-nacl)#permit 192.168.1.0 0.0.0.255
ACME-RT(config-std-nacl)#exit
ACME-RT(config)#ip nat pool PAT 200.0.0.1 200.0.0.1 netmask 255.255.255.0
ACME-RT(config)#ip nat inside source list robert-1 pool PAT overload
ACME-RT(config)#

NAT-ESTATICO
#ip nat inside source static 192.168.2.100 200.0.0.3 
ACME-RT(config)#

~~~~
