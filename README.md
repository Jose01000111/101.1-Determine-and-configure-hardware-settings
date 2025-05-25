# 🧪 LPIC-1 Lab: Topic 101.1 Determine and Configure Hardware Settings

I created these LPIC-1 labs on my own Linux machine to get hands-on practice with hardware-related topics covered in the certification. Below, you’ll find a breakdown of what I did in each lab, what I learned, and why it matters. 

I’ve included some helpful links to guide you through the lab and for studying afterward:

[Topic 101.1 Determine and Configure Hardware Settings LPI Exam topics](https://www.lpi.org/our-certifications/exam-101-102-objectives/#101.1_Determine_and_configure_hardware_settings)

---

[Topic 101.1 Notes](https://1drv.ms/w/c/354f1c8d534fbced/Ef7G_xVPG0ZJu6wZ0DdeGSUBmSy6RBxTid3fkbKFnt8J-w?e=Mm5yvf)

---

[LPIC-1 Exam 101.1 Lab](https://1drv.ms/w/c/354f1c8d534fbced/EZOo5qb56thNhBnLrsEatygBT3OPsqAiqxEYwSc89oVSxQ?e=kbBURl)

---
### 🔸 Part 1: Enable/Disable Integrated Peripherals

I rebooted and entered the BIOS/UEFI (pressed "Esc" key for mine). Inside the Integrated Peripherals section, I found toggles for USB controllers, network cards, and onboard audio.

What I learned: It’s important to know how to access and control these settings outside the OS. Useful for troubleshooting when a device isn’t even being detected.

![mO70WL8](https://github.com/user-attachments/assets/747b7fea-e9f5-4b20-bf0b-7b91edad2e14)

Also here is what the GRUB (Bootloader) looks like:

![NcgQ1Af](https://github.com/user-attachments/assets/bdbe8123-970b-402e-80a1-2713a3d5b0cc)

![YlKl9sR](https://github.com/user-attachments/assets/d62a452c-762b-4d71-970b-46838d85c995)

![Ge52hxt](https://github.com/user-attachments/assets/07368661-0dc0-478c-bc9b-6d0e6c9e792d)

---
### 🔸 Part 2: Identify Mass Storage Devices

I ran the lsblk and fdisk -l commands to check out my drives. Then I plugged in a USB stick and saw it show up as /dev/sdb.

What I learned: Good practice to spot the difference between SSDs, HDDs, loop devices, and USBs using command-line tools.

![CaCuLxS](https://github.com/user-attachments/assets/9c05a34e-feee-440c-93ee-3ad2d31ce0a2)

![CaCuLxS](https://github.com/user-attachments/assets/eedc7449-948e-426e-9d62-f28b3f9067de)

---
### 🔸 Part 3: Check Hardware Resources

I checked system resource usage with:

cat /proc/interrupts for IRQs

cat /proc/ioports

cat /proc/dma

![1fJJ2jY](https://github.com/user-attachments/assets/4f9bc116-2df1-4ac7-b018-c1c0c5de9788)


What I learned: These files show how devices are connected and using resources. This can help figure out conflicts or issues with certain hardware.

---
### 🔸 Part 4: List Hardware Info

I ran the following:

lspci and lsusb to list PCI and USB devices

lshw -short for a quick system summary

lscpu and free -h for CPU and memory

dmidecode for BIOS and system details

![JtCkbWw](https://github.com/user-attachments/assets/058948db-641f-4427-9ae6-a9abcedd0604)

![C8wYBsM](https://github.com/user-attachments/assets/d8e98d10-658b-4985-9a9a-d1bb483511e8)

![5L5SQQO](https://github.com/user-attachments/assets/132cec76-59ef-4baf-b975-322aa628912b)

![j0ZcqC6](https://github.com/user-attachments/assets/4d68b5cc-74d1-4dfa-8b65-30fd26e704a3)

![LwadXQE](https://github.com/user-attachments/assets/c32e1bfd-aea5-4a50-b831-1474fde241d4)

What I learned: These are quick and powerful tools for checking what hardware you have and how it’s performing—all from the terminal.

---
### 🔸 Part 5: Manage USB Devices

###  🛠️ Troubleshooting Incident – USB Mount Commands on CentOS
While working on Part 5: Mount and Unmount USB Devices, I noticed that commands like udisksctl didn’t work on my CentOS VM. Turns out, CentOS doesn’t include desktop-focused tools like udisks2 by default, since it's a server-oriented OS.

To fix this, I’d need to install udisks2 manually or stick to basic commands like mount and umount with the correct device paths. This was a helpful reminder that tools vary across distros, so knowing your environment is just as important as knowing the commands.

![ArZ4OVT](https://github.com/user-attachments/assets/3cc535c2-a2c0-4d7f-9f89-840efca54ee3)

![ZWzRdj3](https://github.com/user-attachments/assets/c7ae6349-eb3a-4b0b-ba2e-147190d3a64d)

---

Plugged in a USB stick, mounted it to /mnt/usb, and then unmounted it. I used both traditional and udisksctl commands.

What I learned: Mounting and unmounting correctly is key to keeping USB data safe. Also nice to know how to power down a USB port.

![YdciHxY](https://github.com/user-attachments/assets/56792e34-eb81-4b8a-8143-19c261eefdbd)


---
### 🔸 Part 6: Explore sysfs, udev, and dbus

I checked network interface details in /sys/class/net

Ran udevadm info and udevadm monitor to see device events

Used dbus-monitor to watch system messages

![mG0oYSB](https://github.com/user-attachments/assets/d42e1d85-0bef-4339-84fa-47fa07a3bc81)

What I learned: These tools show how Linux tracks devices behind the scenes. You can actually see the kernel reacting when you plug or unplug something.
