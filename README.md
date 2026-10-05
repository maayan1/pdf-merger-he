# PDF Merger (Hebrew UI)

A small, single-purpose tool for merging multiple PDF files into one — runs entirely in the browser, with a **true zero-network-request guarantee**.

## Why

I needed to merge personal PDFs without uploading them anywhere — not even to a CDN. Existing tools required a server upload, so I built my own with one hard requirement: **zero network requests, including for loading libraries**. I verified this empirically by disconnecting the internet entirely and confirming the merge still works.

## Features

- Select multiple PDF files at once
- Reorder files before merging (↑ / ↓)
- Remove a file from the list, or clear the list
- Accessible status messages (`aria-live`) for success/error states
- Clear, actionable error handling for corrupted/protected PDFs (including a practical workaround: print to "Microsoft Print to PDF" to produce a valid copy)
- Full RTL and Hebrew UI support
- [`pdf-lib`](https://github.com/Hopding/pdf-lib) is vendored locally in this repo (`lib/pdf-lib.min.js`) instead of loaded from a CDN — so the tool works on a machine that is fully disconnected from the internet, with zero network dependency even on first run

## How it works

All logic is plain JavaScript (no framework): each file is loaded with `PDFDocument.load`, pages are copied into one output document with `copyPages`, and the result is served as a client-side download via `Blob` + `URL.createObjectURL`. There is no `fetch`, no API call, and no network dependency at all — not even for the PDF library itself, which is vendored locally in `lib/pdf-lib.min.js` rather than pulled from a CDN.

## Run it

Just open `index.html` in a browser — no build step, no install.

```bash
git clone https://github.com/maayan1/pdf-merger-he.git
cd pdf-merger-he
open index.html   # or just double-click the file
```

## Built with AI-assisted development

Built in collaboration with an AI assistant (ChatGPT), while I drove the hard requirements myself: a self-contained file, zero network dependency, and empirical verification (disconnecting the internet) before accepting the result. This reflects how I actually work: using AI to speed up implementation, while staying in control of the requirements, the architecture, and verifying the result actually meets them.

## License

MIT — see [LICENSE](LICENSE).
