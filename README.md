# ftm-stmt

TUI diff tool for zavod `statements.pack` files. Lets you diff two arbitrary `.pack` files against each other

## Installation

```bash
alias ftm-stmt="uvx --from git+https://github.com/opensanctions/ftm-inspect.git ftm-stmt"
```

If you get compilation errors related to `pyICU`, see the [zavod install docs](https://zavod.opensanctions.org/install/) for how to set the correct magic environment variables (ideally at shell startup).

## Running

```bash
ftm-stmt diff LEFT RIGHT
```

### Example

```bash
ftm-stmt diff https://data.opensanctions.org/datasets/latest/us_ofac_sdn/statements.pack \
              data/datasets/us_ofac_sdn/statements.pack
```

### Using with zavod and the OpenSanctions archive

If you're running zavod locally and want to diff your local output against the published archive, use `zavod archive url` to resolve the URL for you:

```bash
ftm-stmt diff $(zavod archive url statements --latest datasets/us/ofac/us_ofac_sdn.yml) \
              data/datasets/us_ofac_sdn/statements.pack
```

If your dataset name is in `$DATASET`:

```bash
ftm-stmt diff $(zavod archive url statements --latest datasets/**/$DATASET.yml) \
              data/datasets/$DATASET/statements.pack
```

## TUI keybindings

| Key | Action |
|-----|--------|
| `t` | Toggle truncation |
| `w` | Toggle word wrap |
| `/` | Search |
| `n` / `N` | Next / previous match |
| `q` / `Esc` | Quit |
