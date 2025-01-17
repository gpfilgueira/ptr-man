
---

> **Manual BGP - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Interfaces e dispositivos com IPs configurados

# 2 - Configuração Roteadores

## Configuração do BGP em cada Roteador

```bash
enable
configure terminal

router bgp <AS_NUMBER>
network <NETWORK> mask <SUBNET_MASK>
neighbor <IP_ADDRESS> remote-as <AS_NUMBER>

# (Opcional) Descrição de vizinho
neighbor <IP_ADDRESS> description <TEXT>
```
# 3 - Comandos de verificação

## Específicos BGP 

```bash
exit
show ip bgp
show ip bgp summary
show ip prefix-list
show ip route
show ip route bgp
show ip bgp <NETWORK>
show ip bgp neighbors <NEIGHBOR_IP>
show ip bgp neighbors <NEIGHBOR_IP> advertised-routes
show ip bgp neighbors <NEIGHBOR_IP> received-routes
show running-config | section router bgp
show logging
show ip bgp filtered
show route-map
debug ip bgp
clear ip bgp <NEIGHBOR_IP>
clear ip bgp *
```

## Gerais

```bash
show running config
show running config | <>
show startup-config
show ip route
show ip route <ip>

show ip interface brief
show running config | section <interface>
show interface <interface>

ping <ip>
traceroute <ip> #nos VPCS trace

# Opções de pipe 
|include <keyword>
|exclude <keyword>
|begin <keyword>
|section <keyword>
```

# 4 - Salvar configurações no roteador

```bash
write memory
```
