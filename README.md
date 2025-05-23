# 🧪 LPIC-1 Topic 101.1 Determine and Configure Hardware Settings

**Objective:** Learn to identify, inspect, and manage hardware components in Linux.

---

## 🔸 Part 1: Enable and Disable Integrated Peripherals

### 🔍 Goal:
Understand where and how integrated hardware (USB, NICs, audio, etc.) can be enabled or disabled.

### 📌 Step 1.1: Understand BIOS/UEFI Settings

1. Reboot your physical/virtual machine.
2. As it starts up, press the BIOS/UEFI key (usually `Del`, `F2`, `F10`, or `Esc`).
3. Look for a tab like **"Integrated Peripherals"** or **"Advanced"**.

#### ✅ In BIOS/UEFI:
Locate options such as:

- USB Controllers  
- Network Adapter (Ethernet/Wi-Fi)  
- Audio Devices  

Practice enabling/disabling them.

> **Note:** These changes cannot be made from Linux. You just need to understand where they're found.

---

## 🔸 Part 2: Identify Types of Mass Storage Devices

### 🔍 Goal:
Differentiate between HDDs, SSDs, USB drives, loopback devices, and optical drives.

### 📌 Step 2.1: List Block Devices

```bash
lsblk -o NAME,MAJ:MIN,RM,SIZE,RO,TYPE,MOUNTPOINT
