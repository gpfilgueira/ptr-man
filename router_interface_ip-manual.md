
---

> **Manual endereçamento de IPs nas interfaces de roteadores - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Plenajamento de IPs

# 2 - Configuração dos roteadores

```bash
enable
configure terminal
interface <Tipo_da_interface> <Número_da_interface>
ip address <IP> <Sub_máscara>
no shutdown
# Repetir em todas as interfaces conectadas de todos os roteadores

# Para deletar ip 
interface <Tipo_da_interface> <Número_da_interface>
no ip address

# Para adicionar descrição para melhor organização
interface <Tipo_da_interface> <Número_da_interface>
description <Descrição>

```

# 3 - Comandos de verificação

## Específicos para configuração dos IPs nas interfaces dos roteadores

```bash
show ip interface brief
shoe running-config | section interface
show interface <Tipo_da_interface> <Número_da_interaface>
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

# 4 - Salvar configurações roteadores

```bash
write memory
```
