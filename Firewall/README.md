# 🔥 Cisco ASA Firewall Configuration

## 📌 Project Overview
This project demonstrates how to configure a **Cisco ASA 5505 Firewall** in **Cisco Packet Tracer** to block communication between two PCs while allowing other traffic. The firewall is configured using **Access Control Lists (ACLs)** to restrict communication based on IP addresses.

---

## 📁 Network Topology
- **PC1**: `192.168.1.10` (Inside Network)
- **PC2**: `192.168.1.20` (Outside Network)
- **ASA Firewall**: Acts as a security device
- **Switch (2960)**: Connects PCs and Firewall
- **Router (Optional)**: For internet simulation

---

## ⚙️ Configuration Steps

### **1️⃣ Configure ASA Firewall Interfaces**
```bash
enable
configure terminal
```
- **Inside Interface:**
  ```bash
  interface GigabitEthernet0/1
  nameif inside
  security-level 100
  ip address 192.168.1.1 255.255.255.0
  no shutdown
  exit
  ```
- **Outside Interface:**
  ```bash
  interface GigabitEthernet0/0
  nameif outside
  security-level 0
  ip address 192.168.2.1 255.255.255.0
  no shutdown
  exit
  ```
- **Set Default Route (Optional)**
  ```bash
  route outside 0.0.0.0 0.0.0.0 192.168.2.254
  ```

---

### **2️⃣ Configure ACL to Block PC1 from Communicating with PC2**
```bash
access-list BLOCK_PC1 extended deny ip host 192.168.1.10 host 192.168.1.20
access-list BLOCK_PC1 extended permit ip any any
```
✅ **First rule:** Blocks all traffic from PC1 (`192.168.1.10`) to PC2 (`192.168.1.20`).  
✅ **Second rule:** Allows all other traffic.

---

### **3️⃣ Apply ACL to Inside Interface**
```bash
access-group BLOCK_PC1 in interface inside
```

---

## 🎯 Testing the Firewall
1. **Ping PC2 from PC1**:
   ```bash
   ping 192.168.1.20
   ```
   ❌ **Ping should fail** (firewall blocks it).
2. **Try accessing other network services**:
   ✅ Other communication should work fine.

---

## 📌 Conclusion
✅ **Cisco ASA Firewall** is successfully configured to block specific IP communication.
✅ **Access Control Lists (ACLs)** enforce security rules.
✅ **Firewall testing confirms the block is working.**



