
---

> **Manual BGP - Regras, Problemas e Seleção de Rotas**
>
> > **Gustavo Pimentel Filgueira**
> > **221006745**

---

# 1 - Problemas Comuns e Soluções

---

## Não recebe rota de mesmo AS

**Problema**:
eBGP bloqueia rotas com o **próprio AS** no caminho

**Solução**:

```bash
neighbor <IP> allowas-in
```

---

## iBGP não propaga para outro iBGP

**Problema**:
Rota aprendida via iBGP **não é reenviada** para outro vizinho iBGP

**Solução**:

* Criar **full mesh**
* Ou usar **route-reflector**:

```bash
neighbor <IP> route-reflector-client
```

---

## Rota recebida via eBGP não alcançável via iBGP

**Problema**:
Next-hop externo não é conhecido internamente

**Solução**:

```bash
neighbor <IP> next-hop-self
```

---

## Sessão iBGP com loopback não sobe

**Problema**:
Loopbacks usados como vizinhos sem configurar origem

**Solução**:

```bash
neighbor <IP> update-source Loopback0
```

---

## Rota esperada não é preferida

**Problema**:
Outra rota é escolhida por critérios internos do BGP

**Soluções**:

```bash
# Peso local (não propagado)
neighbor <IP> weight <VALOR>

# Preferência local (propagada em iBGP)
set local-preference <VALOR>

# Prejuízo via prepend
set as-path prepend <AS> <AS> <AS>
```

---

## Recebendo muitas rotas indesejadas

**Solução**:

```bash
ip prefix-list BLOQUEIO deny <REDE>
ip prefix-list BLOQUEIO permit 0.0.0.0/0 le 32

route-map FILTRO in
 match ip address prefix-list BLOQUEIO

neighbor <IP> route-map FILTRO in
```

---

# 2 - Tabela de Seleção de Melhor Rota BGP

| Ordem | Critério                               | Preferência           |
| ----- | -------------------------------------- | --------------------- |
| 1     | Weight                                 | Maior                 |
| 2     | Local Preference                       | Maior                 |
| 3     | Origem local (network ou redistribute) | Preferida             |
| 4     | AS-PATH                                | Menor número de ASs   |
| 5     | Origin (IGP < EGP < Incomplete)        | IGP preferido         |
| 6     | MED                                    | Menor                 |
| 7     | Tipo da sessão                         | eBGP preferido a iBGP |
| 8     | IGP Metric até next-hop                | Menor                 |
| 9     | Tempo da rota                          | Mais antiga           |
| 10    | Router-ID                              | Menor                 |

---

# 3 - Comandos de Verificação

```bash
show ip bgp summary
show ip bgp
show ip bgp neighbors
show ip bgp neighbors <IP> advertised-routes
show ip bgp neighbors <IP> received-routes
show ip route bgp
```

---

