---
title: "Ports"
---

<style>
/* Spread ports page to the edge of the screen */
article {
    max-width: none !important;
    margin-right: 2em !important;
}
@media (max-width: 650px) {
    article {
        margin-right: 0 !important;
    }
}

/* Arch/AUR Search Criteria Box */
.pkg-search-box {
    background: rgba(255, 255, 255, 0.45);
    border: 1px solid rgba(0, 0, 0, 0.22);
    border-radius: 4px;
    margin: 1em 0 1.5em 0;
    overflow: hidden;
}
.pkg-search-title {
    background: rgba(44, 54, 99, 0.12);
    border-bottom: 1px solid rgba(0, 0, 0, 0.18);
    padding: 0.5em 1em;
    font-weight: bold;
    color: #0c142e;
    font-size: 1.05em;
}
.pkg-search-form {
    padding: 0.8em 1em;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    gap: 1em;
    align-items: end;
}
@media (max-width: 750px) {
    .pkg-search-form {
        grid-template-columns: 1fr;
    }
}
.pkg-form-group {
    display: flex;
    flex-direction: column;
}
.pkg-form-group label {
    font-size: 0.85em;
    font-weight: bold;
    margin-bottom: 0.3em;
    color: #2c3663;
}
.pkg-form-group input, .pkg-form-group select {
    padding: 0.45em 0.6em;
    border: 1px solid rgba(0, 0, 0, 0.25);
    border-radius: 3px;
    background: #ffffff;
    font-size: 0.9em;
    box-sizing: border-box;
    width: 100%;
}
.pkg-stats {
    font-size: 0.9em;
    margin: 1.2em 0 0.6em 0;
    color: #101426;
}
.pkg-table {
    width: 100%;
    border-collapse: collapse;
    margin: 0.5em 0 1.5em 0;
    font-size: 0.9em;
    background: rgba(255, 255, 255, 0.5);
    border: 1px solid rgba(0, 0, 0, 0.18);
}
.pkg-table th {
    background: rgba(44, 54, 99, 0.12);
    border: 1px solid rgba(0, 0, 0, 0.18);
    padding: 0.6em 0.8em;
    text-align: left;
    color: #0c142e;
    white-space: nowrap;
}
.pkg-table td {
    border: 1px solid rgba(0, 0, 0, 0.18);
    padding: 0.6em 0.8em;
    vertical-align: top;
}
.pkg-table tr:hover {
    background: rgba(255, 255, 255, 0.75);
}
.pkg-name {
    font-weight: bold;
    font-size: 1.05em;
}
.pkg-desc {
    color: #1f293d;
    margin-top: 0.2em;
}
.pkg-tag {
    display: inline-block;
    padding: 0.15em 0.45em;
    background: rgba(170, 32, 34, 0.12);
    color: #aa2022;
    border-radius: 3px;
    font-size: 0.8em;
    font-family: monospace;
}
.pkg-meta {
    font-size: 0.8em;
    color: #555;
    white-space: nowrap;
}
.pkg-cmd {
    font-family: monospace;
    font-size: 0.82em;
    background: rgba(255, 255, 255, 0.65);
    border: 1px solid rgba(0, 0, 0, 0.18);
    color: #0c142e;
    padding: 0.2em 0.5em;
    border-radius: 3px;
    cursor: pointer;
    user-select: all;
    display: inline-block;
}
.pkg-cmd:hover {
    background: rgba(255, 255, 255, 0.95);
    border-color: #aa2022;
}
.catalog-link {
    float: right;
    font-size: 0.85em;
    margin-top: 0.5em;
}
</style>

<span class="catalog-link">Raw catalog: <a href="index.tsv">index.tsv</a></span>
<h1>Ports</h1>

<div class="pkg-search-box">
    <div class="pkg-search-title">Search Criteria</div>
    <div class="pkg-search-form">
        <div class="pkg-form-group">
            <label for="pkg-keywords">Keywords</label>
            <input type="text" id="pkg-keywords" placeholder="Search by name or description..." oninput="filterPackages()">
        </div>
        <div class="pkg-form-group">
            <label for="pkg-searchby">Search by</label>
            <select id="pkg-searchby" onchange="filterPackages()">
                <option value="all">Name, Description</option>
                <option value="name">Name Only</option>
                <option value="desc">Description Only</option>
            </select>
        </div>
        <div class="pkg-form-group">
            <label for="pkg-sort">Sort by</label>
            <select id="pkg-sort" onchange="sortPackages()">
                <option value="name-asc">Name (A-Z)</option>
                <option value="name-desc">Name (Z-A)</option>
                <option value="date-desc">Last Updated</option>
                <option value="size-desc">Size (Largest)</option>
            </select>
        </div>
    </div>
</div>

<div class="pkg-stats" id="pkg-stats">
    <strong>3 packages found.</strong> Page 1 of 1.
</div>

