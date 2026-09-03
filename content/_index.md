---
title: "distill the purified operating system"
---

<div class="distill-backdrop">
    <img class="distill-hero" src="/images/distill-hero.svg" alt="distill">
</div>

<p><em>distill</em> is an independent, purified, and lightweight from-scratch x86-64 <a href="https://en.wikipedia.org/wiki/Linux">linux</a> distribution built from the ground up. it strips corporate telemetry, tracking, and bloated legacy layers, providing a pure, minimal system based on <a href="https://musl.libc.org/">musl libc</a>, <a href="https://landley.net/toybox/">toybox</a>, <a href="https://www.mirbsd.org/mksh.htm">mksh</a>, <a href="http://smarden.org/runit/">runit</a>, and the native <strong><a href="/docs/packages/">drop & sink</a></strong> package management ecosystem.</p>

<div class="release-banner">
latest release: <a href="/releases/">distill-standard 0.1.0-alpha</a> (tier 1 flagship)
</div>

<details open>
<summary>our editions</summary>
<ul>
<li>
<strong>distill-standard (tier 1 / main)</strong>: our flagship release for standard x86_64 PCs, laptops, and workstations. maintains lean minimalism while including practical hardware support and firmware without corporate telemetry.
</li><li>
<strong>distill-libre (tier 2)</strong>: a 100% libre edition running a deblobbed <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel for pure free-software purists.
</li><li>
<strong>distill-t2 (tier 2)</strong>: a specialized edition pre-configured with kernel drivers for apple t2 security chip macs (2018–2020 macbook pro, macbook air, and mac mini).
</li>
</ul>
</details>

<details open>
<summary>features</summary>
<ul>
<li>
<strong>built from scratch</strong> via an independent multi-stage cross-compilation bootstrap pipeline
</li><li>
coreutils replaced with <a href="https://landley.net/toybox/">toybox</a> (0-bsd licensed)
</li><li>
shell replaced with <a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell)
</li><li>
native C package management with <strong><a href="/docs/packages/">drop</a></strong> (binary client) and <strong><a href="/docs/packages/">sink</a></strong> (source builder) using verified <code>.drop</code> containers
</li><li>
pure <a href="https://musl.libc.org/">musl libc</a> and lightweight <a href="http://smarden.org/runit/">runit</a> process supervision
</li><li>
clean clang / llvm compiler toolchain with samurai (samu) build engine
</li><li>
zero corporate tracking, telemetry, or spyware
</li>
</ul>
</details>

<details>
<summary>name & definition</summary>
<p>the name is derived from the definition of <strong>distill</strong> (<em>"to purify a substance by vaporizing and condensing it; to extract the essential essence while leaving behind all impurities and sediments"</em>).</p>
<p>distill strips out telemetry, spyware, and architectural bloat to leave only a clean, pure operating system.</p>
</details>

<details>
<summary>contribute</summary>
<p>pull requests, port recipes, and bug reports are welcome on <a href="https://github.com/distill-linux">github</a>.</p>
<p>explore and contribute package recipes in the <a href="https://github.com/distill-linux/ports">distill ports repository</a>.</p>
</details>

<details>
<summary>discord</summary>
<p>join our community and chat with contributors on discord: <a href="https://discord.gg/distill">discord.gg/distill</a></p>
</details>
