# 🧪 LPIC-1 Lab:
[Topic 101.1 Determine and Configure Hardware Settings](https://www.lpi.org/our-certifications/exam-101-102-objectives/#101.1_Determine_and_configure_hardware_settings)

[Topic 101.1 Notes](https://1drv.ms/w/c/354f1c8d534fbced/Ef7G_xVPG0ZJu6wZ0DdeGSUBmSy6RBxTid3fkbKFnt8J-w?e=Mm5yvf)

---

## 🔸 Part 1: Enable and Disable Integrated Peripherals

### 🎯 Goal:
Understand where and how integrated hardware (USB, NICs, audio, etc.) can be enabled or disabled.

### 🔧 Step 1.1: Access BIOS/UEFI Settings

1. Reboot your physical or virtual machine.
2. As it starts, press the BIOS/UEFI entry key (commonly `Del`, `F2`, `F10`, or `Esc`).
3. Navigate to **Integrated Peripherals**, **Advanced**, or similar section.
4. Locate and experiment with:
   - USB controllers
   - Network adapters (Ethernet/Wi-Fi)
   - Onboard audio

> 📝 **Note:** These changes are outside Linux. This step is about knowing how to access and toggle them.

---

## 🔸 Part 2: Identify Types of Mass Storage Devices

### 🎯 Goal:
Differentiate between HDDs, SSDs, USB drives, loop devices, and optical drives.

### 🔍 Step 2.1: List Block Devices

```bash
lsblk -o NAME,MAJ:MIN,RM,SIZE,RO,TYPE,MOUNTPOINT
```

- `RM`: Removable device (e.g., USB)
- `TYPE`: `disk`, `part`, `rom`, or `loop`

### 🔍 Step 2.2: Show Partition Tables

```bash
sudo fdisk -l
```

- SATA drives: `/dev/sda`
- NVMe SSDs: `/dev/nvme0n1`
- USB drives: `/dev/sdb`, `/dev/sdc`

👉 Insert a USB drive and rerun to observe changes.

---

## 🔸 Part 3: Check Hardware Resources (IRQs, DMA, I/O Ports)

### 🎯 Goal:
Understand how system resources are assigned to devices.

### 📘 Step 3.1: List Interrupts (IRQs)

```bash
cat /proc/interrupts
```

Example:
```
19:  12345678  IO-APIC   eth0
```

### 📘 Step 3.2: View I/O Ports

```bash
cat /proc/ioports
```

### 📘 Step 3.3: View DMA Channels

```bash
cat /proc/dma
```

---

## 🔸 Part 4: Use Tools to List Hardware Info

### 🎯 Goal:
Use CLI tools to audit hardware devices in Linux.

### 🛠️ Step 4.1: PCI Devices

```bash
lspci
lspci -v   # Verbose output
```

### 🛠️ Step 4.2: USB Devices

```bash
lsusb
lsusb -v | less   # Verbose mode
```

### 🛠️ Step 4.3: Full Hardware Inventory

```bash
sudo lshw -short
```

### 🛠️ Step 4.4: CPU and Memory Info

```bash
lscpu
free -h
```

### 🛠️ Step 4.5: DMI/BIOS Info

```bash
sudo dmidecode | less
```

Use `/` to search for terms like `BIOS`, `System`, `Memory`.

---

## 🔸 Part 5: Manage USB Devices

### 🎯 Goal:
Mount/unmount and power off USB devices.

### 💾 Step 5.1: Identify USB Drive

Plug in USB, then:

```bash
lsblk
```

Look for `/dev/sdb1` or similar.

### 💾 Step 5.2: Mount USB Drive

```bash
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```

### 💾 Step 5.3: Unmount USB Drive

```bash
sudo umount /mnt/usb
```

Or using `udisksctl`:

```bash
udisksctl unmount -b /dev/sdb1
udisksctl power-off -b /dev/sdb
```

---

## 🔸 Part 6: Explore sysfs, udev, and dbus

### 🎯 Goal:
Understand the Linux device management system.

### 🧠 Step 6.1: Explore sysfs `/sys`

```bash
cd /sys/class/net
ls
cat eth0/address   # Replace `eth0` with your interface
```

### 🧠 Step 6.2: Use udevadm

```bash
udevadm info --query=all --name=/dev/sdb1
```

Monitor real-time udev activity:

```bash
udevadm monitor
```

Unplug/replug USB to see output.

### 🧠 Step 6.3: Monitor D-Bus Events

```bash
dbus-monitor
```

Useful in GUI environments to see device messages.

---

## ✅ Lab Complete

You’ve now practiced:

- Accessing BIOS settings
- Identifying mass storage devices
- Viewing IRQs, I/O ports, DMA
- Listing PCI, USB, and full hardware
- Managing USB devices
- Using sysfs, udev, and dbus

🎓 **Tip:** These skills are essential for LPIC-1 and real-world Linux troubleshooting.
