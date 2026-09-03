---
title: "components"
description: "technical breakdown of the distill linux architecture"
---

<p>distill is assembled from carefully selected, minimalist components designed to work in synergy without unnecessary abstraction layers.</p>

<details open>
<summary>1. kernel: linux-libre</summary>
<p>distill uses <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a>, a 100% free software kernel project based on the upstream linux kernel.</p>
<ul>
<li>all proprietary firmware blobs have been completely removed.</li>
<li>telemetry hooks and corporate analytics/tracing subsystems are stripped.</li>
<li>all gnu and corporate branding have been cleaned to preserve a pure, distraction-free environment.</li>
</ul>
</details>

<details open>
<summary>2. c library: musl libc</summary>
<p><a href="https://musl.libc.org/">musl</a> is a modern implementation of the c standard library designed for lightweight systems, embedded devices, and servers.</p>
</details>

<details open>
<summary>3. package manager: xbps</summary>
<p>the <a href="https://github.com/void-linux/xbps">x binary package system (xbps)</a> is a native package management system developed originally for void linux.</p>
</details>

<details open>
<summary>4. init system & supervision: runit</summary>
<p>distill uses <a href="http://smarden.org/runit/">runit</a> as its init scheme and service supervision daemon.</p>
</details>

<details open>
<summary>5. core utilities: toybox</summary>
<p><a href="https://landley.net/toybox/">toybox</a> combines common linux command-line utilities into a single multi-call binary under a clean 0-bsd license.</p>
</details>

<details open>
<summary>6. default shell: mksh</summary>
<p>the <a href="https://www.mirbsd.org/mksh.htm">mirbsd korn shell (mksh)</a> is the default interactive and system <code>/bin/sh</code> shell in distill.</p>
</details>
