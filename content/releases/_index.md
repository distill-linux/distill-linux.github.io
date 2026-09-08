---
title: "releases"
description: "distill linux release status and edition roadmap"
---

<div class="release-banner">
distill linux is currently in active pre-release development. there are no official releases available yet.
</div>

<p>official live ISO images and release notes will be published here once distill reaches its initial release milestone. in the interim, live system images can be built from source using our build repository scripts.</p>

<h3>planned editions</h3>

<p>when official releases become available, distill will provide live ISO images for the following editions:</p>

<table>
<thead>
<tr>
<th>tier</th>
<th>edition</th>
<th>target hardware</th>
<th>kernel & firmware</th>
<th>status</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>tier 1 (main)</strong></td>
<td><strong>distill-standard</strong></td>
<td>standard x86_64 PCs, laptops, and servers</td>
<td>standard linux kernel with device drivers and firmware for common hardware</td>
<td><em>in development</em></td>
</tr>
<tr>
<td><strong>tier 2</strong></td>
<td><strong>distill-libre</strong></td>
<td>libre and open-hardware platforms</td>
<td>linux-libre kernel (deblobbed, zero non-free firmware blobs)</td>
<td><em>in development</em></td>
</tr>
<tr>
<td><strong>tier 2</strong></td>
<td><strong>distill-t2</strong></td>
<td>apple t2 macs (2018–2020 macbook pro, air, mini)</td>
<td>linux with t2 kernel patches (apple spi keyboard, trackpad, audio, wifi, uefi)</td>
<td><em>in development</em></td>
</tr>
</tbody>
</table>

<details open>
<summary>core system specifications</summary>
<ul>
<li><strong>architecture</strong>: <code>x86_64</code></li>
<li><strong>c library</strong>: <code>musl libc 1.2.5</code></li>
<li><strong>core utilities</strong>: <code>toybox 0.8.12</code></li>
<li><strong>default shell</strong>: <code>mksh R59c</code></li>
<li><strong>init system</strong>: <code>runit 2.1.2</code></li>
<li><strong>package management</strong>: <code>drop</code> (binary manager) & <code>sink</code> (source builder)</li>
<li><strong>compiler toolchain</strong>: <code>clang / llvm</code> & <code>samurai</code> (samu)</li>
</ul>
</details>

<details open>
<summary>edition details</summary>
<ul>
<li><strong>distill-standard (tier 1)</strong>: our primary edition. provides a minimal musl/toybox/mksh base while including standard hardware drivers and firmware for WiFi, GPU, and peripherals.</li>
<li><strong>distill-libre (tier 2)</strong>: built for users and systems requiring 100% free software, using the deblobbed linux-libre kernel.</li>
<li><strong>distill-t2 (tier 2)</strong>: includes out-of-tree Apple T2 drivers, enabling native Linux execution on 2018–2020 Intel Macs.</li>
</ul>
</details>

<p>for installation steps and build notes, see the <a href="/docs/installation/">installation guide</a>.</p>
