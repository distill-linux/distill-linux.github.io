---
title: "package management (drop & sink)"
description: "guide to native package management with drop and sink in distill linux"
---

<p>distill linux utilizes its own native, dual-tool package management infrastructure: <strong>drop</strong> (binary package client) and <strong>sink</strong> (source builder and recipe engine). all packages are distributed as streaming <code>.drop</code> containers with cryptographically verified <code>.PORT</code> manifests.</p>

<details open>
<summary>drop (binary package manager)</summary>
<p><code>drop</code> is an ultra-minimal native binary package manager (<40 KB stripped) targeting pure musl libc with streaming zlib decompression and on-the-fly SHA-256 verification.</p>

<pre><code># configure official repository URL
export DROP_REPO_URL="https://distill-linux.github.io/pkgs"

# synchronize repository index catalog
drop update

# install a precompiled package from repository or local .drop archive
drop in &lt;pkg&gt;
drop in path/to/pkg-1.0.drop

# audit installed files against recorded SHA-256 hashes in .PORT
drop check &lt;pkg&gt;
drop check

# list installed packages, versions, and sizes
drop ls

# view package metadata from local database or catalog
drop info &lt;pkg&gt;

# uninstall package and tracked artifacts cleanly
drop rm &lt;pkg&gt;</code></pre>
</details>

<details open>
<summary>sink (source builder & recipe engine)</summary>
<p><code>sink</code> is the community build engine and ports helper. it orchestrates dependency checking via <code>drop</code>, checks out source commits with libgit2, executes build scripts inside isolated fakeroot sandboxes, automatically strips ELF binaries, calculates file hashes, and packages artifacts into <code>.drop</code> containers.</p>

<pre><code># inspect a .port recipe
sink info recipes/samurai.port

# build package into a .drop archive
sink make recipes/samurai.port

# build and automatically install artifact via drop
sink make -i recipes/samurai.port

# purge temporary scratch and build directories
sink clean</code></pre>
</details>

<details>
<summary>the .PORT container specification</summary>
<p>every package is built from a dual-role <code>.PORT</code> file that functions as both a human-readable build recipe for <code>sink</code> and a byte-verified installation manifest recorded by <code>drop</code> under <code>/var/db/drop/ports/&lt;name&gt;/.PORT</code>:</p>

<pre><code>PORT_NAME="samurai"
PORT_VERSION="1.2"
PORT_RELEASE="1"
PORT_DESC="Ninja-compatible build tool written in C"
PORT_URL="https://github.com/michaelforney/samurai.git"
PORT_COMMIT="1.2"
BUILD_SYSTEM="make"
BUILD_DEPS=""
RUN_DEPS=""

BUILD:
make CC=clang PREFIX=/usr
make DESTDIR="$PKG_FAKEROOT" PREFIX=/usr install

FILES:
/usr/bin/samu:8a0b2a40...
/usr/share/man/man1/samu.1:b4f535...</code></pre>
</details>
