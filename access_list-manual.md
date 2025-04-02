
---

> **Manual Access-List - Protocolos de Transporte e Roteamento**  
>  
>> **Gustavo Pimentel Filgueira**  
>>  
>> **221006745**

---

# 1 - Pré-requisitos

- Topologia física devidamente conectada.
- Interfaces e dispositivos com IPs configurados.
- Identificação clara das redes e IPs que devem ser filtrados ou liberados.

---

# 2 - Configuração de Access-List

As **Access-Lists** (ACLs) são usadas para permitir ou negar tráfego com base em critérios como endereço IP, protocolo, portas, etc. Elas podem ser configuradas como **padrão (standard)** ou **estendida (extended)**.

### **Tipos de ACLs**

1. **Standard ACL**:

   - Filtra apenas pelo endereço IP de origem.

2. **Extended ACL**:
   - Filtra pelo endereço IP de origem e destino, além de portas e protocolos.

---

## **Configuração de ACL Padrão (Standard ACL)**

### Permitir Tráfego de um IP Específico

```bash
enable
configure terminal

access-list 10 permit 192.168.1.1
```

### Negar Todo o Tráfego

```bash
access-list 10 deny any
```

### Aplicar ACL em uma Interface

```bash
interface <INTERFACE>
ip access-group 10 in
```

---

## **Configuração de ACL Estendida (Extended ACL)**

### Permitir Tráfego HTTP de um IP de Origem para um IP de Destino

```bash
enable
configure terminal

access-list 100 permit tcp 192.168.1.1 0.0.0.0 192.168.2.1 0.0.0.0 eq 80
```

### Negar Todo o Tráfego ICMP

```bash
access-list 100 deny icmp any any
```

### Aplicar ACL em uma Interface

```bash
interface <INTERFACE>
ip access-group 100 in
```

---

## **Configuração de ACLs Nomeadas**

### Criar e Configurar ACL Nomeada

```bash
enable
configure terminal

ip access-list extended BLOQUEIO_HTTP
deny tcp any any eq 80
permit ip any any
```

### Aplicar ACL Nomeada em uma Interface

```bash
interface <INTERFACE>
ip access-group BLOQUEIO_HTTP in
```

---

# 3 - Comandos de Verificação

### Verificar ACLs Configuradas

```bash
show access-lists
show ip access-lists
show running-config | section access-list
```

### Testar Conectividade

```bash
ping <IP_DESTINO>
traceroute <IP_DESTINO>
```

---

# 4 - Salvar Configurações no Roteador

```bash
write memory
```
