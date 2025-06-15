
---

> **Relatório Laboratório 2 - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Topologia física

---

![Topologia](images/topologia2.jpeg "Topologia")

# 2 - Configuração Roteadores

---

## Configuração das interfaces com os IPs correspondentes à tabela

```
enable
configure terminal

Hostname R<x>

interface <Interface ligada a um dos roteadores>
ip address 192.168.<a>.<b> 255.255.255.252
no shutdown

interface <Interface ligada a o outro roteador>
ip address 192.168.<c>.<d> 255.255.255.252
no shutdown

```

## Configuração do OSPF em cada Roteador

### Roteador 1

```
router ospf 1 
network 192.168.1.1 0.0.0.3 area 0
network 192.168.2.1 0.0.0.3 area 0
network 192.168.5.1 0.0.0.255 area 2
```

### Roteador 2

```
router ospf 1 
network 192.168.1.2 0.0.0.3 area 0
network 192.168.3.1 0.0.0.3 area 0
network 192.168.4.1 0.0.0.3 area 1
```

### Roteador 3

```
router ospf 1 
network 192.168.2.2 0.0.0.3 area 0
```

### Roteador 4

```
router ospf 1 
network 192.168.4.2 0.0.0.3 area 1
```

## Configuração de áreas e propagação de rotas

### Roteador 1

```
ip route 0.0.0.0 0.0.0.0 192.168.5.1
router ospf 1
default-information originate

router ospf 1
area 1 range 192.168.5.0 255.255.255.252
```

### Roteador 2

```
router ospf 1
area 1 range 192.168.4.1 255.255.255.252
area 1 range 192.168.5.0 255.255.255.0
```

### Roteador 4

```
router ospf 1
default-information originate
```

# 3 - Configuração Computador (simulando uma conexão da estrutura a uma rede externa)

---

### VPCS

```
ip 192.168.5.10 255.255.255.0 192.168.5.1
```

# 4 - Salvar

---

### Roteadores cisco

```
writte memory
```

### VPCS

```
save
```

# 5 - Imagens dos testes

---

## Traceroute feitos do host 192.168.5.10 (pc ligado ao roteador 1 para simular conexão à rede externa) para 192.168.4.2 (Interface do Roteador 4 ligada ao Roteador 3)

### Com a topologia funcionando normalmente

![traceroute1](images/traceroute1-lab2.jpeg )

### Com a interface que liga R1 a R2 desligada

![traceroute2](images/traceroute2-lab2.jpeg )
