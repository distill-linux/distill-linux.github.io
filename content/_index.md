---
title: "distill"
---

<div class="distill-backdrop">
    <img class="distill-hero" src="/images/distill-hero.svg" alt="distill">
</div>

<p><em>distill</em> is an independent, from-scratch x86-64 <a href="https://en.wikipedia.org/wiki/Linux">linux</a> distribution built from source. it provides a minimal, simple base system based on <a href="https://musl.libc.org/">musl libc</a>, <a href="https://landley.net/toybox/">toybox</a>, <a href="https://www.mirbsd.org/mksh.htm">mksh</a>, <a href="http://smarden.org/runit/">runit</a>, and a native package management system: <strong><a href="/docs/packages/">drop & sink</a></strong>.</p>

<div class="release-banner">
latest release: <a href="/releases/">distill-standard 0.1.0-alpha</a> (tier 1 main)
</div>

<details open>
<summary>editions</summary>
<ul>
<li>
<strong>distill-standard (tier 1 / main)</strong>: our primary release for standard x86_64 PCs, laptops, and servers. provides a minimal base system with standard hardware drivers and firmware for out-of-the-box hardware support.
</li><li>
<strong>distill-libre (tier 2)</strong>: 100% free-software edition running the deblobbed <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel with no non-free firmware.
</li><li>
<strong>distill-t2 (tier 2)</strong>: specialized edition pre-configured with drivers for apple t2 macs (2018–2020 macbook pro, macbook air, and mac mini).
</li>
</ul>
</details>

<details open>
<summary>features</summary>
<ul>
<li>
<strong>built from scratch</strong> via an independent multi-stage cross-compilation bootstrap pipeline
</li><li>
core utilities provided by <a href="https://landley.net/toybox/">toybox</a> (0-bsd license)
</li><li>
default shell is <a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell)
</li><li>
native C package management with <strong><a href="/docs/packages/">drop</a></strong> (binary client) and <strong><a href="/docs/packages/">sink</a></strong> (source builder) using <code>.drop</code> packages
</li><li>
C library: <a href="https://musl.libc.org/">musl libc</a>
</li><li>
init system and service supervision: <a href="http://smarden.org/runit/">runit</a>
</li><li>
build toolchain: clang / llvm and samurai (samu)
</li>
</ul>
</details>

<details>
<summary>about the project</summary>
<p>the name comes from the distillation process: keeping only what is necessary for a functional, minimal operating system without extra layers of complexity.</p>
</details>

<details>
<summary>contribute</summary>
<p>source code and issue trackers are available on <a href="https://github.com/distill-linux">github</a>.</p>
<p>package recipes can be found in the <a href="https://github.com/distill-linux/ports">distill ports repository</a>.</p>
</details>

<details>
<summary>discord</summary>
<p>chat with contributors on discord: <a href="https://discord.gg/distill">discord.gg/distill</a></p>
</details>
