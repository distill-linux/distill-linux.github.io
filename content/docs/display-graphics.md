---
title: "display & graphics"
description: "information regarding display servers, x11libre, and graphics support in distill"
---

<details open>
<summary>is wayland supported on distill?</summary>
<p><strong>wayland is not officially supported at this time.</strong></p>
<p>our primary focus for distill right now is delivering a clean, minimal baseline around <a href="https://github.com/X11Libre/xserver">X11Libre</a>.</p>
<p>wayland packages can still be installed through <code>xbps</code>, but support might be janky or require manual tinkering out of the box. native, officially tested wayland support is planned for a future release once our core stack has fully stabilized.</p>
</details>

<details open>
<summary>about x11libre</summary>
<p><a href="https://github.com/X11Libre/xserver">X11Libre</a> (hosted on <a href="https://github.com/X11Libre">GitHub</a>) is a community-managed fork and modernization of the X.Org Server (xserver). it continues development, maintenance, and cleanup of the classic x11 display protocol without premature deprecation or systemd entanglements.</p>

<p>key highlights of x11libre in distill:</p>
<ul>
<li><strong>independent seat management</strong>: native integration with <code>seatd</code> for unprivileged display sessions, completely eliminating <code>systemd-logind</code> hard dependencies.</li>
<li><strong>modern display defaults</strong>: includes TearFree and atomic modesetting enhancements enabled out of the box.</li>
<li><strong>streamlined codebase</strong>: active refactoring and cleanup of legacy cruft while maintaining rock-solid compatibility with window managers and x11 applications.</li>
<li><strong>100% libre friendly</strong>: pairs seamlessly with distill's linux-libre kernel and lightweight musl/runit stack.</li>
</ul>
</details>
