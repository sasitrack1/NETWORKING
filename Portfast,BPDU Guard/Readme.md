# Cisco Packet Tracer: PortFast and BPDU Guard Configuration

This project demonstrates the configuration and behavior of **PortFast** and **BPDU Guard** in a switched network environment using **Cisco Packet Tracer**.

## 📘 Overview

PortFast and BPDU Guard are features used to protect the spanning-tree topology and speed up port transitions on access ports in Cisco switches.

- **PortFast**: Enables immediate transition of a port to the forwarding state.
- **BPDU Guard**: Shuts down a PortFast-enabled port if it receives a Bridge Protocol Data Unit (BPDU), which helps prevent rogue switches from affecting STP.

## 🧰 Topology Details

- One Cisco switch
- Multiple PCs (end devices)
- One rogue switch (for BPDU testing)
- Connections from the main switch to PCs use access ports with PortFast and BPDU Guard enabled

## 🛠️ Configuration Steps

### 🔌 Step 1: Enable PortFast on Access Ports

```bash
enable
configure terminal
interface range fa0/1 - 3
spanning-tree portfast
