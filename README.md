# t.mcuhome.org

The **target host** for stable links printed by MCUHome tools. A URL
like `https://t.mcuhome.org/docs/getting-started/0.1` is baked into a
released binary and must stay valid for that binary's lifetime — this
host is where such links point, so the tools never carry a link that
can rot.

Today the pages under `docs/` are served statically from this
repository. Once the documentation site (`docs.mcuhome.org`) exists,
every path here becomes a **redirect** to its real home — the inventory
of paths in this repository is the inventory of links the shipped tools
carry.

Rules:

- One directory per link target, versioned by the linking tool's
  `major.minor` (e.g. `docs/getting-started/0.1/`).
- Never delete a path that a released binary links to; turn it into a
  redirect instead.
- Served via GitHub Pages with the custom domain `t.mcuhome.org`
  (`CNAME` file; DNS: CNAME record `t` → `mcu-home.github.io`).

## License

Apache-2.0.
