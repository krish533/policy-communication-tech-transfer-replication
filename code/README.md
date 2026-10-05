# Code

The clean repository exposes one canonical publication workflow:

```bash
python code/reproduce_submission.py
```

It runs, in order:

1. `fetch_inputs.py` — retrieve and SHA-256 verify the frozen AUTM input and Paper 1's sentence file.
1. `mechanical_screen.py` — the 126 → 62 non-overlap and outcome-support screen (Table 2).
1. `descriptive_tables.py` — Tables 1, 2, A2, A10 and A11.
1. `revision_content_keywords.py` — Table 5, both panels.
2. `final_expanded_inference.py` — publication-facing 100,000-assignment inference.
3. `expanded34_diagnostics.py` — balance, event-time, stack-composition, and influence diagnostics.
4. `supporting_annual_analysis.py` — supporting annual-panel lag, robustness, circular-shift placebo, and revision-predictor analyses.
5. `build_expanded_manuscript_figures.py` — regenerate manuscript figures.
6. `export_final_stacked_datasets.py` — export explicit row-level stacked datasets.
7. `revision_replication.py` — frozen 25-event benchmark (Table 4, September-25 row).

Shared modules:

- `revision_event_study.py` — panel construction, revision-universe, stacking, fixed effects, and clustered inference.
- `revision_replication.py` — frozen 25-event exact-enumeration benchmark.
- `expanded_manual_revision_analysis.py` — preferred 34-event and strict 29-event sample construction plus shared permutation routines.

The 34-event documentary sample is the preferred current specification. The annual-panel models are supporting associational evidence. The 25-event sample is retained only as a frozen benchmark/provenance check.

See `../TABLE_PROVENANCE.md` for outputs that depend on documentary/manual descriptive coding rather than a purely computational pipeline.
