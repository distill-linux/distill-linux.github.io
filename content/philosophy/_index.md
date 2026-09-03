---
title: "philosophy"
description: "the principles and motivation behind distill linux"
---

<p>modern computing has largely lost its simplicity. standard operating systems ship gigabytes of opaque binaries, corporate telemetry frameworks, binary blobs, and overlapping layers of abstraction that obscure what your computer is actually doing.</p>

<p><strong>distill</strong> was created to reverse this trend through deliberate distillation and from-scratch independence.</p>

<h3>1. what does "distill" mean?</h3>

<p>in chemistry, distillation is the process of heating a liquid until its volatile components vaporize, then condensing those vapors back into a pure liquid—leaving behind all impurities, sediments, and residues.</p>

<p>in distill linux, we apply this exact principle to the operating system:</p>
<ul>
<li><strong>the impurities</strong>: corporate telemetry, tracking daemons, analytics hooks, artificial vendor lock-in, and bloated duplicate tools.</li>
<li><strong>the pure distillate</strong>: a clean, posix-conforming, audit-friendly unix-like system where every single binary and line of code serves the user alone.</li>
</ul>

<h3>2. our core principles</h3>

<details open>
<summary>practical minimalism & tiered editions</summary>
<p>we do not arbitrarily sacrifice hardware functionality to satisfy dogmatic extremes. instead, we provide clear tiers:</p>
<ul>
<li><strong>distill-standard (tier 1 / main)</strong>: our flagship release. provides pure musl/toybox/mksh minimalism while including practical modern hardware firmware (for WiFi, GPUs, and peripherals) stripped of all corporate telemetry.</li>
<li><strong>distill-libre (tier 2)</strong>: a 100% deblobbed linux-libre edition for users with open-source hardware who require absolute free-software purity.</li>
<li><strong>distill-t2 (tier 2)</strong>: dedicated kernel support for Apple T2 Mac computers.</li>
</ul>
</details>

<details open>
<summary>built from scratch: total architectural independence</summary>
<p>distill does not fork or depend on any upstream distribution. it is cross-compiled from source through an independent multi-stage bootstrap pipeline (stage0 to stage3), establishing full provenance and transparency over every binary on the root filesystem.</p>
</details>

<details open>
<summary>minimalist userland (toybox & mksh)</summary>
<p>rather than pulling in massive utility suites with legacy complexity, distill pairs <a href="https://landley.net/toybox/">toybox</a> with <a href="https://www.mirbsd.org/mksh.htm">mksh</a>:</p>
<ul>
<li><strong>toybox</strong>: provides standard posix core command-line tools in a single, compact, 0-dependency binary under a clean bsd license.</li>
<li><strong>mksh</strong>: the mirbsd korn shell provides a lean, rock-solid, standards-compliant, and secure shell without unnecessary bloat.</li>
</ul>
</details>

<details open>
<summary>musl libc over glibc</summary>
<p><a href="https://musl.libc.org/">musl libc</a> is lightweight, adheres rigorously to posix and c standards, produces clean static and dynamic binaries, and avoids the labyrinthine complexity and legacy overhead of glibc.</p>
</details>

<details open>
<summary>native package management: drop & sink</summary>
<p>package management in distill follows the same ethos of strict minimalism and speed:</p>
<ol>
<li><strong>drop</strong>: an ultra-compact (<40 KB stripped) precompiled package client verifying SHA-256 on the fly with atomic database recording.</li>
<li><strong>sink</strong>: an isolated ports engine and recipe builder utilizing libgit2 and POSIX sandboxing to produce verifiable <code>.drop</code> container archives.</li>
<li><strong>runit</strong>: a bulletproof 3-stage service supervisor that manages processes with near-zero resource consumption.</li>
</ol>
</details>
