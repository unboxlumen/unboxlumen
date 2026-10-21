# UnboxLumen

> Independent Software & Development Studio
>
> We build Android apps: a lightweight browser, a file manager, and a local search tool.

---

## Products

| Product | Description | Latest Release | Size |
|---------|-------------|---------------|------|
| **N Browser** (nBrowser) | Lightweight, customizable Android browser. System WebView, no bundled engine. | [v0.0.18](https://github.com/unboxlumen/nbrowser/releases/tag/v0.0.18) | ~2.1 MB |
| **N Files** (nFiles) | A file manager for your phone. Browse, preview, remote, share — all in one. | [v0.0.4](https://github.com/unboxlumen/filemanager/releases/tag/v0.0.4) | ~45.1 MB |
| **N Search** (nSearch) | Local full-text file search. Multi-language tokenization, privacy-first. | [v0.0.1](https://github.com/unboxlumen/nsearch/releases/tag/v0.0.1) | ~21.4 MB |
| **nDebugBar** | Open-source Android Library (MIT), a debug toolbar component. | v1.0.0 coming soon | — |

> Full product catalog and guidelines: [PRODUCTS.md](PRODUCTS.md). Detailed specs in each subdirectory's `PRODUCT.md`.

---

## Website

**https://unboxlumen.com** — product pages, downloads, and documentation.

---

## Update Check Rules

- Release builds check only the release channel; debug builds check only the debug channel. The two channels never cross.
- Updates are matched by asset filename, then compared by version number.
