## Topologia:

![](https://github.com/redeslinuxcode/atividades_cisco_redes_/blob/main/cisco/topologia%2016.PNG)

## Documentação:

| Dispositivo  | Interface    | Endereço IP   | Máscara de sub-rede | Gateway Padrão|
|--------------|--------------|---------------|---------------------|---------------|
| R1           | G0/0         | 192.168.10.1  | 255.255.255.0       | N/D           |
|              | G0/1         | 192.168.11.1  | 255.255.255.0       | N/D           |
|              | S0/0/0       | 10.1.1.1      | 255.255.255.252     | N/D           |
|              | S0/0/1       | 10.3.3.1      | 255.255.255.252     | N/D           |
| R2           | G0/0         | 192.168.20.1  | 255.255.255.0       | N/D           |
|              | S0/0/0       | 10.1.1.2      | 255.255.255.252     | N/D           |
|              | S0/0/1       | 10.2.2.1      | 255.255.255.252     | N/D           |
| R3           | G0/0         | 192.168.30.1  | 255.255.255.0       | N/D           |
|              | S0/0/0       | 10.3.3.2      | 255.255.255.252     | N/D           |
|              | S0/0/1       | 10.2.2.2      | 255.255.255.252     | N/D           |
| PC1          | NIC          | 192.168.10.10 | 255.255.255.0       | 192.168.10.1  |
| PC2          | NIC          | 192.168.11.10 | 255.255.255.0       | 192.168.11.1  |
| PC3          | NIC          | 192.168.30.10 | 255.255.255.0       | 192.168.30.1  |
| Servidor Web |Placa de rede | 192.168.20.254| 255.255.255.0       |192.168.20.1   |

·         Um ping de 192.168.10.10 a 192.168.11.10 é confirmado.

·         Um ping de 192.168.10.10 a 192.168.20.254 é confirmado.

·         Um ping de 192.168.11.10 a 192.168.20.254 falha.

·         Um ping de 192.168.10.10 a 192.168.30.10 falha.

·         Um ping de 192.168.11.10 a 192.168.30.10 é confirmado.

·         Um ping de 192.168.30.10 a 192.168.20.254 é confirmado.

## Comandos:

~~~~

RT-03
R3#ena
R3#config t
R3(config)#access-list 1 deny 192.168.10.0 0.0.0.255
R3(config)#access-list 1 pemit any
R3(config)#access-list 1 permit any
R3(config)#int g0/0
R3(config-if)#ip access-group 1 out

RT-02
R2#ena
R2#config t
R2(config)#access-list 1 deny 192.168.11.0 0.0.0.255
R2(config)#access-list 1 permit any
R2(config)#int g0/0
R2(config-if)#ip access-group 1 out
R2(config-if)#

~~~
