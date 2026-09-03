---
title: "service management with runit"
description: "managing services and daemons using runit in distill"
---

<p>distill uses <a href="http://smarden.org/runit/">runit</a> for init and process supervision. runit operates without the complexity and overhead of systemd.</p>

<details open>
<summary>enabling & disabling services</summary>
<p>services in distill reside in <code>/etc/sv/</code> and are enabled by symlinking into <code>/var/service/</code>:</p>
<pre><code># enable a service
ln -s /etc/sv/dhcpcd /var/service/

# disable a service
rm /var/service/dhcpcd</code></pre>
</details>

<details open>
<summary>controlling services (sv)</summary>
<pre><code># check status
sv status dhcpcd

# start / stop / restart
sv up dhcpcd
sv down dhcpcd
sv restart dhcpcd

# reload configuration via SIGHUP
sv hup dhcpcd</code></pre>
</details>

<details>
<summary>writing a custom service</summary>
<p>a service in runit is simply an executable script named <code>run</code> inside its directory:</p>
<pre><code>#!/bin/sh
exec 2&gt;&amp;1
echo "Starting daemon..."
exec /usr/bin/mydaemon --foreground</code></pre>
</details>
