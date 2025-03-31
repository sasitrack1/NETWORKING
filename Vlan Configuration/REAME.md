# VLAN Configuration - Cisco Packet Tracer

## Overview
This project demonstrates the configuration of VLANs (Virtual Local Area Networks) in Cisco Packet Tracer. VLANs are used to segment a network into different broadcast domains, improving security and network efficiency.

## Network Topology
- **Switch (2960-24TT)**: Central network device managing VLANs.
- **PC0, PC1, PC2, PC3**: End devices connected to the switch.
- **VLAN Assignments**:
  - VLAN 10: PC0, PC1 (Group 1)
  - VLAN 20: PC2, PC3 (Group 2)

## Configuration Steps
1. **Access the switch CLI**
   ```
   enable
   configure terminal
   ```
2. **Create VLANs**
   ```
   vlan 10
   name Group1
   vlan 20
   name Group2
   exit
   ```
3. **Assign VLANs to Ports**
   ```
   interface FastEthernet0/1
   switchport mode access
   switchport access vlan 10
   exit

   interface FastEthernet0/2
   switchport mode access
   switchport access vlan 10
   exit

   interface FastEthernet0/3
   switchport mode access
   switchport access vlan 20
   exit

   interface FastEthernet0/4
   switchport mode access
   switchport access vlan 20
   exit
   ```
4. **Verify VLAN Configuration**
   ```
   show vlan brief
   ```

## Expected Outcome
- PCs in VLAN 10 (PC0, PC1) can communicate with each other.
- PCs in VLAN 20 (PC2, PC3) can communicate with each other.
- Devices in different VLANs cannot communicate without a router or Layer 3 switch.

## Requirements
- **Cisco Packet Tracer 8.2 or later**
- Basic knowledge of VLANs and switch configuration.

## Future Enhancements
- Implement **Inter-VLAN Routing** for communication between VLANs.
- Configure **VLAN Trunking Protocol (VTP)** for better VLAN management.

## Author
- **Sasikumar R**  
  Web Developer & Network Enthusiast

## License
This project is open-source and available under the **MIT License**.

