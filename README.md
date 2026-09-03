# distill linux website

Official static website for **Distill Linux** - a minimal, independent from-scratch Linux distribution based on `musl`, `drop`, `sink`, `runit`, `toybox`, `mksh`, and `linux-libre`.

Built with **Hugo** and pure **HTML / CSS** (0 JavaScript), inspired by the minimalist aesthetic of [derivelinux.org](https://derivelinux.org/) and cat-v/werc.

---

## Local Development

To run the site locally:

```sh
# Start Hugo development server
hugo server -D
```

Then navigate to `http://localhost:1313/` in your browser.

---

## Building

To generate the static HTML files:

```sh
hugo --minify
```

The output will be placed in the `public/` directory.

---

## Deployment (GitHub Pages)

This repository includes a ready-to-use GitHub Actions workflow located at `.github/workflows/gh-pages.yml`.

1. Push this repository to your GitHub account (branch `main`).
2. Go to your repository **Settings** &rarr; **Pages**.
3. Under **Build and deployment**, select **Source** &rarr; **GitHub Actions**.
4. Every push to `main` will automatically build and publish your site!
