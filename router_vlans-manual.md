
---

> **Manual Vlans em roteadores - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Plano de endereçamento de IPs
- Configuração dos switches conectados com as vlans

# 2 - Configuração dos roteadores

## Sintaxe para configuração das interfaces que só suportam uma vlan)

```bash
interface <Interface_do_roteador>
ip address <IP> <Sub_máscara>

# Opcional descrição da interface
interface <Interface_do_roteador>
description Conexão à VLAN X
```

## Sintaxe para configuração das subinterfaces (múltiplas vlans)

```bash
interface <Interface_do_roteador>.<Tag_da_vlan>
encapsulation dot1Q <Tag_da_vlan>
ip address <IP> <Sub_máscara>
interface <Interface_que_contém_as_subinterfaces>
no ip address
no shutdown
# Repetir para todas as subinterfaces em todas as interfaces necessárias em todos os roteadores
```

# 3 - Comandos de verificação

## Específicos vlans em roteadores

```bash
show ip interface brief
show running-config | section interface
show ip route
show interfaces <Interface>.<tag_da_vlan>
show ip arp
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
| include <keyword>
| exclude <keyword>
| begin <keyword>
| section <keyword>
```

# 4 - Salvar configurações Roteadores

```bash
write memory
```
