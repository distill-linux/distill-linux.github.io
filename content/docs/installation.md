---
title: "installation guide"
description: "step-by-step installation instructions for distill linux"
---

<p>distill linux is currently in active pre-release development. prebuilt installation images will be available on the <a href="/releases/">releases</a> page once initial releases are published. in the interim, live system ISOs can be built from source using our bootstrap build pipeline.</p>

<details open>
<summary>1. installation ISO media</summary>
<p>if you have built an ISO from source or acquired a development image (e.g. <code>distill-standard.iso</code>), verify its checksum before writing to media:</p>

```sh
# verify sha256 checksum of your built ISO
sha256sum distill-standard.iso
```

</details>

<details open>
<summary>2. write ISO to installation media</summary>
<p>write the ISO to a usb flash drive (replace <code>/dev/sdX</code> with your target device):</p>

```sh
dd if=distill-standard.iso of=/dev/sdX bs=4M status=progress conv=fsync
```

<p>boot the machine from the usb drive and log in as <code>root</code> (password: <code>distill</code>).</p>
</details>

<details open>
<summary>3. partitioning & filesystems</summary>
<p>create a standard GPT partition layout using <code>fdisk</code> or <code>parted</code>:</p>

```sh
# example layout:
# /dev/nvme0n1p1: 512M EFI System Partition (vfat)
# /dev/nvme0n1p2: Root partition (ext4)

mkfs.vfat -F32 /dev/nvme0n1p1
mkfs.ext4 /dev/nvme0n1p2

mount /dev/nvme0n1p2 /mnt
mkdir -p /mnt/boot/efi
mount /dev/nvme0n1p1 /mnt/boot/efi
```

</details>

<details open>
<summary>4. copy base system to disk</summary>
<p>deploy the system rootfs onto the mounted disk:</p>

```sh
# copy live system rootfs to target disk
cp -a /run/distill/rootfs/* /mnt/

# ensure essential mount points exist
mkdir -p /mnt/dev /mnt/proc /mnt/sys /mnt/run /mnt/tmp
```

</details>

<details open>
<summary>5. system configuration & bootloader</summary>
<p>mount virtual filesystems and chroot into the new installation:</p>

```sh
# bind mount kernel virtual filesystems
mount --rbind /dev /mnt/dev
mount --rbind /proc /mnt/proc
mount --rbind /sys /mnt/sys

# enter target system with mksh
chroot /mnt /bin/mksh

# set system hostname
echo "distill-node" > /etc/hostname

# set root password
passwd

# configure filesystem table (/etc/fstab)
cat << 'FSTAB' > /etc/fstab
/dev/nvme0n1p2  /          ext4  defaults,noatime  0 1
/dev/nvme0n1p1  /boot/efi  vfat  defaults          0 2
FSTAB

# install UEFI bootloader
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=distill
grub-mkconfig -o /boot/grub/grub.cfg

# exit chroot
exit

# unmount partitions and reboot
umount -R /mnt
reboot
```

</details>
