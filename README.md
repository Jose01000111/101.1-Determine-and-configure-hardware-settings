# 🧪 LPIC-1 Lab: Topic 101.1 Determine and Configure Hardware Settings
[Topic 101.1 Determine and Configure Hardware Settings LPI Exam topics](https://www.lpi.org/our-certifications/exam-101-102-objectives/#101.1_Determine_and_configure_hardware_settings)
---
[Topic 101.1 Notes](https://1drv.ms/w/c/354f1c8d534fbced/Ef7G_xVPG0ZJu6wZ0DdeGSUBmSy6RBxTid3fkbKFnt8J-w?e=Mm5yvf)
---
[LPIC-1 Exam 101.1 Lab](https://1drv.ms/w/c/354f1c8d534fbced/EZOo5qb56thNhBnLrsEatygBT3OPsqAiqxEYwSc89oVSxQ?e=kbBURl)
---
I created these LPIC-1 labs on my own Linux machine to get hands-on practice with hardware-related topics covered in the certification. Below, you’ll find a breakdown of what I did in each lab, what I learned, and why it matters. I’ve also marked spots with a 📸 emoji where I took screenshots to include in my GitHub repo.

For reference, I’ve included the following helpful links:

Official LPI Exam Objectives: https://www.lpi.org/our-certifications/lpic-1-overview

My Lab Notes: [link goes here]

Full Lab Instructions: [link goes here]

Let’s get into it!

🔸 Part 1: Enable/Disable Integrated Peripherals

I rebooted and entered the BIOS/UEFI (pressed "Del" for mine). Inside the Integrated Peripherals section, I found toggles for USB controllers, network cards, and onboard audio.

What I learned: It’s important to know how to access and control these settings outside the OS. Useful for troubleshooting when a device isn’t even being detected.

📸 Screenshot BIOS screen showing peripheral options.

🔸 Part 2: Identify Mass Storage Devices

I ran the lsblk and fdisk -l commands to check out my drives. Then I plugged in a USB stick and saw it show up as /dev/sdb.

What I learned: Good practice to spot the difference between SSDs, HDDs, loop devices, and USBs using command-line tools.

📸 Screenshot before and after inserting the USB.

🔸 Part 3: Check Hardware Resources

I checked system resource usage with:

cat /proc/interrupts for IRQs

cat /proc/ioports

cat /proc/dma

What I learned: These files show how devices are connected and using resources. This can help figure out conflicts or issues with certain hardware.

📸 Screenshot of cat /proc/interrupts.

🔸 Part 4: List Hardware Info

I ran the following:

lspci and lsusb to list PCI and USB devices

lshw -short for a quick system summary

lscpu and free -h for CPU and memory

dmidecode for BIOS and system details

What I learned: These are quick and powerful tools for checking what hardware you have and how it’s performing—all from the terminal.

📸 Screenshot of lshw -short or lspci.

🔸 Part 5: Manage USB Devices

Plugged in a USB stick, mounted it to /mnt/usb, and then unmounted it. I used both traditional and udisksctl commands.

What I learned: Mounting and unmounting correctly is key to keeping USB data safe. Also nice to know how to power down a USB port.

📸 Screenshot showing mounted USB in lsblk.

🔸 Part 6: Explore sysfs, udev, and dbus

I checked network interface details in /sys/class/net

Ran udevadm info and udevadm monitor to see device events

Used dbus-monitor to watch system messages

What I learned: These tools show how Linux tracks devices behind the scenes. You can actually see the kernel reacting when you plug or unplug something.

📸 Screenshot of udevadm monitor while plugging in a USB.

