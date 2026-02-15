# Server Zone Configuration

**IP Address:** 192.168.0.66  
**Subnet Mask:** 255.255.255.192  
**Default Gateway:** 192.168.0.65  
**Preferred DNS:** 192.168.0.66  

---

## DHCP Server Pools

| Pool Name    | Default Gateway | DNS Server    | Start IP      | Subnet Mask       | Max Users |
|-------------|----------------|---------------|--------------|-----------------|-----------|
| serverPool  | 192.168.0.65   | 192.168.0.66  | 192.168.0.67 | 255.255.255.192 | 60        |
| Vertrieb    | 192.168.0.33   | 192.168.0.66  | 192.168.0.34 | 255.255.255.248 | 6         |
| Buchhaltung | 192.168.0.17   | 192.168.0.66  | 192.168.0.18 | 255.255.255.248 | 6         |
| GF          | 192.168.0.41   | 192.168.0.66  | 192.168.0.42 | 255.255.255.248 | 6         |
| HR          | 192.168.0.25   | 192.168.0.66  | 192.168.0.26 | 255.255.255.248 | 6         |
| IT          | 192.168.0.1    | 192.168.0.66  | 192.168.0.2  | 255.255.255.240 | 14        |

---

## DNS Server Records (A Records)

| Hostname           | Type      | IP Address     |
|-------------------|-----------|---------------|
| buchhaltung.jk.de | A Record  | 192.168.0.17  |
| dhcp.jk.de        | A Record  | 192.168.0.66  |
| dns.jk.de         | A Record  | 192.168.0.66  |
| gf.jk.de          | A Record  | 192.168.10.10 |
| hr.jk.de          | A Record  | 192.168.10.10 |
| it.jk.de          | A Record  | 192.168.10.10 |
| jk.de             | A Record  | 192.168.10.10 |
| mail.jk.de        | A Record  | 192.168.10.10 |
| vertrieb.jk.de    | A Record  | 192.168.0.33  |