<table class="pkg-table" id="pkg-table">
    <thead>
        <tr>
            <th style="width: 18%;">Name</th>
            <th style="width: 10%;">Version</th>
            <th>Description</th>
            <th style="width: 14%;">Maintainer</th>
            <th style="width: 14%;">Last Updated</th>
            <th style="width: 12%;">Package</th>
        </tr>
    </thead>
    <tbody id="pkg-body">
        <tr class="pkg-row" data-name="drop" data-desc="native minimal binary package manager for distill linux" data-date="2026-09-02" data-size="14942">
            <td>
                <a class="pkg-name" href="https://github.com/distill-linux/drop" target="_blank" rel="noopener" title="View source code">drop</a>
            </td>
            <td>
                <span class="pkg-tag">0.1.0-1</span>
            </td>
            <td>
                <div class="pkg-desc">Native minimal binary package manager for Distill Linux</div>
                <div style="margin-top: 0.3em;">
                    <code class="pkg-cmd" title="Click to copy">drop in drop</code>
                </div>
            </td>
            <td class="pkg-meta">
                distill-core
            </td>
            <td class="pkg-meta">
                2026-09-02 (UTC)
            </td>
            <td>
                <a href="drop-0.1.0.drop" download style="font-weight: bold;">drop-0.1.0.drop</a><br>
                <span style="font-size: 0.8em; color: #666;">14.6 KB</span>
            </td>
        </tr>
        <tr class="pkg-row" data-name="samurai" data-desc="ninja-compatible build tool written in c" data-date="2026-09-02" data-size="27965">
            <td>
                <a class="pkg-name" href="https://github.com/michaelforney/samurai" target="_blank" rel="noopener" title="View source code">samurai</a>
            </td>
            <td>
                <span class="pkg-tag">1.2-1</span>
            </td>
            <td>
                <div class="pkg-desc">Ninja-compatible build tool written in C</div>
                <div style="margin-top: 0.3em;">
                    <code class="pkg-cmd" title="Click to copy">drop in samurai</code>
                </div>
            </td>
            <td class="pkg-meta">
                distill-core
            </td>
            <td class="pkg-meta">
                2026-09-02 (UTC)
            </td>
            <td>
                <a href="samurai-1.2.drop" download style="font-weight: bold;">samurai-1.2.drop</a><br>
                <span style="font-size: 0.8em; color: #666;">27.3 KB</span>
            </td>
        </tr>
        <tr class="pkg-row" data-name="sink" data-desc="community source builder and ports engine for distill linux" data-date="2026-09-02" data-size="13790">
            <td>
                <a class="pkg-name" href="https://github.com/distill-linux/sink" target="_blank" rel="noopener" title="View source code">sink</a>
            </td>
            <td>
                <span class="pkg-tag">0.1.0-1</span>
            </td>
            <td>
                <div class="pkg-desc">Community source builder and ports engine for Distill Linux</div>
                <div style="margin-top: 0.3em;">
                    <code class="pkg-cmd" title="Click to copy">drop in sink</code>
                </div>
            </td>
            <td class="pkg-meta">
                distill-core
            </td>
            <td class="pkg-meta">
                2026-09-02 (UTC)
            </td>
            <td>
                <a href="sink-0.1.0.drop" download style="font-weight: bold;">sink-0.1.0.drop</a><br>
                <span style="font-size: 0.8em; color: #666;">13.5 KB</span>
            </td>
        </tr>
    </tbody>
</table>

<script>
function filterPackages() {
    var query = document.getElementById('pkg-keywords').value.toLowerCase().trim();
    var mode = document.getElementById('pkg-searchby').value;
    var rows = document.querySelectorAll('#pkg-body .pkg-row');
    var visible = 0;

    rows.forEach(function(row) {
        var name = row.getAttribute('data-name') || '';
        var desc = row.getAttribute('data-desc') || '';
        var match = false;

        if (!query) {
            match = true;
        } else if (mode === 'name') {
            match = name.indexOf(query) !== -1;
        } else if (mode === 'desc') {
            match = desc.indexOf(query) !== -1;
        } else {
            match = (name.indexOf(query) !== -1) || (desc.indexOf(query) !== -1);
        }

        if (match) {
            row.style.display = '';
            visible++;
        } else {
            row.style.display = 'none';
        }
    });

    var stats = document.getElementById('pkg-stats');
    if (visible === 1) {
        stats.innerHTML = '<strong>1 package found.</strong> Page 1 of 1.';
    } else {
        stats.innerHTML = '<strong>' + visible + ' packages found.</strong> Page 1 of 1.';
    }
}

function sortPackages() {
    var sort = document.getElementById('pkg-sort').value;
    var tbody = document.getElementById('pkg-body');
    var rows = Array.from(tbody.querySelectorAll('.pkg-row'));

    rows.sort(function(a, b) {
        var nameA = a.getAttribute('data-name') || '';
        var nameB = b.getAttribute('data-name') || '';
        var sizeA = parseInt(a.getAttribute('data-size') || '0', 10);
        var sizeB = parseInt(b.getAttribute('data-size') || '0', 10);
        var dateA = a.getAttribute('data-date') || '';
        var dateB = b.getAttribute('data-date') || '';

        if (sort === 'name-asc') return nameA.localeCompare(nameB);
        if (sort === 'name-desc') return nameB.localeCompare(nameA);
        if (sort === 'size-desc') return sizeB - sizeA;
        if (sort === 'date-desc') return dateB.localeCompare(dateA);
        return 0;
    });

    rows.forEach(function(row) {
        tbody.appendChild(row);
    });
}
</script>
