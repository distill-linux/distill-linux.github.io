---
title: "distill the purified operating system"
---

<div class="distill-backdrop">
    <img class="distill-hero" src="/images/distill-hero.svg" alt="distill">
</div>

<p><em>distill</em> is an independent, purified, and lightweight from-scratch x86-64 <a href="https://en.wikipedia.org/wiki/Linux">linux</a> distribution built from the ground up. it completely strips all corporate telemetry, proprietary blobs, and bloated legacy layers, providing a pure, minimal system based on <a href="https://musl.libc.org/">musl libc</a>, <a href="https://landley.net/toybox/">toybox</a>, <a href="https://www.mirbsd.org/mksh.htm">mksh</a>, <a href="http://smarden.org/runit/">runit</a>, the native <strong><a href="/docs/packages/">drop & sink</a></strong> package management ecosystem, and the <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel.</p>

<div class="release-banner">
latest release: <a href="/releases/">distill 0.1.0-alpha</a> (x86_64-musl-libre)
</div>

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
kernel built from <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> with proprietary blobs, tracking, and corporate branding removed
</li><li>
clean clang / llvm toolchain with samurai (samu) build engine
</li><li>
100% free software, zero corporate tracking, and completely gnu-free
</li>
</ul>
</details>

<details>
<summary>name & definition</summary>
<p>the name is derived from the definition of <strong>distill</strong> (<em>"to purify a substance by vaporizing and condensing it; to extract the essential essence while leaving behind all impurities and sediments"</em>).</p>
<p>distill strips out proprietary code, telemetry, and bloat to leave only a clean, pure operating system.</p>
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
