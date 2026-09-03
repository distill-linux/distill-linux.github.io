---
title: "releases"
description: "download official ISO images and release notes for distill linux"
---

<p>distill produces live ISO images built from source through our independent cross-compilation pipeline. we offer a primary <strong>tier 1</strong> release alongside two specialized <strong>tier 2</strong> community editions:</p>

<div class="release-banner">
latest release: <strong>distill-standard 0.1.0-alpha</strong> (x86_64-musl)
</div>

<h3>available editions</h3>

<table>
<thead>
<tr>
<th>tier</th>
<th>edition</th>
<th>target hardware</th>
<th>kernel & firmware</th>
<th>download</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>tier 1 (main)</strong></td>
<td><strong>distill-standard</strong></td>
<td>standard x86_64 PCs, laptops, and servers</td>
<td>standard linux kernel with device drivers and firmware for common hardware</td>
<td><a href="#">distill-standard-0.1.0.iso</a></td>
</tr>
<tr>
<td><strong>tier 2</strong></td>
<td><strong>distill-libre</strong></td>
<td>libre and open-hardware platforms</td>
<td>linux-libre kernel (deblobbed, zero non-free firmware blobs)</td>
<td><a href="#">distill-libre-0.1.0.iso</a></td>
</tr>
<tr>
<td><strong>tier 2</strong></td>
<td><strong>distill-t2</strong></td>
<td>apple t2 macs (2018–2020 macbook pro, air, mini)</td>
<td>linux with t2 kernel patches (apple spi keyboard, trackpad, audio, wifi, uefi)</td>
<td><a href="#">distill-t2-0.1.0.iso</a></td>
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

<details>
<summary>verification</summary>

```sh
# verify iso checksum
sha256sum distill-standard-0.1.0.iso

# verify gpg signature
gpg --verify distill-standard-0.1.0.iso.sig distill-standard-0.1.0.iso
```

</details>

<p>for installation steps, see the <a href="/docs/installation/">installation guide</a>.</p>
