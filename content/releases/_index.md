---
title: "releases"
description: "download official images and release notes for distill linux"
---

<p>all distill installation media are signed with our release key and built in isolated chroot containers.</p>

<div class="release-banner">
latest release: distill 0.1.0-alpha (x86_64-musl-libre)
</div>

<h3>downloads</h3>

<table>
<thead>
<tr>
<th>image</th>
<th>format</th>
<th>size</th>
<th>sha256 checksum</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>distill-0.1.0-x86_64-musl-base.iso</strong></td>
<td>live iso</td>
<td>~180 MB</td>
<td><code>e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855</code></td>
</tr>
<tr>
<td><strong>distill-0.1.0-x86_64-musl-rootfs.tar.xz</strong></td>
<td>rootfs archive</td>
<td>~45 MB</td>
<td><code>2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae</code></td>
</tr>
</tbody>
</table>

<details open>
<summary>release details</summary>
<ul>
<li><strong>architecture</strong>: <code>x86_64-musl</code></li>
<li><strong>kernel</strong>: <code>linux-libre 6.12.x</code> (unbranded & blob-free)</li>
<li><strong>base userland</strong>: <code>musl 1.2.5</code>, <code>toybox 0.8.11</code>, <code>mksh R59c</code>, <code>xbps 0.59.2</code>, <code>runit 2.1.2</code></li>
</ul>
</details>

<details>
<summary>gpg verification</summary>
<p>verify the downloaded iso against the official release signature:</p>
<pre><code># import release signing key
gpg --recv-keys 0xDISTILL_SIGNING_KEY_ID

# verify iso signature
gpg --verify distill-0.1.0-x86_64-musl-base.iso.sig distill-0.1.0-x86_64-musl-base.iso</code></pre>
</details>

<p>for installation steps, see the <a href="/docs/installation/">installation guide</a>.</p>
