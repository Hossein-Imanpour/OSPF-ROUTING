# OSPF Routing Project

This project is a network simulation in **Cisco Packet Tracer** where the **OSPF (Open Shortest Path First)** protocol is used for routing between multiple Local Area Networks (LANs).

---

## 🖼️ Network Topology

<img width="1348" height="422" alt="ospf-routing" src="https://github.com/user-attachments/assets/0f418af3-f17a-4a80-9888-ea6b5cf15abf" />

---

## 📌 Network Details
In this project, three LANs are designed and connected through three routers:

- **LAN1 (192.168.10.0/24)**
  - Laptop1 → `192.168.10.1`
  - Gateway (R1) → `192.168.10.100`

- **LAN2 (192.168.20.0/24)**
  - Laptop0 → `192.168.20.1`
  - Gateway (R2) → `192.168.20.10`

- **LAN3 (192.168.30.0/24)**
  - Laptop2 → `192.168.30.1`
  - Gateway (R3) → `192.168.30.10`

---

## 🌐 Router Interfaces

### Router R1
- `Gig0/0/0` → `192.168.100.1`
- `Gig0/0/1` → `192.168.80.1`
- `Gig0/0/2` → `192.168.10.100`

### Router R2
- `Gig0/0/0` → `192.168.100.2`
- `Gig0/0/1` → `192.168.90.1`
- `Gig0/0/2` → `192.168.20.10`

### Router R3
- `Gig0/0/0` → `192.168.80.2`
- `Gig0/0/1` → `192.168.90.2`
- `Gig0/0/2` → `192.168.30.10`

---

## ⚙️ OSPF Configuration
On all three routers, OSPF is enabled with **Process ID = 1**, and the following networks are advertised:

```bash
router ospf 1
 network 192.168.10.0 0.0.0.255 area 0
 network 192.168.20.0 0.0.0.255 area 0
 network 192.168.30.0 0.0.0.255 area 0
 network 192.168.80.0 0.0.0.255 area 0
 network 192.168.90.0 0.0.0.255 area 0
 network 192.168.100.0 0.0.0.255 area 0

```
## ⚙️ STP (Spanning Tree Protocol) Configuration

On the switches in this topology, the **STP protocol** has been enabled in order to:
- Prevent network loops.  
- Establish faster connectivity using **PortFast**.  
- Increase security and control STP traffic on ports using **BPDU Guard**.  

### Example configuration on switches:
```bash
spanning-tree portfast default
spanning-tree bpduguard enable
