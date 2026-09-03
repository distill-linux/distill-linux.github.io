---
title: "distill the purified operating system"
---

<div class="distill-backdrop">
    <img class="distill-hero" src="/images/distill-hero.svg" alt="distill">
</div>

<p><em>distill</em> is a purified, lightweight, and independent x86-64 <a href="https://en.wikipedia.org/wiki/Linux">linux</a> distribution forked from <a href="https://voidlinux.org/">void linux</a>. it strips all big corpo and proprietary code, providing a pure, lean system based on <a href="https://musl.libc.org/">musl libc</a>, <a href="https://landley.net/toybox/">toybox</a>, <a href="https://www.mirbsd.org/mksh.htm">mksh</a>, <a href="http://smarden.org/runit/">runit</a>, <a href="https://github.com/void-linux/xbps">xbps</a>, and the <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> kernel.</p>

<div class="release-banner">
latest release: <a href="/releases/">distill 0.1.0-alpha</a> (x86_64-musl-libre)
</div>

<details open>
<summary>features</summary>
<ul>
<li>
coreutils replaced with <a href="https://landley.net/toybox/">toybox</a> (0-bsd licensed)
</li><li>
shell replaced with <a href="https://www.mirbsd.org/mksh.htm">mksh</a> (mirbsd korn shell)
</li><li>
kernel switched to <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> with gnu and corporate branding and telemetry stripped out
</li><li>
uses void linux's <a href="https://musl.libc.org/">musl libc</a>, <a href="https://github.com/void-linux/xbps">xbps</a>, and <a href="http://smarden.org/runit/">runit</a>
</li><li>
zero proprietary blobs, corporate tracking, or telemetry
</li><li>
almost 100% gnu free
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
<p>pull requests and package templates are always welcome on <a href="https://git.distill-linux.org">git</a>.</p>
<p>contribute a package template to <a href="https://git.distill-linux.org/packages">the distill package tree</a>.</p>
</details>

<details>
<summary>discord</summary>
<p>join our community and chat with contributors on discord: <a href="https://discord.gg/distill">discord.gg/distill</a></p>
</details>
