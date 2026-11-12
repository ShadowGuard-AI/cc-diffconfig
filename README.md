![The edges of two quilt panels close up where their square grids meet, one changed square picked out in mustard against the indigo and cream around it, the stitching sharp](intro-banner.png)

# cc-diffconfig

![A long work table holding two large quilt panels side by side, their cream, indigo, and faded rose squares in matching grids, hands smoothing the nearer panel flat and one mustard square standing out on it](banner.png)

![The overlapping corner of two quilt panels: cream and indigo squares with faded rose stitching and one single mustard square standing out at the overlap, the heading plate](logo.png)

![Fitting room scene in three planes: dusk deepening at the window, a gilt highlight travelling down the ledger entries, the hanging tape tag turning slowly](scene.svg)



Compares two configuration files (JSON, YAML, or INI) and highlights the differences, showing additions, deletions, and modifications using difflib. Can be used to track config drift.


![Running tape divider](sep-heavy.svg)

## Install
```sh
git clone https://github.com/ShadowGuard-AI/cc-diffconfig
cd cc-diffconfig
pip install -r requirements.txt
```


![Running tape divider](sep-light.svg)

## Usage
```sh
python3 main.py [--type json|yaml|ini] [--output OUTPUT] [--schema SCHEMA] FILE1 FILE2
```


![Running tape divider](sep-heavy.svg)

## Parameters
- `FILE1`: path to the first configuration file.
- `FILE2`: path to the second configuration file.
- `-h`: show help message and exit.
- `--type`: type of configuration files: `json`, `yaml`, or `ini`. Default: `yaml`.
- `--output`, `-o`: output file to write the diff to.
- `--schema`: path to a JSON schema file for validating the config files before diffing.


![Running tape divider](sep-heavy.svg)

## Verified behavior
- A JSON sample differing in one value and adding one key produced a unified diff with the changed and added lines.
- With `--output`, the diff was written to the named file.
- With `--schema`, a config that fails the schema exits 1 and no diff is produced.

> Carbon copy: a failing schema stops the run before any diff exists. No diff is produced, and that is the recorded result, not a fault in the book.

- Identical configs exit 0 and, when `--output` is given, no file is written at all, so a diff file left by an earlier run survives untouched.

> Carbon copy: identical files leave an earlier diff file untouched. When an output file is named and nothing had changed, no file is written at all.

- A missing input file exits 1.


![Running tape divider](sep-heavy.svg)

## License
MIT License, see [LICENSE](LICENSE).
