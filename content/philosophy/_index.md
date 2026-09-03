---
title: "philosophy"
description: "the design goals behind distill linux"
---

<p>distill is designed around minimalism, simplicity, and architectural independence.</p>

<h3>1. minimalism & simplicity</h3>

<p>modern operating systems often include layers of unnecessary background services, complex configuration systems, and overlapping utilities. distill keeps the base system small, verifiable, and focused on essential unix functionality.</p>

<h3>2. core principles</h3>

<details open>
<summary>independent & built from scratch</summary>
<p>distill does not fork an upstream distribution. it is cross-compiled from source through a multi-stage bootstrap pipeline (stage0 to stage3), establishing full control and transparency over every binary on the root filesystem.</p>
</details>

<details open>
<summary>editions for different needs</summary>
<p>we provide distinct editions rather than forcing a one-size-fits-all approach:</p>
<ul>
<li><strong>distill-standard (tier 1 / main)</strong>: our primary release, providing a minimal musl/toybox/mksh base with standard hardware drivers and firmware.</li>
<li><strong>distill-libre (tier 2)</strong>: a 100% free-software edition with a deblobbed linux-libre kernel for fully open hardware.</li>
<li><strong>distill-t2 (tier 2)</strong>: dedicated kernel support for Apple T2 Mac computers.</li>
</ul>
</details>

<details open>
<summary>compact userland (toybox & mksh)</summary>
<p>distill uses <a href="https://landley.net/toybox/">toybox</a> and <a href="https://www.mirbsd.org/mksh.htm">mksh</a> for its core utilities:</p>
<ul>
<li><strong>toybox</strong>: provides standard posix utilities in a compact single binary under a 0-bsd license.</li>
<li><strong>mksh</strong>: the mirbsd korn shell is small, standards-compliant, and fast.</li>
</ul>
</details>

<details open>
<summary>musl libc</summary>
<p><a href="https://musl.libc.org/">musl libc</a> is lightweight, adheres to posix and C standards, produces small binaries, and avoids unnecessary complexity.</p>
</details>

<details open>
<summary>native package management: drop & sink</summary>
<p>package management is handled by two focused C tools:</p>
<ol>
<li><strong>drop</strong>: a compact (<40 KB stripped) package installer that checks SHA-256 hashes on the fly and tracks installed files.</li>
<li><strong>sink</strong>: a source builder that handles git checkouts, builds packages in fakeroot sandboxes, strips binaries, and produces <code>.drop</code> archives.</li>
</ol>
</details>

<details open>
<summary>init & service supervision: runit</summary>
<p><a href="http://smarden.org/runit/">runit</a> is a fast, simple service supervisor that manages daemons and system startup:</p>
<ul>
<li>deterministic 3-stage initialization without complex dependency graphs.</li>
<li>instant daemon restart upon abnormal termination.</li>
<li>minimal resource consumption and simple shell run scripts.</li>
</ul>
</details>
