---
title: "frequently asked questions"
description: "common questions about distill linux"
---

<details open>
<summary>why build distill from scratch?</summary>
<p>most linux distributions carry decades of legacy code, large toolchains, and overlapping layers of background services. distill is built from the ground up to provide a simple, verifiable base system with musl libc, toybox, mksh, runit, and a lightweight native package manager.</p>
</details>

<details open>
<summary>what editions are available?</summary>
<p>distill provides three release editions:</p>
<ul>
<li><strong>distill-standard (tier 1 / main)</strong>: our primary release for standard x86_64 PCs, laptops, and servers. includes standard hardware firmware so devices like WiFi, Bluetooth, and graphics work out of the box.</li>
<li><strong>distill-libre (tier 2)</strong>: a 100% free-software edition running the linux-libre kernel with no proprietary firmware blobs.</li>
<li><strong>distill-t2 (tier 2)</strong>: an edition pre-configured with drivers for Intel Apple Macs with the T2 security chip.</li>
</ul>
</details>

<details open>
<summary>how does distill handle hardware firmware?</summary>
<p>we provide separate editions based on hardware and user requirements:</p>
<ul>
<li><strong>distill-standard</strong> includes standard hardware firmware so common WiFi cards, Bluetooth adapters, and graphics cards work without manual setup.</li>
<li><strong>distill-libre</strong> removes all non-free firmware for users running fully open hardware.</li>
<li><strong>distill-t2</strong> includes the necessary drivers and firmware for Apple T2 hardware.</li>
</ul>
</details>

<details open>
<summary>what package manager does distill use?</summary>
<p>distill uses a native dual-tool package management system:</p>
<ul>
<li><strong>drop</strong>: a small (<40 KB stripped) C client targeting musl libc that installs binary packages, verifies SHA-256 checksums on the fly, and tracks installed files.</li>
<li><strong>sink</strong>: a source builder that checks out git sources, builds packages in an isolated fakeroot environment, strips binaries, and generates <code>.drop</code> archives.</li>
</ul>
</details>

<details open>
<summary>why toybox instead of gnu coreutils or busybox?</summary>
<ul>
<li><strong>vs gnu coreutils</strong>: toybox implements standard posix utilities in a compact multi-call binary with zero external dependencies and a clean 0-bsd license.</li>
<li><strong>vs busybox</strong>: toybox is designed specifically for standard linux desktop and development environments, with posix compliance and modern C code.</li>
</ul>
</details>

<details open>
<summary>why mksh instead of bash or zsh?</summary>
<p><a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell) starts instantaneously, has a low memory footprint, and provides a strict standards-compliant shell with interactive line editing.</p>
</details>

<details>
<summary>can i run graphical desktop environments?</summary>
<p>yes. distill supports lightweight window managers and desktop environments through <a href="https://github.com/X11Libre/xserver">X11Libre</a> with seatd, as well as modern Wayland compositors.</p>
</details>
