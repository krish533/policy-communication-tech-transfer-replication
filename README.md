# Replication package: Policy Communication and University Licensing

This is the clean replication package for the paper on university intellectual property policy revisions, policy communication, and technology transfer.

Only the material needed to reproduce the empirical results is included here:

- `README.md`
- `requirements.txt`
- `code/`
- `data/`

No manuscript files, drafting history, or development-only materials are included.

## Quick start

Use Python 3.11 from the repository root:

```bash
python -m venv .venv
source .venv/bin/activate
# Windows: .venv\Scripts\activate

python -m pip install --upgrade pip
pip install -r requirements.txt
python code/reproduce.py
```

The runner creates a `results/` directory and, where needed, generated files under `data/derived/`.

## What is reproduced

The code reconstructs the revision universe, applies the documentary event definitions, and reproduces the preferred 34-event stacked event study, the stricter 29-event sensitivity, balance and influence diagnostics, the continuous annual PCSI analyses, and the stricter PCSI-threshold sensitivity.

The preferred documentary sample contains 34 revisions at 32 universities: 8 upward and 26 downward revisions. The principal licensing estimate is approximately 0.495 log points with a clustered standard error of 0.140. The stricter 29-event sample produces an estimate of approximately 0.499 with a standard error of 0.133.

The analysis is observational. Revision direction is chosen by universities and should not be interpreted as randomly assigned.

## Data

The committed files in `data/` contain the policy-level PCSI input and documentary revision coding used to construct the event sample.

The AUTM analysis file is not duplicated here. `code/fetch_inputs.py` retrieves the frozen analysis input from the tested source snapshot and checks its SHA-256 checksum before use. The same script retrieves the sentence-level Paper 1 input used for the descriptive revision-content comparison.

Users are responsible for complying with applicable AUTM data-use terms.

## Main files

`code/reproduce.py` is the single replication entry point.

The core stacked event-study implementation is in `code/revision_event_study.py`. Publication-facing inference for the preferred and strict samples is in `code/final_expanded_inference.py`. The additional threshold sensitivity is in `code/threshold_sensitivity_final34.py`.

All numerical outputs are written to `results/`.
