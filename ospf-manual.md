
---

> **Manual OSPF - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Interfaces e dispositivos com IPs configurados

# 2 - Configuração Roteadores

## Configuração do OSPF em cada Roteador

```bash
enable
configure terminal

router ospf <ID_Processo>
network <NETWORK_ADDRESS> <WILDCARD_MASK> area <AREA_ID>
# Repetir com os devidos parâmetros para cada interface do roteador conectada a algo

int loopback0
ip address <IP/32>
router-id <int loopback ip address>
```

## Configuração de áreas e propagação de rotas

```bash
area <AREA_ID> range <NETWORK> <SUBNET_MASK>
```

### Propagação de uma rota default(padrão) para vizinhos ospf

```bash
ip route 0.0.0.0 0.0.0.0 <ip do próximo salto> #Exemplo
router ospf 1
default-information originate
```

### Propagação de uma rota default(padrão), aprendida dinamicamente, para vizinhos ospf

```bash
router ospf 1
default-information originate
```

# 3 - Comandos de verificação

## Específicos OSPF

```bash
exit
show ip ospf neighbor
show ip ospf database
show ip ospf interface
show ip ospf interface <Interface>
show ip route ospf
show ip ospf
show running config
show running config | include <ospf, network, ???> #Include funciona como grep
show running config | section ospf
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
