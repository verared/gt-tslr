# True Local Solar Time (EXPERIMENTAL)

Part of the **Gerarion** reference suite (verared/gerarion `v3.2.2`,
Gerarion Universal Standard). This directory is an **export package**
ready to be published (or consumed) as the `verared/gt-tslr` satellite
repository; it keeps the base repository's relative layout so modules
compose cleanly.

## The unique problem it solves

Optional astronomical verification for Level-3 forensic evidence. EXPERIMENTAL PROFILE: separate from the normative core; no reference implementation yet. The initial structure is ready for independent development.

## Normative status

- **EXPERIMENTAL** (`maturity: experimental`) — baseline `v3.2.2` (frozen arithmetic and vectors:
  GUS v3.0.0).
- Included specification(s): `docs/specs/TSLR.es.md`, `docs/specs/TSLR.en.md`
- Verifiable integrity manifest: [`EXPORT-MANIFEST.json`](EXPORT-MANIFEST.json)
- Official compatibility matrix: [`COMPATIBILITY.md`](https://github.com/verared/gerarion/blob/v3.2.2/COMPATIBILITY.md)

## Dependencies

- `gt-core` (*verared/gt-core*): tipos base y servicios del núcleo.
Common base: `verared/gerarion` `3.2.2`.

## Contents

- `EXPORT-MANIFEST.json`
- `LICENSE`
- `NOTICE`
- `docs/specs/TSLR.en.md`
- `docs/specs/TSLR.es.md`
- `src/.gitkeep`
- `tests/.gitkeep`
- `vectors/.gitkeep`

## Offline usage

No network, accounts, package registries, or frameworks required:

```bash
python3 -c 'import sys; sys.path.insert(0, "src"); import gerarion'
```

## Verification

With Python ≥ 3.9 and `reuse` installed:

```bash
reuse lint                                    # licensing 100 %
# (sin código compilable en este módulo)
```

From `verared/gerarion`, full integrity against `EXPORT-MANIFEST.json` is verified with:

```bash
python3 tools/export_module.py --verify-existing /path/to/gt-tslr
```

## Synchronisation contract with `verared/gerarion`

This package is **generated, never hand-edited**: it is regenerated
byte for byte from `verared/gerarion v3.2.2` with
`python3 tools/export_module.py --module gt-tslr --out <dir>`. The
normative source of truth (specifications, CC0 vectors, reference
cores for the three platforms, and the full test suite) stays in
`verared/gerarion`; `verared/gt-tslr` satellites consume it and never fork the
arithmetic. Updates flow by regenerating the export from a tag of the
base repository — never by editing exported files.
