
---

> **Manual de Endereçamento IP e Sub-redes - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# Tipos de Endereços IP

1. **IPv4**: Um endereço de 32 bits escrito no formato decimal com pontos (por exemplo, 192.168.1.1).
2. **IPv6**: Um endereço de 128 bits escrito no formato hexadecimal, separado por dois-pontos (por exemplo, 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

# Endereçamento IPv4

## Classes de Endereços

Os endereços IPv4 são categorizados em cinco classes:

- **Classe A**: 0.0.0.0 a 127.255.255.255 (Redes grandes)

  - Máscara de Sub-rede Padrão: 255.0.0.0 (/8)
  - Exemplo: 10.0.0.1

- **Classe B**: 128.0.0.0 a 191.255.255.255 (Redes de médio porte)

  - Máscara de Sub-rede Padrão: 255.255.0.0 (/16)
  - Exemplo: 172.16.0.1

- **Classe C**: 192.0.0.0 a 223.255.255.255 (Redes pequenas)

  - Máscara de Sub-rede Padrão: 255.255.255.0 (/24)
  - Exemplo: 192.168.1.1

- **Classe D**: 224.0.0.0 a 239.255.255.255 (Multicast)
- **Classe E**: 240.0.0.0 a 255.255.255.255 (Experimental)

## Faixas de IP Reservados

- **Endereços IP Privados**:

  - Classe A: 10.0.0.0 a 10.255.255.255
  - Classe B: 172.16.0.0 a 172.31.255.255
  - Classe C: 192.168.0.0 a 192.168.255.255

- **Endereço de Loopback**: 127.0.0.1 (Testes e diagnósticos)
- **APIPA**: 169.254.0.0 a 169.254.255.255 (Atribuição automática de IP quando o DHCP não está disponível)

---

# Sub-redes

A segmentação de sub-redes divide uma grande rede em segmentos menores, melhorando o desempenho e a segurança.

### Máscaras de Sub-rede

Uma **máscara de sub-rede** define o limite entre o ID da rede e o ID do host. Ela é escrita em dois formatos:

1. **Decimal com Pontos**: por exemplo, 255.255.255.0
2. **CIDR (Classless Inter-Domain Routing)**: por exemplo, /24

### Máscaras de Sub-rede Comuns

| CIDR | Máscara de Sub-rede | Total de Sub-redes | Hosts por Sub-rede |
| ---- | ------------------- | ------------------ | ------------------ |
| /8   | 255.0.0.0           | 1                  | 16.777.214         |
| /16  | 255.255.0.0         | 256                | 65.534             |
| /24  | 255.255.255.0       | 65.536             | 254                |
| /30  | 255.255.255.252     | 4                  | 2                  |
| /32  | 255.255.255.255     | 1                  | 1                  |

## Exemplo de Sub-redes

Dada uma rede 192.168.1.0/24, para dividi-la em quatro sub-redes:

- Nova Máscara de Sub-rede: /26 (255.255.255.192)
- Sub-redes:
  - 192.168.1.0 - 192.168.1.63
  - 192.168.1.64 - 192.168.1.127
  - 192.168.1.128 - 192.168.1.191
  - 192.168.1.192 - 192.168.1.255

---

# Segmentos de Rede

Segmentos de rede são porções de uma rede separadas por dispositivos como roteadores ou switches.

## Tipos de Segmentação

1. **Segmentação Física**: Utiliza hardware, como switches, para dividir redes.
2. **Segmentação Lógica**: Utiliza VLANs ou sub-redes para criar divisões virtuais.

## Benefícios

- Melhor desempenho da rede
- Maior segurança
- Melhor gerenciamento de tráfego

---

# Quando Usar Sub-redes Específicas

## Escritórios Pequenos/Residenciais (SOHO)

- **CIDR**: /24 (por exemplo, 192.168.1.0/24)
- **Razão**: Suporta até 254 dispositivos, suficiente para ambientes pequenos.

## Empresas de Médio Porte

- **CIDR**: /22 (por exemplo, 192.168.4.0/22)
- **Razão**: Equilibra utilização e gerenciamento do espaço IP.

## Links Ponto-a-Ponto

- **CIDR**: /30 ou /31
- **Razão**: Requisitos mínimos de host reduzem o desperdício de IPs.

## Loopbacks ou IDs

- **CIDR**: /32 (por exemplo, 1.1.1.1/32)
- **Razão**: Apenas um IP é necessário para a sub-rede.

---

## Melhores Práticas para Endereçamento IP

1. **Planeje o Esquema de IP**:

   - Utilize IPs privados para redes internas.
   - Reserve IPs para dispositivos críticos (por exemplo, servidores, roteadores).

2. **Documente o Endereçamento**:

   - Mantenha um registro dos endereços atribuídos.

3. **Use DHCP para Atribuições Dinâmicas**:

   - Simplifica o gerenciamento para redes grandes.

4. **Monitore e Audite**:
   - Verifique regularmente conflitos e IPs não utilizados.


