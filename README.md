# SVG Optimizer

Strip and minify SVG markup in your browser: no upload, no network, nothing leaves your machine.

**Live demo:** https://0xelitesystem.github.io/svg-optimizer/

## Use

1. Open the page, then paste SVG markup into the input box, drop a `.svg` file onto the drop zone, or click **Load sample**.
2. Toggle the cleanup passes you want:
   - **Remove comments** strips `<!-- ... -->` nodes.
   - **Remove metadata** drops `<metadata>` blocks (RDF, Dublin Core, license junk).
   - **Remove editor data** deletes Inkscape, Illustrator, and Sketch namespaced elements and attributes, plus the now unused `xmlns:` declarations that point at them.
   - **Collapse whitespace** removes whitespace-only text between elements while leaving `<text>`, `<tspan>`, `<style>`, and other text-bearing nodes untouched.
   - **Remove empty groups** deletes empty `<g>` and `<defs>` containers that carry no `id`.
   - **Minify styles** compresses `<style>` blocks and inline `style="..."` attributes.
   - **Remove title and desc** is off by default because those nodes power screen-reader labels.
   - **Round numbers** rounds coordinates, path data, transforms, and viewBox values to the chosen number of decimal places.
3. Read the size stats and confirm the before and after previews match, then click **Copy output** or **Download .svg**.

Parsing uses the browser's own XML engine, so malformed SVG is reported as an error instead of being silently mangled. Whitespace inside text elements and referenced groups (those with an `id`) are preserved so the rendered image stays identical.

## Why this exists

Most SVG minifiers are npm packages or paste-into-a-website services. The first needs a toolchain; the second ships your artwork, which sometimes carries client names, file paths, or unreleased logos, to a server you do not control. This tool is one static HTML file with no dependencies, no build step, and no telemetry. Read it, host it yourself, or keep a copy on a USB stick. It is MIT licensed, so it is yours to fork.

## Privacy

Everything runs in your browser. Your SVG is parsed, optimized, and previewed entirely on your machine using local JavaScript. There is no server call, no analytics, no external font, and no CDN. The page works fully offline once loaded.

## Run locally

```
git clone https://github.com/0xelitesystem/svg-optimizer.git
cd svg-optimizer
```

Then open `index.html` directly in a browser, or serve the folder:

```
python -m http.server
```

and visit `http://localhost:8000`.

## Build

There is no build. It is a single self-contained `index.html` with inline CSS and JavaScript. No bundler, no package manager, no dependencies.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright (c) 2026 0xelitesystem.

## Related

- JWT Inspector: https://github.com/0xelitesystem/jwt-inspector
- E-E-A-T signals reference: https://github.com/0xelitesystem/eeat-signals-reference
