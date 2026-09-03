---
title: "xbps package manager"
description: "guide to package management with xbps in distill"
---

<p>xbps (x binary package system) is the primary package manager for distill linux. it is fast, lightweight, and written in clean c.</p>

<details open>
<summary>basic operations</summary>
<pre><code># synchronize repository index caches
xbps-install -S

# install packages
xbps-install -S git neovim

# upgrade entire system
xbps-install -Su

# remove a package
xbps-remove neovim

# remove orphaned packages
xbps-remove -o

# clean package download cache
xbps-remove -O</code></pre>
</details>

<details open>
<summary>querying packages</summary>
<pre><code># search repositories for a package
xbps-query -Rs &lt;pattern&gt;

# list all installed packages
xbps-query -l

# view files owned by an installed package
xbps-query -f &lt;package-name&gt;</code></pre>
</details>

<details>
<summary>building from source with distill-packages</summary>
<p>compile packages from source in clean chroot containers using <code>xbps-src</code>:</p>
<pre><code>git clone https://git.distill-linux.org/distill-packages.git
cd distill-packages
./xbps-src binary-bootstrap
./xbps-src pkg &lt;package-name&gt;
xbps-install --repository hostdir/binpkgs &lt;package-name&gt;</code></pre>
</details>
