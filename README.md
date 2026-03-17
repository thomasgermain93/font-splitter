# Variable Font Splitter

Drop a variable font file, get individual `.woff2` files for each weight — all in the browser, no upload, no backend.

## Features

- Drag & drop `.woff`, `.woff2`, `.ttf` or `.otf`
- Auto-detects the weight range and available axes
- Generates one `.woff2` per weight (100–900)
- Downloads everything as a `.zip`
- Runs entirely client-side via [Pyodide](https://pyodide.org) + [fonttools](https://fonttools.readthedocs.io)

## Usage

1. Open the app
2. Drop a variable font file onto the drop zone
3. Wait for analysis (~2s)
4. Click **Generate & Download ZIP**

> **Note:** The first load takes ~15 seconds to download the Python runtime (Pyodide + fonttools). Subsequent visits are instant thanks to browser caching.

## How it works

[fonttools](https://github.com/fonttools/fonttools) compiled to WebAssembly via [Pyodide](https://pyodide.org) runs directly in the browser. For each target weight, `varLib.instancer` pins the `wght` axis and all other axes to their defaults, producing a fully static font file. [JSZip](https://stuk.github.io/jszip/) bundles the results.

No font data ever leaves your machine.

## Deploy

Static single-file app — works with any static host.

[![Deploy to Cloudflare Pages](https://deploy.workers.cloudflare.com/button)](https://dash.cloudflare.com/)

Or clone and open `index.html` directly in a browser.

## Stack

- Pyodide 0.26.2
- fonttools 4.x
- JSZip 3.10
- Zero dependencies, zero build step
