---
title: "frequently asked questions"
description: "common questions about distill linux"
---

<details open>
<summary>why build distill linux from scratch?</summary>
<p>most modern linux distributions rely on deeply entrenched legacy stacks: sprawling GNU toolchains, complex systemd service graphs, glibc binary bloat, and upstream package trees carrying thousands of non-free firmware blobs and telemetry hooks.</p>
<p>distill is built completely from the ground up to achieve total architectural independence and purification. by implementing our own multi-stage cross-compilation pipeline, native package management (<strong>drop & sink</strong>), pure musl libc, toybox, and mksh, distill guarantees a strictly audited, distraction-free environment that answers only to its users.</p>
</details>

<details open>
<summary>what package manager does distill use?</summary>
<p>distill uses its own native dual-tool package management ecosystem:</p>
<ul>
<li><strong>drop</strong>: an ultra-compact (<40 KB stripped) precompiled package manager targeting pure musl libc with on-the-fly streaming SHA-256 verification and atomic state registration.</li>
<li><strong>sink</strong>: the community ports engine and recipe builder, orchestrating Git repositories, POSIX sandbox builds, and automated ELF stripping into verified <code>.drop</code> container archives.</li>
</ul>
</details>

<details open>
<summary>why toybox instead of gnu coreutils or busybox?</summary>
<ul>
<li><strong>vs gnu coreutils</strong>: gnu tools carry decades of legacy code, massive binary sizes, complex dependency chains, and non-standard flags. toybox is clean, tiny, and strictly posix-compliant.</li>
<li><strong>vs busybox</strong>: while busybox is great, toybox is developed under the 0-bsd license, specifically crafted with clean modern c standards and designed from the ground up for full linux desktop and posix compatibility.</li>
</ul>
</details>

<details open>
<summary>why mksh instead of bash or zsh?</summary>
<p>gnu bash is large, slow to start, and prone to complex feature bloat. <a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell) provides a rock-solid, standards-compliant, and secure shell environment with interactive line editing, low memory footprint, and instantaneous execution.</p>
</details>

<details>
<summary>is any proprietary software allowed in distill?</summary>
<p>no. the core repositories of distill do not package or distribute closed-source binaries, drm blobs, or proprietary drivers. if hardware requires closed binary firmware to function, you will need libre-compatible hardware or libre firmware equivalents.</p>
</details>

<details>
<summary>how does distill strip telemetry and corporate branding?</summary>
<ul>
<li><strong>kernel</strong>: built with linux-libre deblobbing scripts, purging non-free microcode and corporate telemetry drivers.</li>
<li><strong>base system</strong>: removed any package reporting, crash report hooks, or phone-home daemons.</li>
<li><strong>software ports</strong>: packages are compiled with privacy-preserving flags (telemetry disabled at compile time).</li>
</ul>
</details>

<details>
<summary>can i run graphical desktop environments?</summary>
<p>yes. distill supports lightweight window managers and desktop environments through our modernized <a href="https://github.com/X11Libre/xserver">X11Libre</a> display server stack with seatd, as well as modern Wayland compositors.</p>
</details>
