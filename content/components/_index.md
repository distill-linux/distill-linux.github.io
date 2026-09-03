---
title: "components"
description: "technical breakdown of the distill linux architecture"
---

<p>distill is assembled from scratch using minimalist, standards-conforming components designed to work together cleanly.</p>

<details open>
<summary>1. kernel</summary>
<p>distill provides three kernel configurations depending on the edition:</p>
<ul>
<li><strong>distill-standard (tier 1 / main)</strong>: standard linux kernel with common device drivers and firmware for modern x86_64 PCs.</li>
<li><strong>distill-libre (tier 2)</strong>: 100% free-software <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel with no non-free firmware blobs.</li>
<li><strong>distill-t2 (tier 2)</strong>: linux kernel pre-patched with Apple T2 silicon drivers (keyboard, trackpad, audio, NVMe, and WiFi).</li>
</ul>
</details>

<details open>
<summary>2. c library: musl libc</summary>
<p><a href="https://musl.libc.org/">musl</a> is a lightweight, standards-compliant implementation of the C standard library. it produces small, efficient binaries with low memory usage.</p>
</details>

<details open>
<summary>3. package management: drop & sink</summary>
<p>distill uses a native dual-tool package management system:</p>
<ul>
<li><strong>drop</strong>: binary package manager (<40 KB stripped, musl + zlib). installs packages, verifies SHA-256 hashes on the fly, and manages the package database in <code>/var/db/drop/</code>.</li>
<li><strong>sink</strong>: community source builder and ports engine. manages git sources with libgit2, builds packages in isolated fakeroot directories, automatically strips ELF binaries, and generates <code>.drop</code> archives.</li>
</ul>
</details>

<details open>
<summary>4. init system & service supervision: runit</summary>
<p>distill uses <a href="http://smarden.org/runit/">runit</a> for system initialization and service supervision. it provides fast boots, simple service run scripts, and automatic service restart.</p>
</details>

<details open>
<summary>5. core utilities: toybox</summary>
<p><a href="https://landley.net/toybox/">toybox</a> provides standard posix utilities in a single multi-call binary under a 0-bsd license.</p>
</details>

<details open>
<summary>6. default shell: mksh</summary>
<p><a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell) is the default interactive and system <code>/bin/sh</code> shell in distill.</p>
</details>

<details open>
<summary>7. build system: from-scratch bootstrap pipeline</summary>
<p>distill is cross-compiled from source through a multi-stage bootstrap system:</p>
<ul>
<li><strong>stage0</strong>: host build tools and prerequisites.</li>
<li><strong>stage1</strong>: target cross-toolchain (clang/llvm, musl headers, and sysroot).</li>
<li><strong>stage2</strong>: pure musl rootfs compilation (toybox, mksh, runit, dropbear, mandoc, drop, sink).</li>
<li><strong>stage3</strong>: kernel integration based on profile, initramfs creation, and bootable live ISO production.</li>
</ul>
</details>
