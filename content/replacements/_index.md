---
title: "replacements"
description: "components chosen in distill for simplicity and minimalism"
---

<p>distill replaces common desktop and server components with lightweight, standards-compliant alternatives:</p>

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
<td>linux (generic)</td>
<td>standard linux / <a href="https://www.fsfla.org/ikiwiki/selibre/linux-libre/">linux-libre</a></td>
<td>clean, minimal kernel configurations tailored to each release tier</td>
</tr>
<tr>
<td>gnu coreutils</td>
<td><a href="https://landley.net/toybox/">toybox</a></td>
<td>compact single-binary posix tools under 0-bsd license</td>
</tr>
<tr>
<td>gnu bash</td>
<td><a href="https://www.mirbsd.org/mksh.htm">mksh</a></td>
<td>lightweight, standards-compliant mirbsd korn shell with low memory usage</td>
</tr>
<tr>
<td>glibc</td>
<td><a href="https://musl.libc.org/">musl libc</a></td>
<td>small, standards-compliant C library</td>
</tr>
<tr>
<td>systemd</td>
<td><a href="http://smarden.org/runit/">runit</a></td>
<td>simple 3-stage init and process supervision with low resource usage</td>
</tr>
<tr>
<td>x.org xserver</td>
<td><a href="https://github.com/X11Libre/xserver">X11Libre</a></td>
<td>modernized X11 display server with seatd and TearFree support</td>
</tr>
<tr>
<td>apt / dnf / pacman</td>
<td><a href="/docs/packages/">drop & sink</a></td>
<td>native C package management (<40 KB drop client, streaming .drop format, SHA-256 verification)</td>
</tr>
<tr>
<td>gnu make / gcc</td>
<td><a href="/ports/">samurai & clang</a></td>
<td>fast C99 ninja-compatible build engine and modern LLVM toolchain</td>
</tr>
</tbody>
</table>
