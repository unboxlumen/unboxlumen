# UnboxLumen

> Independent Software & Development Studio

---

## Products

| Product | Description | License | Source |
|---------|-------------|---------|--------|
| **libcaca-go** (nfilesart) | A pure Go colour ASCII-art toolkit, ported from the core of libcaca. No cgo. | WTFPL v2 | [GitHub](https://github.com/unboxlumen/libcaca-go) |

### libcaca-go

libcaca-go (the umbrella package is `art`, the project calls itself **nfilesart**) is a Go port of the **core** of [libcaca](https://github.com/cacalabs/libcaca) — the `caca/` library sources — and is released under the same **WTFPL v2** (Do What The Fuck You Want To Public License, Version 2). Every source file carries an attribution header naming the upstream file and license; see [`LICENSE`](https://github.com/unboxlumen/libcaca-go/blob/main/LICENSE).

The port targets libcaca **0.99.beta20** (upstream commit `de48e1a`) and is versioned in step with it: the current tag is **v0.99.20**. Requires Go 1.26 or newer. There is no cgo and no C dependency — `tcell` (MIT) and `golang.org/x/image` (BSD-3-Clause) are the only third-party modules.

```sh
go get github.com/unboxlumen/libcaca-go@v0.99.20
```

```go
import (
    "github.com/unboxlumen/libcaca-go/canvas"
    "github.com/unboxlumen/libcaca-go/codec"
    "github.com/unboxlumen/libcaca-go/dither"
)

d, _ := dither.New(img, dither.DefaultOptions())
c, _ := canvas.New(80, 24)
_ = d.Draw(c, 0, 0, 80, 24)
ansi, _ := codec.Export(c, "ansi")
```

| Area | State |
|---|---|
| Character grid, attributes, frames, dirty rectangles | complete, byte-compatible |
| Drawing primitives and transforms | complete |
| Dithering (6 algorithms, 7 colour modes, 3 charsets) | complete, golden-tested |
| Import: `caca`, `text`, `ansi`, `utf8`, `bin`, auto-detect | complete |
| Export: `caca`, `ansi`, `utf8`, `utf8cr`, `html`, `html3`, `bbfr`, `irc`, `ps`, `svg`, `tga`, `troff` | complete |
| Bitmap fonts (libcaca `.data`), FIGlet/TOIlet FIGfonts | complete |
| Display backends | `tcell` (pure Go) and `null` |
| Platform drivers, `caca0`/`conio` compatibility layers | not ported |

Packages: `canvas`, `dither`, `codec`, `font`, `charset`, `display`, `backend/tcell`, `backend/null`, `preview`. Two demos live under `cmd/`: `demo` (animated terminal scene) and `img2txt` (image → character art, mirroring libcaca's `img2txt` flags). Output is byte-compatible with libcaca for the native, ANSI, UTF-8, HTML, HTML3, BBCode, IRC, PostScript, SVG and troff formats.

> Upstream licensing note: only the WTFPL-licensed `caca/` core was used as the reference. The GPL/LGPL parts of the libcaca tree — `kernel/multiboot.h` (GPL), `src/aafire.c` and `examples/demo0.c` (LGPL) — were **not** used. See [`PROVENANCE.md`](https://github.com/unboxlumen/libcaca-go/blob/main/PROVENANCE.md).

---

## Website

**https://unboxlumen.com** — product pages, downloads, and documentation.
