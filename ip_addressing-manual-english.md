
---

> **IP Addressing and Subnetting Manual - Protocolos de Transporte e Roteamento**
>
>> **Gustavo Pimentel Filgueira**
>>
>> **221006745**

---

# Types of IP Adresses

1. **IPv4**: A 32-bit address written in dotted decimal format (e.g., 192.168.1.1).
2. **IPv6**: A 128-bit address written in hexadecimal format, separated by colons (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).

# IPv4 Addressing

## Address Classes

IPv4 addresses are categorized into five classes:

- **Class A**: 0.0.0.0 to 127.255.255.255 (Large networks)

  - Default Subnet Mask: 255.0.0.0 (/8)
  - Example: 10.0.0.1

- **Class B**: 128.0.0.0 to 191.255.255.255 (Medium-sized networks)

  - Default Subnet Mask: 255.255.0.0 (/16)
  - Example: 172.16.0.1

- **Class C**: 192.0.0.0 to 223.255.255.255 (Small networks)

  - Default Subnet Mask: 255.255.255.0 (/24)
  - Example: 192.168.1.1

- **Class D**: 224.0.0.0 to 239.255.255.255 (Multicasting)
- **Class E**: 240.0.0.0 to 255.255.255.255 (Experimental)

## Reserved IP Ranges

- **Private IP Addresses**:

  - Class A: 10.0.0.0 to 10.255.255.255
  - Class B: 172.16.0.0 to 172.31.255.255
  - Class C: 192.168.0.0 to 192.168.255.255

- **Loopback Address**: 127.0.0.1 (Testing and diagnostics)
- **APIPA**: 169.254.0.0 to 169.254.255.255 (Automatic IP assignment when no DHCP is available)

---

# Subnetting

Subnetting divides a large network into smaller segments, improving performance and security.

### Subnet Masks

A **subnet mask** defines the boundary between the network ID and host ID. It is written in two formats:

1. **Dotted Decimal**: e.g., 255.255.255.0
2. **CIDR (Classless Inter-Domain Routing)**: e.g., /24

### Common Subnet Masks

| CIDR | Subnet Mask     | Total Subnets | Hosts per Subnet |
| ---- | --------------- | ------------- | ---------------- |
| /8   | 255.0.0.0       | 1             | 16,777,214       |
| /16  | 255.255.0.0     | 256           | 65,534           |
| /24  | 255.255.255.0   | 65,536        | 254              |
| /30  | 255.255.255.252 | 4             | 2                |
| /32  | 255.255.255.255 | 1             | 1                |

## Subnetting Example

Given a network 192.168.1.0/24, to divide it into four subnets:

- New Subnet Mask: /26 (255.255.255.192)
- Subnets:
  - 192.168.1.0 - 192.168.1.63
  - 192.168.1.64 - 192.168.1.127
  - 192.168.1.128 - 192.168.1.191
  - 192.168.1.192 - 192.168.1.255

---

# Network Segments

Network segments are portions of a network separated by devices such as routers or switches.

## Types of Segmentation

1. **Physical Segmentation**: Uses hardware like switches to divide networks.
2. **Logical Segmentation**: Uses VLANs or subnets to create virtual divisions.

## Benefits

- Improved network performance
- Enhanced security
- Better traffic management

---

# When to Use Specific Subnets

## Small Office/Home Office (SOHO)

- **CIDR**: /24 (e.g., 192.168.1.0/24)
- **Reason**: Supports up to 254 devices, sufficient for small environments.

## Medium-Sized Business

- **CIDR**: /22 (e.g., 192.168.4.0/22)
- **Reason**: Balances IP space utilization and management.

## Point-to-Point Links

- **CIDR**: /30 or /31
- **Reason**: Minimal host requirements reduce IP wastage.

## Loopbacks or IDs

- **CIDR**: /32 (e.g., 1.1.1.1/32)
- **Reason**: Only one IP for subnet necessary

---

## Best Practices for IP Addressing

1. **Plan the IP Scheme**:

   - Use private IPs for internal networks.
   - Reserve IPs for critical devices (e.g., servers, routers).

2. **Document the Addressing**:

   - Maintain a record of assigned addresses.

3. **Use DHCP for Dynamic Assignments**:

   - Simplifies management for large networks.

4. **Monitor and Audit**:
   - Regularly check for conflicts and unused IPs.
