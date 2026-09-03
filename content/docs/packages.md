---
title: "package management (drop & sink)"
description: "guide to native package management with drop and sink in distill linux"
---

<p>distill linux utilizes two dedicated native tools for package management:</p>
<ul>
<li><strong>drop</strong>: official precompiled binary package manager with built-in networking for core repositories.</li>
<li><strong>sink</strong>: community source builder and recipe orchestrator for user repositories (such as user ports).</li>
</ul>

<details open>
<summary>drop (binary package manager for core repositories)</summary>
<p><code>drop</code> is an ultra-minimal C client (<40 KB stripped) targeting musl libc with native networking, streaming zlib decompression, and on-the-fly SHA-256 verification. it interacts directly with core binary package repositories.</p>

```sh
# configure official repository URL
export DROP_REPO_URL="https://distill-linux.github.io/ports"

# synchronize repository catalog (index.tsv)
drop update

# install a precompiled package from core repository
drop in <package>

# install a local .drop package file
drop in path/to/pkg-1.0.drop

# audit installed files against recorded SHA-256 hashes
drop check <package>
drop check

# list installed packages, versions, and sizes
drop ls

# view package metadata from local database or catalog
drop info <package>

# uninstall package and tracked artifacts cleanly
drop rm <package>
```

</details>

<details open>
<summary>sink (source builder for user repositories)</summary>
<p><code>sink</code> is purely for building packages from source recipes in user repositories (like <code>distill-linux/usr-ports</code>). it clones git repositories or fetches source archives, builds them inside isolated fakeroot sandboxes, strips ELF binaries, packages artifacts into streaming <code>.drop</code> containers, and invokes <code>drop</code> to install them.</p>

```sh
# inspect a .port recipe
sink info recipes/samurai.port

# build package from recipe into a .drop archive
sink make recipes/samurai.port

# build and automatically install artifact via drop
sink make -i recipes/samurai.port

# purge temporary scratch and build directories
sink clean
```

</details>

<details>
<summary>the .PORT container specification</summary>
<p>every package is built from a dual-role <code>.PORT</code> file that functions as both a human-readable build recipe for <code>sink</code> and a byte-verified installation manifest recorded by <code>drop</code> under <code>/var/db/drop/ports/&lt;name&gt;/.PORT</code>:</p>

```ini
PORT_NAME="samurai"
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
/usr/bin/samu:8a0b2a4006d9c80f96ea973bedad05a04e588a8de51a9de0b94e195b11f12831
/usr/share/man/man1/samu.1:3fb96bc3c4b03657cb2184d0b271d4eb3d7e5d8719f96b996841fb2aa4a8523c
```

</details>
