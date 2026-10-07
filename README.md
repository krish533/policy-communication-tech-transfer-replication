# Replication package: Policy Communication and University Technology Transfer

This repository contains the clean replication and manuscript package for:

**When Universities Rewrite Their Intellectual-Property Policies: Policy Revisions, Policy Communication, and University Technology Transfer**

The paper studies documented university intellectual-property policy revisions using an observational stacked event-study design. The preferred documentary sample contains **34 revisions at 32 institutions (8 upward / 26 downward)**. A stricter post-support sensitivity contains **29 revisions (7 upward / 22 downward)**. The earlier September 25 specification with 25 events is retained only as a frozen provenance/robustness benchmark.

## Reproduce the submission results

Use Python 3.11 from the repository root:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python code/reproduce_submission.py
```

The canonical runner verifies/fetches the frozen inputs and regenerates the mechanical screen, descriptive tables (Tables 1, 2, A2, A10, A11), the Table 5 keyword comparison, the publication-facing 34/29 inference, diagnostics, supporting annual-panel analyses, figures, explicit stacked datasets, and the frozen 25-event benchmark. Publication-facing direction-label inference uses **100,000 assignments per outcome** with fixed seeds.

## Repository structure

- `code/` — canonical analysis and replication programs.
- `data/` — documentary revision coding plus instructions for the checksum-verified frozen AUTM input.
- `manuscript/` — current LaTeX manuscript source and appendix.
- `replication/` — documentary-review provenance.
- `results/` — generated numerical outputs documented by `results/README.md`.
- `REPRODUCIBILITY.md` — detailed clean-checkout instructions and automated checks.
- `TABLE_PROVENANCE.md` — table-by-table map of computational versus documentary/manual sources.
- `.github/workflows/` — end-to-end replication and manuscript-build CI.

## Empirical hierarchy

1. **Preferred:** 34 documentary-reviewed revisions, 8 upward and 26 downward.
2. **Strict sensitivity:** 29 revisions, 7 upward and 22 downward.
3. **Frozen benchmark:** September 25 25-event specification, retained for provenance/robustness.

The design is observational. The paper does not claim that supportive wording itself causally raises licensing.

## Source snapshot

This clean repository was separated from the development repository using the tested source snapshot:

`krish533/policy-communication-tech-transfer` commit `6015d82feea1b3d593dfa329f2f1cb7a16349436`.

The current manuscript source was copied from that passing snapshot; the clean repository then removed development-only scripts/history and added stricter clean-checkout CI and supporting annual-table replication.

## Reproducibility scope

CI is designed to reproduce the preferred/strict stacked analyses, supporting annual regressions, explicit stacked datasets, the frozen benchmark, figures, and compiled manuscript. Documentary classification remains human judgment. One inherited descriptive output—the original provision-coded appendix (Table A12)—is explicitly identified in `TABLE_PROVENANCE.md` because it comes from hand coding whose row-level source is not in the package.

