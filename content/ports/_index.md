---
title: "ports"
---

# distill ports & package repository

Official precompiled binary packages for Distill Linux (`x86_64-musl`), built from source with `sink` and managed via `drop`.

### Using with `drop`
```sh
# Configure repository
export DROP_REPO_URL="https://distill-linux.github.io/ports"

# Synchronize repository catalog
drop update

# Install a package
drop in samurai

# Verify package integrity against recorded SHA-256 hashes
drop check samurai
```

Plain-text catalog for scripts: [`index.tsv`](index.tsv)

---

## Available Packages

| Package | Version | Size | SHA-256 | Download |
|---|---|---|---|---|
| **samurai** | `1.2` | 26.8 KB | `6a6ca06b2dc038299ddb2843144fb160f4818b3f42a9ae6839843f3d1aba39a4` | [samurai-1.2.drop](samurai-1.2.drop) |

