# Reproducibility guide

This repository is the clean replication package for the revised 34-event manuscript.

## Clean-checkout replication

Use Python 3.11:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
python code/reproduce_submission.py
```

`code/reproduce_submission.py` first fetches and SHA-256 verifies the frozen large AUTM analysis input from the exact tested source snapshot, then regenerates:

1. publication-facing 100,000-assignment inference for the preferred 34-event sample and strict 29-event sensitivity;
2. event-time, balance, stack-composition, and leave-one-event-out diagnostics;
3. manuscript figures;
4. explicit row-level stacked datasets for the 34-event and 29-event designs.

The revision universe is reconstructed from the Paper 1 observed-policy sequence pinned to commit `25a9472b34334825b6d6c6a334f5b88eb00695b5`.

## Frozen large input

`data/merged_autm.csv` is not committed in this clean repository. `code/fetch_inputs.py` retrieves it from the public tested source snapshot:

`krish533/policy-communication-tech-transfer@6015d82feea1b3d593dfa329f2f1cb7a16349436`

Expected SHA-256:

`070f10179b34a0730d1f09ea3322d21e8f32e20d3036760df2adfef182aa2d4b`

If automatic retrieval is unavailable, place the exact file at `data/merged_autm.csv`; the fetcher accepts it only when the checksum matches. Users remain responsible for complying with any applicable AUTM data-use terms.

## Analysis hierarchy

- Preferred sample: **34 revisions (8 upward / 26 downward)**.
- Strict post-support sensitivity: **29 revisions (7 upward / 22 downward)**.
- Frozen benchmark: **25 revisions (6 upward / 19 downward)**.

The regression `N` counts stacked institution-year-event observations. It must not be interpreted as the number of independent policy events.

## Determinism and environment

- Python: 3.11.
- Package versions are pinned in `requirements.txt`.
- Monte Carlo seeds are fixed in code.
- Publication-facing direction-label inference uses 100,000 assignments per outcome.
- The 25-event benchmark uses exact enumeration of all `C(25,6)=177,100` label assignments.

## Expected publication-facing headline checks

For the preferred 34-event sample, the licensing estimate should reproduce approximately:

- gap: `0.49498236`;
- clustered SE: `0.13955734`;
- permutation p-value: `0.03199968`;
- pre-trend p-value: `0.31972163`.

For the strict 29-event sample, licensing should reproduce approximately:

- gap: `0.49876530`;
- clustered SE: `0.13256833`;
- permutation p-value: `0.02603974`;
- pre-trend p-value: `0.51665075`.

## Automated checks

The GitHub Actions workflow should verify that:

- frozen inputs pass checksum validation;
- the preferred and strict stacked datasets contain exactly 34 and 29 stacks;
- revision directions are `up` and `down` only;
- publication-facing result rows contain both `expanded34` and `strict29` samples;
- the frozen 25-event benchmark reproduces its exact-enumeration regression sample sizes;
- manuscript figures regenerate;
- the LaTeX manuscript compiles successfully;
- a replication artifact is uploaded.

## Human checks that code cannot resolve

Before journal submission, complete the following separately:

- blinded independent coauthor verification of the nine second-pass documentary classifications;
- final author list, order, and affiliations;
- author-contribution statement;
- funding statement;
- conflict/competing-interest statement as required by the target journal;
- journal-specific data/code availability wording and archival DOI/link;
- final visual inspection of the compiled PDF, tables, figures, citations, and appendix cross-references.

Do not mark these items complete merely because CI passes.
