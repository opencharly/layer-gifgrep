# gifgrep

GIF search and download from the command line.

`gifgrep` installs the [gifgrep](https://github.com/steipete/gifgrep) Kong-based
CLI with `go install`, landing the binary at `~/go/bin/gifgrep` (`GOPATH=~/go`,
with `~/go/bin` appended to `PATH`). The install is verifiable without the
network: the binary is present and executable, and `gifgrep --help` runs (exit 0)
and prints its Kong usage banner listing the `search`/`tui`/`still`/`sheet`
subcommands.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `gifgrep` |
| Requires | `@github.com/opencharly/layer-golang` |
| Binary | `~/go/bin/gifgrep` |
| Env | `GOPATH=~/go`, `PATH` append `~/go/bin` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list:

```yaml
my-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-gifgrep:v2026.243.0409'
```

Then, inside the built image:

```bash
gifgrep --help           # Kong usage banner
gifgrep search "cats"    # search and download
```

## Layout

- `charly.yml` — the `gifgrep:` candy entity: the `require:` dep, the `env:` /
  `path_append:` block, the `go install` step, and the `check:` steps.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Family skill: `/charly-tools:gifgrep`
- `/charly-coder:golang` — the required Go toolchain dependency
- `/charly-tools:goplaces` — a sibling Go-based CLI
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
