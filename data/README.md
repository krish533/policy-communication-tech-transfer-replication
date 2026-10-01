# Data

This directory contains the documentary event-coding inputs committed with the clean replication package.

## Committed files

- `revision_codes_manual.csv` — frozen September 25 25-event benchmark coding.
- `revision_codes_rereview37.csv` — complete second-pass review of the 37 mechanically eligible non-benchmark pairs, including source-based review notes.

## Fetched frozen input

`merged_autm.csv` is intentionally not tracked in this clean repository. Run:

```bash
python code/fetch_inputs.py
```

or simply run the canonical `python code/reproduce_submission.py` command. The fetcher downloads the file from the exact tested source snapshot and verifies SHA-256 before use.

Expected `merged_autm.csv` SHA-256:

`070f10179b34a0730d1f09ea3322d21e8f32e20d3036760df2adfef182aa2d4b`

Users remain responsible for complying with applicable AUTM data-use terms.

## Generated data

`code/export_final_stacked_datasets.py` creates `data/derived/` with explicit row-level stacked datasets for the preferred 34-event design and strict 29-event sensitivity. These generated files are excluded from Git history and are produced in CI artifacts.
