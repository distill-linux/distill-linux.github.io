---
title: "packages"
---

# distill ports & package repository

Official precompiled binary packages for Distill Linux (`x86_64-musl`), built purely with `clang`, managed via `drop`, and packaged with `sink`.

### Using with `drop`
```sh
# Configure repository
export DROP_REPO_URL="https://distill-linux.github.io/pkgs"

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
| **samurai** | `1.2` | 27.3 KB | `8a0b2a4006d9c80f96ea973bedad05a04e588a8de51a9de0b94e195b11f12831` | [samurai-1.2.drop](samurai-1.2.drop) |
