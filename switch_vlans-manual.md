
---

> **Manual Vlans em switches - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Planejamento de endereçamento de IPs
- Conexão dos switches a dispositivos de camada 3

# 2 - Configuração dos switches

## Criação das vlans

```bash
vlan <ID_da_VLAN>
name <Nome_da_VLAN>
```

## Atribuição das portas às VLANs

```bash
interface <Interface_do_switch>
switchport mode access
switchport access vlan <ID_da_VLAN>
```

## Configuração das portas trunk

```bash
interface <Interface_do_switch>
switchport mode trunk
switchport trunk allowed vlan <Lista_das_VLANs_permitidas>
```

# 3 - Comandos de verificação

## Específicos vlans em switches

```bash
show vlan
show vlan brief
show interfaces status
show interfaces trunk
show spanning-tree #Se estiver usando STP
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

# 4 - Salvar configurações switches

```bash
save
# Ou
copy running-config startup-config
# Ou
write memory
```
