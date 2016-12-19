---
layout: default
title: Reinstalling GRUB2 on Fedora 22 with LVM and LUKS
tags: ['linux']
---

My system dual-boots Fedora 22 and Ubuntu 12.04. The Fedora 22 system is managed with LVM, and all partitions except `/boot` are encrypted with LUKS. Ubuntu is on a primary partition. It's simpler to have Fedora managing the MBR, because it can easily detect Ubuntu, but not vice versa.

Unfortunately, on a recent package update of Ubuntu, its GRUB2 package was updated, and it overwrote the MBR without any prompts. I've come to expect this quality of engineering from Ubuntu (since 10.04 at least). I only use Ubuntu for better compatibility with Steam and other non-free software I reluctantly use.

I noticed my bootloader had been replaced on reboot, when the BIOS booted straight into a purple screen, which booted straight into Ubuntu -- it didn't even register the Fedora installation.

Here's what I did to reinstall Fedora's GRUB2, so that both Fedora and Ubuntu are selectable from the bootloader:

- create a Fedora 22 Live USB;

- boot the Live USB to the desktop;

- mount the necessary partitions of the existing Fedora installation, `chroot` into them, and reinstall GRUB2 from there, so:
  - open nautilus, select the "encrypted partition" representing the Fedora 22 LVM partition, and type in the password. This will make the logical partitions appear, and prompt a message saying "unknown filesystem" - don't worry about that;
  - open the Disks application to determine the labels of the disk(s), the LVM partitions, and the Fedora installation's `/boot` partition;
  - `mkdir /mnt/fedora`
  - `mount /dev/<fedora-lvm-label>/root /mnt/fedora`
  - mount other LVM partitions if you have split it up further, e.g. `/usr` or `/var`; don't worry about `/home`
  - `mount /dev/<fedora-boot-label> /mnt/fedora/boot`
  - `mount --bind /dev /mnt/fedora/dev`
  - `mount --bind /proc /mnt/fedora/proc`
  - `mount --bind /sys /mnt/fedora/sys`
  - `chroot /mnt/fedora`
  - `grub2-install /dev/<boot-disk>`

- reboot and you should be golden!

I adapted these steps from: <https://ask.fedoraproject.org/en/question/40578/how-to-reinstall-or-fix-grub-in-fedora-20/?answer=40593#post-id-40593>

I spent a while trying other approaches, to no avail. Hopefully this helps others come to the solution quicker.

