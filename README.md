# 🔒 Cisco ASA Firewall Configuration Project (DMZ, LAN & Internet Access)

## 📌 Project Overview
This project demonstrates how to configure a **Cisco ASA Firewall** to securely connect three zones: **LAN**, **DMZ**, and the **Internet**. The goal is to enforce security policies that allow internal users to access the Internet, while DMZ-hosted services (e.g., web servers) are accessible externally but isolated from the LAN.  

This hands-on setup simulates a real-world enterprise perimeter firewall deployment.

---

## 🛠️ Lab Topology
- **Cisco ASA Firewall** (physical or virtual on GNS3/Packet Tracer)
- **LAN Network** – 192.168.1.0/24  
- **DMZ Network** – 192.168.2.0/24  
- **Outside/Internet** – DHCP/Public IP  
- **Clients/Servers**:
  - Windows/Linux client in LAN
  - Web server in DMZ
 
---

## ⚙️ Step-by-Step Configuration

### 1. Assign Interfaces
```bash
# Inside (LAN)
interface GigabitEthernet0/1
 nameif inside
 security-level 100
 ip address 192.168.1.1 255.255.255.0
 no shutdown

# DMZ
interface GigabitEthernet0/2
 nameif dmz
 security-level 50
 ip address 192.168.2.1 255.255.255.0
 no shutdown

# Outside (Internet)
interface GigabitEthernet0/0
 nameif outside
 security-level 0
 ip address dhcp setroute
 no shutdown

