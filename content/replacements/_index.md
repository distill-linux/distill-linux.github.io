---
title: "replacements"
description: "components replaced in distill to achieve purification"
---

<p>distill replaces bloated, proprietary, or telemetry-ridden components with clean, minimalist, and libre alternatives:</p>

<table>
<thead>
<tr>
<th>standard component</th>
<th>distill replacement</th>
<th>reason</th>
</tr>
</thead>
<tbody>
<tr>
<td>linux (with non-free blobs & telemetry)</td>
<td><a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a> (stripped)</td>
<td>100% free software kernel, 0 proprietary blobs or corporate tracking</td>
</tr>
<tr>
<td>gnu coreutils</td>
<td><a href="https://landley.net/toybox/">toybox</a></td>
<td>clean single-binary posix tools, 0-bsd licensed, 0 legacy bloat</td>
</tr>
<tr>
<td>gnu bash</td>
<td><a href="https://www.mirbsd.org/mksh.htm">mksh</a></td>
<td>mirbsd korn shell: lightweight, fast, strict posix standards</td>
</tr>
<tr>
<td>glibc</td>
<td><a href="https://musl.libc.org/">musl libc</a></td>
<td>standards-compliant, minimal memory footprint, clean c</td>
</tr>
<tr>
<td>systemd</td>
<td><a href="http://smarden.org/runit/">runit</a></td>
<td>simple 3-stage init and process supervision without complexity</td>
</tr>
<tr>
<td>x.org xserver (unmaintained upstream)</td>
<td><a href="https://github.com/X11Libre/xserver">X11Libre</a></td>
<td>community modernization with seatd support and TearFree by default</td>
</tr>
<tr>
<td>apt / dnf / pacman / xbps</td>
<td><a href="/docs/packages/">drop & sink</a></td>
<td>independent native C package management (<40 KB drop client, .drop containers, on-the-fly streaming SHA-256 verification)</td>
</tr>
<tr>
<td>gnu make / gcc</td>
<td><a href="/pkgs/">samurai & clang</a></td>
<td>ninja-compatible C99 build engine and LLVM/clang compiler toolchain</td>
</tr>
</tbody>
</table>
