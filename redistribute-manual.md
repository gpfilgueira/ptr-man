
---

> **Manual Redistribute - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada.
- Interfaces e dispositivos com IPs configurados.
- Protocolo de roteamento configurado (OSPF, EIGRP, RIP, etc.) e/ou rotas estáticas aplicadas nos roteadores.

# 2 - Configuração Roteadores

## Configuração do comando `redistribute` em cada roteador

O comando `redistribute` permite a redistribuição de rotas aprendidas de um protocolo de roteamento para outro, ou a redistribuição de rotas estáticas.

### Exemplos Gerais de Configuração:

#### Redistribuindo rotas OSPF em BGP

```bash
enable
configure terminal

router bgp <AS_NUMBER>
redistribute ospf
```

#### Redistribuindo rotas estáticas em OSPF

```bash
enable
configure terminal

router ospf <PROCESS_ID>
redistribute static subnets
```

#### Redistribuindo EIGRP em OSPF

```bash
enable
configure terminal

router ospf <PROCESS_ID>
redistribute eigrp <AS_NUMBER>
```

#### Redistribuindo rotas entre dois processos OSPF

```bash
enable
configure terminal

router ospf <PROCESS_ID_1>
redistribute ospf <PROCESS_ID_2> subnets metric-type <TYPE>
```

#### Redistribuindo Redes Conectadas para OSPF
```bash
enable
configure terminal

router ospf 1
redistribute connected subnets
```

#### Redistribuindo Redes Conectadas para BGP
```bash
enable
configure terminal

router bgp 65001
redistribute connected metric 10 route-map FILTER_CONNECTED
```

### Explicação dos Parâmetros

- **`metric`**: Define a métrica usada nas rotas redistribuídas.
- **`metric-type`**: Define o tipo de métrica no OSPF (1 para cumulativa, 2 para estática).
- **`subnets`**: Redistribui redes que não sejam de classe padrão (CIDR).
- **`route-map`**: Aplica filtros ou define modificações nas rotas redistribuídas.
- **`match`**: Define critérios como listas de acesso ou prefixos para selecionar rotas.
- **`set`**: Modifica atributos das rotas redistribuídas, como a métrica.

# 3 - Comandos de verificação

## Comandos Específicos

```bash
show ip route
show ip route ospf
show ip route eigrp
show ip route bgp
show ip protocols
show running-config | section router
show ip ospf border-routers
show ip bgp redistributed
```

## Comandos Gerais

```bash
show running-config
show ip interface brief
ping <IP>
traceroute <IP>
```

# 4 - Salvar configurações no roteador

```bash
write memory
```

--- 

Essa estrutura cobre as principais utilizações do comando `redistribute` e pode ser adaptada conforme necessário para configurações mais específicas.
