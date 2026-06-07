# Governing Documents

The **constitution** and **bylaws** for the ML Paper Reading Group (Augusta University),
written in LaTeX.

| Document            | Source             | Output (after build)      |
| ------------------- | ------------------ | ------------------------- |
| Constitution        | `constitution.tex` | `build/constitution.pdf`  |
| Bylaws              | `bylaws.tex`       | `build/bylaws.pdf`        |

## Building

Pick the Makefile for your platform and copy it to `Makefile` (which is gitignored,
so your choice won't be committed):

```sh
# Linux (uses latexmk + a TeX distribution)
cp Makefile.linux Makefile

# macOS (uses tectonic)
cp Makefile.mac Makefile
```

Then build:

```sh
make all            # build both PDFs into build/
make constitution   # build constitution.pdf only
make bylaws         # build bylaws.pdf only
make open           # build + open the constitution
make open-bylaws    # build + open the bylaws
make clean          # remove build output
make help           # list all targets
```

### Live rebuild while editing

```sh
make watch          # rebuild constitution on change
make watch-bylaws   # rebuild bylaws on change
```

On Linux this uses `latexmk -pvc`. On macOS it uses `fswatch`
(`brew install fswatch`).

## Toolchain

- **Linux:** [`latexmk`](https://m%67.ctan.org/pkg/latexmk) plus a TeX distribution
  (e.g. TeX Live: `sudo apt install texlive-full` or a smaller subset).
- **macOS:** [Tectonic](https://tectonic-typesetting.github.io/)
  (`brew install tectonic`) — self-contained, downloads packages on demand.

Either toolchain works on either OS; the split just reflects the most common setup
for each. CI builds with Tectonic.

## Continuous integration

`.github/workflows/build.yml` builds both PDFs on every push to `main` and on pull
requests, and uploads them as a downloadable artifact named **documents**. A failed
build (e.g. a LaTeX error) fails the check.

## License

See [`UNLICENSE`](UNLICENSE).