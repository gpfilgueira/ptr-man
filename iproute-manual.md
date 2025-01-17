
---

> **Manual Roteamento estático de IPs - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Interfaces e dispositivos com IPs configurados

# 2 - Configuração Roteadores

## Configuração do roteamento de IPs

```
ip routing
ip route <REDE_DESTINO> <SUB_MÁSCARA> <IP_OU_INTERFACE_DO_PRÓXIMO_SALTO>
# Repetir para todos os destinos que o roteador deve conhecer
```

## Outros comandos

```
# Remover rota
no ip route <REDE_DESTINO> <SUB_MÁSCARA> <IP_OU_INTERFACE_DO_PRÓXIMO_SALTO>
ip route 0.0.0.0 0.0.0.0 <IP_OU_INTERFACE_DO_PRÓXIMO_SALTO>
```
# 3 - Comandos de verificação

## Específicos para roteamento estático de IP

```bash
show ip route
show ip route <ip>

show running-config | include ip route
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

# 4 - Salvar configurações nos roteadores

```bash
write memory
```
