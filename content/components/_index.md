---
title: "components"
description: "technical breakdown of the distill linux architecture"
---

<p>distill is assembled from scratch using carefully engineered, minimalist components designed to work in synergy without unnecessary abstraction layers or upstream distribution baggage.</p>

<details open>
<summary>1. kernel & hardware support: tiered architecture</summary>
<p>rather than enforcing a single rigid stance on hardware firmware, distill structures kernel support into tiers:</p>
<ul>
<li><strong>distill-standard (tier 1 / main)</strong>: optimized standard linux kernel with telemetry and tracking stripped out, providing essential modern firmware for WiFi, GPUs, and peripherals.</li>
<li><strong>distill-libre (tier 2)</strong>: 100% deblobbed <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel for pure free-software hardware.</li>
<li><strong>distill-t2 (tier 2)</strong>: linux kernel pre-patched with Apple T2 security silicon drivers (SPI keyboard, trackpad, audio, WiFi, Bluetooth, and NVMe).</li>
</ul>
</details>

<details open>
<summary>2. c library: musl libc</summary>
<p><a href="https://musl.libc.org/">musl</a> is a modern implementation of the c standard library designed for lightweight systems, embedded devices, and servers. it strictly adheres to posix and c99/c11 standards with a tiny footprint.</p>
</details>

<details open>
<summary>3. package management: drop & sink</summary>
<p>distill features its own native, dual-tool package management ecosystem:</p>
<ul>
<li><strong>drop</strong>: minimal native precompiled binary package manager (<40 KB stripped, musl + zlib). validates SHA-256 on the fly, enforces <code>.PORT</code> manifests as first headers in streaming <code>.drop</code> containers, and audits filesystem integrity with <code>drop check</code>.</li>
<li><strong>sink</strong>: community source builder and ports engine. orchestrates git checkouts with libgit2, enforces POSIX and clang builds inside isolated fakeroot sandboxes, and packages <code>.drop</code> containers with automatic ELF stripping.</li>
</ul>
</details>

<details open>
<summary>4. init system & supervision: runit</summary>
<p>distill uses <a href="http://smarden.org/runit/">runit</a> as its init scheme and service supervision daemon. it provides instant boots, deterministic 3-stage service startup, and automatic restart of crashed daemons with zero overhead.</p>
</details>

<details open>
<summary>5. core utilities: toybox</summary>
<p><a href="https://landley.net/toybox/">toybox</a> combines common linux command-line utilities into a single multi-call binary under a clean 0-bsd license, providing all essential shell utilities without GNU bloat.</p>
</details>

<details open>
<summary>6. default shell: mksh</summary>
<p>the <a href="https://www.mirbsd.org/mksh.htm">mirbsd korn shell (mksh)</a> is the default interactive and system <code>/bin/sh</code> shell in distill.</p>
</details>

<details open>
<summary>7. build system: from-scratch bootstrap pipeline</summary>
<p>distill is compiled from source from the ground up via an independent multi-stage cross-compilation pipeline:</p>
<ul>
<li><strong>stage0</strong>: host toolchain and hermetic prerequisites.</li>
<li><strong>stage1</strong>: target cross-toolchain (clang/llvm, musl headers, and sysroot).</li>
<li><strong>stage2</strong>: pure musl rootfs compilation (toybox, mksh, runit, dropbear, mandoc, drop, sink).</li>
<li><strong>stage3</strong>: kernel integration based on profile (standard, libre, or t2), initramfs generation, and bootable live ISO production.</li>
</ul>
</details>
