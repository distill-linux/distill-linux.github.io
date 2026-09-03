---
title: "userland: toybox & mksh"
description: "guide to the minimal userland environment in distill"
---

<p>distill replaces heavy gnu toolchains and gnu bash in base with <a href="https://landley.net/toybox/">toybox</a> and <a href="https://www.mirbsd.org/mksh.htm">mksh</a>.</p>

<details open>
<summary>toybox core utilities</summary>
<p>toybox provides standard posix utilities in a single, clean 0-bsd multi-call binary:</p>
<pre><code># list all available commands
toybox

# execute directly
toybox ls -la</code></pre>
</details>

<details open>
<summary>the mksh shell</summary>
<p><code>/bin/sh</code> points to the mirbsd korn shell. configure your prompt in <code>~/.mkshrc</code>:</p>
<pre><code># ~/.mkshrc
export PS1='$USER@$(hostname):$PWD $ '
export EDITOR="vi"
export PAGER="less"</code></pre>
</details>
