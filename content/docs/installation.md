---
title: "installation guide"
description: "step-by-step installation instructions for distill linux"
---

<p>distill linux can be installed directly from an official live ISO onto bare metal or a virtual machine.</p>

<details open>
<summary>1. download & verify ISO</summary>
<p>download your chosen edition from the <a href="/releases/">releases</a> page and verify its checksum:</p>
<pre><code># download and verify sha256 checksum
sha256sum distill-standard-0.1.0.iso</code></pre>
</details>

<details open>
<summary>2. write ISO to installation media</summary>
<p>write the ISO to a usb flash drive (replace <code>/dev/sdX</code> with your target device):</p>
<pre><code>dd if=distill-standard-0.1.0.iso of=/dev/sdX bs=4M status=progress conv=fsync</code></pre>
<p>boot the machine from the usb drive and log in as <code>root</code> (password: <code>distill</code>).</p>
</details>

<details open>
<summary>3. partitioning & filesystems</summary>
<p>create a standard GPT partition layout using <code>fdisk</code> or <code>parted</code>:</p>
<pre><code># example layout:
# /dev/nvme0n1p1: 512M EFI System Partition (vfat)
# /dev/nvme0n1p2: Root partition (ext4)

mkfs.vfat -F32 /dev/nvme0n1p1
mkfs.ext4 /dev/nvme0n1p2

mount /dev/nvme0n1p2 /mnt
mkdir -p /mnt/boot/efi
mount /dev/nvme0n1p1 /mnt/boot/efi</code></pre>
</details>

<details open>
<summary>4. copy base system to disk</summary>
<p>deploy the system rootfs onto the mounted disk:</p>
<pre><code># copy live system rootfs to target disk
cp -a /run/distill/rootfs/* /mnt/

# ensure essential mount points exist
mkdir -p /mnt/dev /mnt/proc /mnt/sys /mnt/run /mnt/tmp</code></pre>
</details>

<details open>
<summary>5. system configuration & bootloader</summary>
<p>mount virtual filesystems and chroot into the new installation:</p>
<pre><code># bind mount kernel virtual filesystems
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
cat &lt;&lt; 'FSTAB' &gt; /etc/fstab
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
reboot</code></pre>
</details>
