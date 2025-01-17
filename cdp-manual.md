
---

> **Manual CDP - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Interfaces e dispositivos com IPs configurados

# 2 - Configuração Roteadores

## Configuração do CDP globalmente

```bash
enable
configure terminal

# Habilita CDP globalmente no roteador
cdp run

# Para desabilitar
no cdp run
```

## Configuração CDP por interfaces

```bash
# Habilita
interface <INTERFACE_ID>
cdp enable

# Desabilita
interface <INTERFACE_ID>
no cdp enable
```

# 3 - Comandos de verificação

## Específicos CDP 

```bash
exit
show cdp
show cdp neighbors
show cdp traffic
show cdp neighbors detail
show running config
show running config | include <cdp, protocols> #Include funciona como grep
show running config | section cdp 
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
