---
title: mount a usb drive on linux
tags: [it, linux]
date: 2026-05-18
id: iiiw
author: Julian Stoerig
---

On many linux distributions a GUI solution exists, this solution may be superfluous there. If no such solution exists, follow these steps:

1. Use `lsblk` before and after plugging in the drive. A new drive and partition should appear, this belongs to the drive. E.g. the drive `sda` with partition `sda1`.

2. Create mount directory in `/mnt`, e.g. with `sudo -p /mnt/usbdrive`.

3. Mount the drive there: `sudo mount /dev/sda1 /mnt/usbdrive`.

4. Use the drive.

5. Safely unmount it: `sudo umount /mnt/usbdrive`

6. Remove it.
