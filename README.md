# A Small Enterprise Network Design (Cisco IOS Simulation)

## Overview

This project simulates a small enterprise network infrastructure using Cisco IOS devices.  
The topology demonstrates VLAN-based segmentation, Layer 3 switching, 802.1Q trunking, DMZ architecture, ACL-based firewall policies, and secure remote management via SSH.

The objective of this lab is to model a structured and security-oriented enterprise network.

---

## Network Architecture

### Core Components

- **Core Layer 3 Switch**
  - Performs Inter-VLAN Routing
  - Acts as default gateway for internal VLANs
  - Provides DHCP relay functionality

- **Access Layer 2 Switch**
  - Provides end-device connectivity
  - Uses 802.1Q trunk to Core Switch

- **Internal Router**
  - Connects Server Zone and DMZ
  - Provides static routing between internal network and edge firewall

- **Edge Router**
  - Internet Gateway
  - Implements ACL-based firewall policies
  - Controls inbound/outbound traffic
  - NAT (Network Address Translation) configured for internet access

---
## Network Zones

### Internal Network
192.168.0.0/24  
Segmented via VLANs.

### Server Zone
192.168.0.64/26  
- DNS / DHCP Server: 192.168.0.66  
- Default Gateway: 192.168.0.65  

### DMZ Zone
192.168.10.0/28  
- Public Server: 192.168.10.10  
- Gateway (Edge Router): 192.168.10.1  
---

## VLAN Segmentation

The internal network (192.168.0.0/24) is segmented into multiple VLANs for security and department isolation.

| VLAN | Department  | Subnet              | Gateway        |
|------|------------|--------------------|---------------|
| 10   | IT         | 192.168.0.0/28     | 192.168.0.1   |
| 20   | HR         | 192.168.0.24/29    | 192.168.0.25  |
| 30   | Management | 192.168.0.40/29    | 192.168.0.41  |
| 40   | Sales      | 192.168.0.32/29    | 192.168.0.33  |
| 50   | Accounting | 192.168.0.16/29    | 192.168.0.17  |

Each VLAN is implemented as a Switch Virtual Interface (SVI) on the Layer 3 switch.

---

## Trunking Design

VLAN traffic is transported between switches using IEEE 802.1Q trunking.

**Core Switch ↔ Access Switch**
- Interface: GigabitEthernet0/1
- Mode: trunk
- Encapsulation: dot1Q
- Allowed VLANs: 10,20,30,40,50

This ensures proper VLAN tagging and separation across switching layers.


---

## Security Implementation

- VLAN segmentation for department isolation
- Inter-VLAN routing on Layer 3 switch
- ACL-based firewall on Edge Router
- Restricted SSH access (IT VLAN only)
- Encrypted remote management (RSA 2048, SSH v2)
- DMZ isolation for public-facing services

---

## Implemented Services

- DHCP (centralized, with relay agent)
- DNS server
- HTTP web server (DMZ)
- Mail server (DMZ)
- Secure device management via SSH

---

## Technologies Used

- Cisco IOS CLI
- VLAN & 802.1Q Trunking
- Inter-VLAN Routing
- Static Routing
- Access Control Lists (ACL)
- DHCP Relay
- NAT (PAT / Static NAT)
- SSH v2 with RSA encryption

---

## Future Improvements

- Replace static routing with OSPF
- Introduce stateful firewall inspection
- Add redundancy (HSRP / VRRP)
- Implement centralized logging (Syslog)
