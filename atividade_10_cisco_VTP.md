## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia_1.PNG)

## Documentação:






## Codigo:

~~~

sw-1

S1>ena
S1#config t
S1(config)#vlan 99
S1(config-vlan)#vlan 999
S1(config-vlan)#vlan 10
S1(config-vlan)#name Red
S1(config-vlan)#vlan 20
S1(config-vlan)#name Blue
S1(config-vlan)#vlan 30 
S1(config-vlan)#name Yellow
S1(config-vlan)#int range g0/1-2
S1(config-if-range)#switchport trunk native vlan 999
S1(config-if-range)#switchport mode trunk
S1(config-if-range)#exit
S1(config)#int g0/1
S1(config-if)#switchport mode dynamic desirable
S1(config-if)#vtp mode server
S1(config)#vtp domain CCNA
S1(config)#vtp password cisco

sw-2

S2>en
S2#config t
S2(config)#int g0/1
S2(config-if)#switchport mode dynamic desirable
S2(config-if)#switchport mode trunk
S2(config-if)#switchport trunk native vlan 999
S2(config-if)#vtp mode client
S2(config)#vtp domain CCNA
S2(config)#vtp password cisco
S2(config)#int range f0/1-8
S2(config-if-range)#switchport mode access
S2(config-if-range)#switchport acces vlan 10
S2(config-if-range)#
S2(config-if-range)#int range f0/9-16
S2(config-if-range)#switchport mode access
S2(config-if-range)#switchport access vlan 20
S2(config-if-range)#
S2(config-if-range)#int range f0/17-24 
S2(config-if-range)#switchport mode access
S2(config-if-range)#switchport access vlan 30

sw-3
S3>ena
S3#config t
S3(config)#int g0/2
S3(config-if)#switchport mode trunk
S3(config-if)#switchport trunk native vlan 999
S3(config-if)#
S3(config-if)#vtp mode transparent
S3(config)#vtp domain CCNA
S3(config)#vtp password cisco
S3(config)#
S3(config)#int range f0/1-8
S3(config-if-range)#switchport mode access
S3(config-if-range)#switchport acces vlan 10
S3(config-if-range)#
S3(config-if-range)#int range f0/9-16
S3(config-if-range)#switchport mode access
S3(config-if-range)#switchport access vlan 20
S3(config-if-range)#
S3(config-if-range)#int range f0/17-24 
S3(config-if-range)#switchport mode access
S3(config-if-range)#switchport access vlan 30%

~~~
