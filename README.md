# t.mcuhome.org

The **target host** for stable links printed by MCUHome tools. A URL
like `https://t.mcuhome.org/cli/docs/getting-started/0.1` is baked into
a released binary and must stay valid for that binary's lifetime — this
host is where such links point, so the tools never carry a link that
can rot.

Today the pages are served statically from this repository. Once the
documentation site (`docs.mcuhome.org`) exists, every path here becomes
a **redirect** to its real home — the inventory of paths in this
repository is the inventory of links the shipped tools carry.

## The path scheme (PO 2026-08-15)

```
/<source-repo>/<target-area>/<target-detail>/<version>/
```

- `source-repo` — the tool the link ships in (`cli`, later
  `dashboard`, …). Each source versions its links independently, so
  the same topic can point somewhere else per tool and per release.
- `target-area` / `target-detail` — what the page is about
  (`docs/getting-started`, `docs/device-supported-boards`, …).
- `version` — the linking tool's `major.minor` (e.g. `0.1`).

Rules:

- Never delete a path that a released binary links to; turn it into a
  redirect instead.
- Served via GitHub Pages with the custom domain `t.mcuhome.org`
  (`CNAME` file; DNS: CNAME record `t` → `mcu-home.github.io`).

## License

Apache-2.0.
