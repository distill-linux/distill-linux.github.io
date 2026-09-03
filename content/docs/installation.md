---
title: "installation guide"
description: "step-by-step installation instructions for distill linux"
---

<p>distill linux can be installed directly from a live iso or bootstrapped manually using xbps.</p>

<details open>
<summary>1. download & verify iso</summary>
<p>download the latest <code>x86_64-musl-libre</code> image from the <a href="/releases/">releases</a> page and verify its checksum:</p>
<pre><code>sha256sum distill-0.1.0-x86_64-musl.iso</code></pre>
</details>

<details open>
<summary>2. boot the live environment</summary>
<p>flash the iso to a usb flash drive (replace <code>/dev/sdX</code> with your target drive):</p>
<pre><code>dd if=distill-0.1.0-x86_64-musl.iso of=/dev/sdX bs=4M status=progress conv=fsync</code></pre>
<p>boot the target machine and log in as <code>root</code> (password: <code>distill</code>).</p>
</details>

<details open>
<summary>3. partitioning & filesystems</summary>
<p>prepare your disk with standard gpt layout:</p>
<pre><code># /dev/nvme0n1p1: 512M EFI System Partition (vfat)
# /dev/nvme0n1p2: Root partition (ext4)

mkfs.vfat -F32 /dev/nvme0n1p1
mkfs.ext4 /dev/nvme0n1p2

mount /dev/nvme0n1p2 /mnt
mkdir -p /mnt/boot/efi
mount /dev/nvme0n1p1 /mnt/boot/efi</code></pre>
</details>

<details open>
<summary>4. bootstrap the base system</summary>
<p>install the purified base package group with xbps:</p>
<pre><code>export XBPS_ARCH=x86_64-musl
xbps-install -S -r /mnt base-distill linux-libre</code></pre>
</details>

<details open>
<summary>5. system configuration & bootloader</summary>
<p>enter the environment via chroot:</p>
<pre><code>xchroot /mnt /bin/mksh

# set hostname and root password
echo "distill-node" > /etc/hostname
passwd

# configure bootloader
xbps-install -S grub-x86_64-efi
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=distill
grub-mkconfig -o /boot/grub/grub.cfg

# exit and reboot
exit
umount -R /mnt
reboot</code></pre>
</details>
