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
<li><strong>the impurities</strong>: proprietary firmware, corporate telemetry, tracking daemons, analytics hooks, artificial vendor lock-in, and bloated duplicate tools.</li>
<li><strong>the pure distillate</strong>: a clean, posix-conforming, audit-friendly, libre unix-like system where every single binary and line of code serves the user alone.</li>
</ul>

<h3>2. our core principles</h3>

<details open>
<summary>100% free software & libre kernel</summary>
<p>we believe computing hardware should belong entirely to the user. we reject proprietary closed-source kernel blobs and telemetry daemons. by deploying <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> and stripping out corporate branding and data collection hooks, distill guarantees that your operating system cannot spy on you.</p>
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
