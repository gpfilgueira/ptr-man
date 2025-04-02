
---

> **Relatório Laboratório 1 - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# 1 - Topologia Física

---

![Topologia](images/topologia1.jpeg "Topologia")

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

# 2 - Configurar Roteadores

---

## Configuração dos IPs das vlans em cada interface e subinterface

```
enable
configure terminal

Hostname R<x>
no ip domain-lookup

interface <Interface ligada ao switch>.<Tag da vlan'1'>
encapsulation dot1Q <Tag da vlan'1'>
ip address 192.168.<Tag da vlan'1'>.1 255.255.255.0

interface <Interface ligada ao switch>.<Tag da vlan'2'>
encapsulation dot1Q <Tag da vlan'2'>
ip address 192.168.<Tag da vlan'2'>.1 255.255.255.0

interface <Interface ligada ao switch>
no ip address
no shutdown
```
  
## Configuração das interfaces ligadas entre os roteadores

```
interface <Interface ligada a um dos outros dois roteadores>
ip address 192.168.0.<x> 255.255.255.252
no shutdown

interface <Interface ligada a o outro roteador>
ip address 192.168.0.<y> 255.255.255.252
no shutdown
```

## Configuração do roteamento de IPs

```
ip routing
ip route 192.168.<tag de uma vlan não ligada ao rotedor>.0 255.255.255.0 <ip da interface que faz o proxímo salto>
# repetir para as 4 vlans que o roteador não conhece
```

<br>
<br>
<br>
<br>

# 3 - Configurar Switches

---

## Criação de todas as vlans

```
login: admin
password:

configure vlan default delete ports all

create vlan VLAN10 tag 10
create vlan VLAN20 tag 20
create vlan VLAN30 tag 30
create vlan VLAN40 tag 40
create vlan VLAN50 tag 50
create vlan VLAN60 tag 60
```

## Configuração das portas com suas respectivas vlans

```
configure vlan VLAN10 add ports 1 tagged
configure vlan VLAN20 add ports 1 tagged
configure vlan VLAN30 add ports 1 tagged
configure vlan VLAN40 add ports 1 tagged
configure vlan VLAN50 add ports 1 tagged
configure vlan VLAN60 add ports 1 tagged

configure vlan <nome VLAN pertencente ao switch> add ports <x> untagged
configure vlan <nome outra VLAN pertencente ao switch> add ports <y> untagged
```

## Configuração dos IPs nas vlans

```
configure vlan <nome VLAN pertencente ao switch> ipaddress 192.168.<tag vlan>.2/24
configure vlan <nome outra VLAN pertencente ao switch> ipaddress 192.168.<tag outra vlan>.2/24
```

## Configuração do switch para permitir o roteamento das vlans e encaminhamento de IPs

```
configure iproute add default 192.168.<tag primeira vlan do switch>.1

enable ipfowarding vlan <nome vlan>
enable ipfowarding vlan <nome outra vlan>
```

<br>

# 4 - Configurar Computadores

---

```
ip 192.168.<tag vlan>.10
```

<br>

# 5 - Salvar

---

### Roteadores cisco

```
writte memory
```

### Switches exos

```
save
```

### VPCS

```
save
```

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

# 6 - Roteamentos estáticos de IP

---

### R1

![R1 IP routing](images/ipR1-lab1.jpeg)

### R2

![R2 IP routing](images/ipR2.1-lab1.jpeg)
![R2 IP routing](images/ipR2.2-lab1.jpeg)

###  R3

![R3 IP routing](images/ipR3-lab1.jpeg)
