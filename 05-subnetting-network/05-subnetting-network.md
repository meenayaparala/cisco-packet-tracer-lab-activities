# 🧪 Lab 5: Subnetting and Network Design

This lab demonstrates how to design and configure a network with **two subnets**, each containing **two PCs**, connected via a router. The configuration includes assigning IP addresses, setting up default gateways, and verifying connectivity across subnets.

---

## 🎯 Goal:
- Create a network with **two subnets**.
- Assign IP addresses to devices in each subnet.
- Configure the router to enable communication between the subnets.

---

## 🖥 Devices:
| Device   | Quantity |
|----------|----------|
| PCs      | 4        |
| Switches | 2        |
| Router   | 1        |

---

## 🔧 Topology:

[PC0] [PC1] \ / [Switch0] ---- (G0/0) Router (G0/1) ---- [Switch1] / [PC2] [PC3]

---

## 🧠 IP Plan:
| Device   | Interface          | IP Address      | Subnet          | Subnet Mask       | Default Gateway  |
|----------|--------------------|-----------------|-----------------|-------------------|------------------|
| PC0      | FastEthernet0      | 192.168.1.10    | 192.168.1.0/24  | 255.255.255.0     | 192.168.1.1      |
| PC1      | FastEthernet0      | 192.168.1.11    | 192.168.1.0/24  | 255.255.255.0     | 192.168.1.1      |
| Router   | GigabitEthernet0/0 | 192.168.1.1     | 192.168.1.0/24  | 255.255.255.0     | -                |
| Router   | GigabitEthernet0/1 | 192.168.2.1     | 192.168.2.0/24  | 255.255.255.0     | -                |
| PC2      | FastEthernet0      | 192.168.2.10    | 192.168.2.0/24  | 255.255.255.0     | 192.168.2.1      |
| PC3      | FastEthernet0      | 192.168.2.11    | 192.168.2.0/24  | 255.255.255.0     | 192.168.2.1      |

---

## 🔧 Configuration Steps:

### 🔹 Step 1: Connect Devices
- Use **copper straight-through cables**:
  - PC0 → Switch0
  - PC1 → Switch0
  - Switch0 → Router G0/0
  - Router G0/1 → Switch1
  - Switch1 → PC2
  - Switch1 → PC3

### 🔹 Step 2: Configure Router Interfaces
1. Click on the router → **CLI** tab.
2. Enter the following commands to configure the router:
   ```bash
   enable
   configure terminal

   interface gigabitEthernet0/0
   ip address 192.168.1.1 255.255.255.0
   no shutdown
   exit

   interface gigabitEthernet0/1
   ip address 192.168.2.1 255.255.255.0
   no shutdown
   exit
   🔹 Step 3: Configure PCs
On each PC, go to Desktop > IP Configuration.
Assign the following IP addresses and default gateways:
PC0: IP: 192.168.1.10, Subnet Mask: 255.255.255.0, Gateway: 192.168.1.1
PC1: IP: 192.168.1.11, Subnet Mask: 255.255.255.0, Gateway: 192.168.1.1
PC2: IP: 192.168.2.10, Subnet Mask: 255.255.255.0, Gateway: 192.168.2.1
PC3: IP: 192.168.2.11, Subnet Mask: 255.255.255.0, Gateway: 192.168.2.1
✅ Verification:
Use the Command Prompt on each PC to test connectivity:
From PC0, ping PC2:
ping 192.168.2.10
From PC1, ping PC3:
ping 192.168.2.11
If the configuration is correct, you should see replies like:
Reply from 192.168.2.10: bytes=32 time<1ms TTL=128

📌 Notes:
Ensure all cables are properly connected (green link lights).
Verify that the router interfaces are enabled (no shutdown).
Set the correct default gateways on all PCs.
This setup uses manual IP assignment. For dynamic IPs, consider using DHCP.
📸 Screenshot:
![Logo](05-subnet-networking-image.png)