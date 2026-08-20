# site-t.mcuhome.org

This is the site served at t.mcuhome.org; it answers the stable links that
MCUHome tools print. Every page here exists because a shipped tool names its
URL, so a person who hits a wall in that tool lands on an explanation.

## What this repository holds

- The published pages, one directory per link, each a self-contained
  `index.html` that needs nothing else to render.
- The path scheme `/<source-repo>/<target-area>/<target-detail>/<version>`,
  which lets a tool build a link out of what it already knows about itself.
- `index.html`, the page served at the root of the site.
- `CNAME`, which binds the site to the `t.mcuhome.org` domain.
- `.nojekyll`, which makes GitHub Pages serve the checked-in tree as it stands.

## Using it

A link is read, not called: open it in a browser. Its parts are the tool that
printed it (`cli`, `dashboard`), the area and the page inside that tool's
documentation, and the linking tool's own `major.minor` — which is how one
page can be answered differently for two releases of the same command:

```
https://t.mcuhome.org/cli/docs/getting-started/0.1
```

## How it fits into MCUHome

The links landing here are printed by
[mcuhome-cli](https://github.com/mcu-home/mcuhome-cli), under `cli/`, and by
[mcuhome-ui](https://github.com/mcu-home/mcuhome-ui), the web interface, under
`dashboard/` — in help text, in the output of a command that completed
something, and in refusals that a person has to act on. Neither tool imports
anything from here: what travels is a URL a human follows, so a page can be
rewritten without touching a release. That is also the constraint this
repository works under, because a binary that prints a path keeps printing it
for as long as it is installed.

## Layout

| Path | Purpose |
|---|---|
| `cli/` | Pages linked from the command-line interface |
| `dashboard/` | Pages linked from the web interface |

## Working on this repository

A page is plain HTML with no build step and no generator, so editing one and
reloading it is the whole loop; serving the tree instead shows the
directory-to-`index.html` resolution that every printed link relies on.

```
python3 -m http.server --directory . 8000
```

Publication is GitHub Pages serving the repository root of `main`, so a merge
is a release. A path is added, never moved and never removed: a new version of
a page takes a new `<version>` segment beside the old one.

## Documentation

- [t.mcuhome.org](https://t.mcuhome.org/) — the site as a reader sees it
- [`cli/`](cli/) — the pages the command-line interface links
- [`dashboard/`](dashboard/) — the pages the web interface links
- [github.com/mcu-home](https://github.com/mcu-home) — the MCUHome
  organization and its repositories

## Contributing and support

A wrong, unclear or missing page is a bug: report it in this repository's
[issue tracker](https://github.com/mcu-home/site-t.mcuhome.org/issues). How to
propose a change is described in the organization's
[contributing guide](https://github.com/mcu-home/.github/blob/main/CONTRIBUTING.md).

## License

Apache License 2.0; see [LICENSE](LICENSE).
