![The fitting room between clients: a red fitting tape hanging at the left, a dress form in a half pinned toile, brass scales level and an open ledger ruled but unread, no readable mark anywhere](intro-banner.png)

# cc-diffconfig

![Early evening in the fitting room, the tape hanging beside the dark mirror and the name lettered in gilt across the mirror's lower corner](banner.png)

![Seat red measuring tape unrolled in a loose S from a small gilt case with a blank brass tag at its end, the heading plate](logo.png)

![Fitting room scene in three planes: dusk deepening at the window, a gilt highlight travelling down the ledger entries, the hanging tape tag turning slowly](scene.svg)



# cc-DiffConfig
Compares two configuration files (JSON, YAML, or INI) and highlights the differences, showing additions, deletions, and modifications using difflib. Can be used to track config drift.


![Running tape divider](sep-heavy.svg)

## Install
```
git clone https://github.com/ShadowGuard-AI/cc-diffconfig
cd cc-diffconfig
pip install -r requirements.txt
```


![Running tape divider](sep-light.svg)

## Usage
```
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
MIT License, see LICENSE.
