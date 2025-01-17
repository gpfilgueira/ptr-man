
---

> **Manual OSPF Redistribute - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada
- Interfaces e dispositivos com IPs configurados
- OSPF devidamente configurado em todos os roteadores

# 2 - Configuração Roteadores

## Configuração do OSPF em cada Roteador

```bash
enable
configure terminal

router ospf <ID_Processo>
redistribute <PROTOCOL> [<PROCESS_ID>] [metric <VALUE>] [subnets]
```

## Exemplos de configurações

### Redistribuir rotas conectadas

```bash
router ospf 1
redistribute connected subnets
```

### Redistribuir rotas estaáticas

```bash
router ospf 1
redistribute static subnets metric 10
```

### Redistribuir rotas RIP

```bash
router ospf 1
redistribute rip subnets
```

### Redistribuir rotas BGP

```bash
router ospf 1
redistribute bgp 65001 subnets metric 20
```

### Redistribuir rotas EIGRP

```bash
router ospf 1
redistribute eigrp 100 subnets metric 20
```

### Usar Route-Maps para filtrar rotas

```bash
route-map FILTER_STATIC permit 10
 match ip address 1
 set metric 5

access-list 1 permit 192.168.1.0 0.0.0.255

router ospf 1
redistribute static subnets route-map FILTER_STATIC
```

# 3 - Comandos de verificação

## Específicos OSPF

```bash
exit
show ip route ospf
show ip ospf neighbor
show ip ospf database
show running-config | section router ospf
debug ip ospf redistribute
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
