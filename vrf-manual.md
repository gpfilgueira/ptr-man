
> **Manual VRF com BGP - Protocolos de Transporte e Roteamento**
>
> > **Gustavo Pimentel Filgueira**
> > **221006745**

---

# 1 - Pré-requisitos

* Topologia conectada fisicamente
* Interfaces com IP configurado
* Dispositivos com suporte a VRF (virtual routing and forwarding)
* IP routing ativado

```bash
ip routing
```

---

# 2 - Criação e Associação de VRF

## Opção 1: Usando `ip vrf`

```bash
ip vrf CLIENTE1
 rd 100:1
 route-target export 100:1
 route-target import 100:1

ip vrf CLIENTE2
 rd 200:1
 route-target export 200:1
 route-target import 200:1
```

## Opção 2: Usando `vrf definition`

```bash
vrf definition CLIENTE1
 rd 100:1
 address-family ipv4
  route-target export 100:1
  route-target import 100:1

vrf definition CLIENTE2
 rd 200:1
 address-family ipv4
  route-target export 200:1
  route-target import 200:1
```

## Associar VRF às interfaces

```bash
interface GigabitEthernet0/0
 vrf forwarding CLIENTE1
 ip address <IP> <MASK>

interface GigabitEthernet0/1
 vrf forwarding CLIENTE2
 ip address <IP> <MASK>
```

---

# 3 - Configuração do BGP com VRF

```bash
router bgp <AS_NUMBER>
 address-family ipv4 vrf CLIENTE1
  redistribute connected
  neighbor <IP> remote-as <AS>
  neighbor <IP> activate

 address-family ipv4 vrf CLIENTE2
  redistribute connected
  neighbor <IP> remote-as <AS>
  neighbor <IP> activate
```

---

# 4 - Verificação e Testes

```bash
show ip vrf
show ip route vrf CLIENTE1
show ip bgp vpnv4 all
show ip bgp vpnv4 vrf CLIENTE1
show ip bgp vpnv4 vrf CLIENTE2

ping vrf CLIENTE1 <IP>
traceroute vrf CLIENTE2 <IP>
```

---

# 5 - Salvar configurações no roteador

```bash
write memory
```

