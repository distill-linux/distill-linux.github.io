---
title: "frequently asked questions"
description: "common questions about distill linux"
---

<details open>
<summary>why fork void linux?</summary>
<p>void linux is an extraordinary distribution with two of the best engineering choices in unix: <strong>xbps</strong> (written in pure c, blazing fast, byte-verified) and <strong>runit</strong> (simple, bulletproof process supervision).</p>
<p>however, void linux includes non-free repository options, gnu coreutils by default, standard linux kernels with proprietary blobs, and default shells like bash/dash. distill takes the best of void and strictly purifies it: strictly <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> (blob-free), pure <a href="https://musl.libc.org/">musl</a>, <a href="https://landley.net/toybox/">toybox</a>, <a href="https://www.mirbsd.org/mksh.htm">mksh</a>, and zero corporate tracking.</p>
</details>

<details open>
<summary>why toybox instead of gnu coreutils or busybox?</summary>
<ul>
<li><strong>vs gnu coreutils</strong>: gnu tools carry decades of legacy code, huge binary sizes, complex dependency chains, and non-standard flags. toybox is clean, tiny, and posix-compliant.</li>
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
<p>yes. distill provides a rock-solid baseline around <a href="https://github.com/X11Libre/xserver">X11Libre</a> without systemd or dbus hard dependencies. for wayland support details, check the <a href="/docs/display-graphics/">display & graphics</a> documentation.</p>
</details>
