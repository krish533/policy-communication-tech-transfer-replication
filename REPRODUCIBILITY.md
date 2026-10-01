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
3. supporting annual-panel lag, robustness, placebo, and revision-predictor analyses;
4. manuscript figures;
5. explicit row-level stacked datasets for the 34-event and 29-event designs.

The revision universe is reconstructed from the Paper 1 observed-policy sequence pinned to commit `25a9472b34334825b6d6c6a334f5b88eb00695b5`.

See `TABLE_PROVENANCE.md` for a table-by-table distinction between computational outputs and documentary/manual descriptive coding.

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

## Environment and numerical reproducibility

- Python: 3.11.
- Package versions are pinned in `requirements.txt`.
- Monte Carlo seeds are fixed in code.
- Publication-facing direction-label inference uses 100,000 assignments per outcome.
- The supporting circular-shift placebo uses 1,000 fixed-seed shifts.
- The 25-event benchmark uses exact enumeration of all `C(25,6)=177,100` label assignments.

Point estimates, standard errors, sample definitions, and stack sizes are checked at tight numerical tolerances. Monte Carlo p-values are not required to be bit-identical across numerical libraries: assignments that lie essentially on the observed-statistic boundary can differ by a handful of counts across BLAS/platform implementations. CI therefore checks the publication-relevant tolerance (for example, the preferred licensing permutation p-value must remain approximately `0.032`).

## Expected publication-facing headline checks

For the preferred 34-event sample, licensing should reproduce approximately:

- gap: `0.49498236`;
- clustered SE: `0.13955734`;
- permutation p-value: `0.032`;
- pre-trend p-value: `0.31972163`;
- stacked rows: `26,679`.

For the strict 29-event sample, licensing should reproduce approximately:

- gap: `0.49876530`;
- clustered SE: `0.13256833`;
- permutation p-value: `0.026`;
- pre-trend p-value: `0.51665075`;
- stacked rows: `23,186`.

The supporting annual filing-margin specification should reproduce the manuscript sample sizes of 2,271 observations at lag 1 and 2,132 at lag 2, with coefficients approximately 0.939 and 1.201. The 1,000-shift circular placebo should reproduce a p-value of approximately 0.017.

## Automated checks

The GitHub Actions workflow verifies that:

- frozen inputs pass checksum validation;
- the preferred and strict stacked datasets contain exactly 34 and 29 stacks;
- revision directions are `up` and `down` only;
- publication-facing result rows contain both `expanded34` and `strict29` samples;
- headline coefficients, SEs, pre-tests, rounded Monte Carlo p-values, and stacked-row counts reproduce;
- supporting annual-panel sample sizes/coefficients and the circular-shift placebo reproduce;
- the frozen 25-event benchmark reproduces its exact-enumeration regression sample sizes;
- manuscript figures regenerate;
- the LaTeX manuscript compiles successfully;
- a checksum-stamped replication artifact is uploaded.

## Human/source checks that automation cannot resolve

Before journal submission, complete the following separately:

- blinded independent coauthor verification of the nine second-pass documentary classifications;
- final author list, order, and affiliations;
- author-contribution statement;
- funding statement;
- conflict/competing-interest statement as required by the target journal;
- journal-specific data/code availability wording and archival DOI/link;
- final visual inspection of the compiled PDF, tables, figures, citations, and appendix cross-references;
- preserve the row-level source for the original provision-coding appendix if that appendix is to be described as fully computationally reproducible.

Do not mark these items complete merely because CI passes.
