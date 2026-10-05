# Derived stacked event-study datasets

These files make the actual row-level inputs to the updated stacked event-study design explicit.

## Files

- `final_stacked_event_dataset_expanded34.csv`: preferred sample, 34 policy-revision events (8 upward, 26 downward).
- `final_stacked_event_dataset_strict29.csv`: stricter sensitivity sample, 29 events (7 upward, 22 downward).

## Row interpretation

A row is a **university-year within a particular event stack**. It is not an independent policy revision. The same comparison university-year can appear in more than one stack when it is a valid clean control for multiple policy revisions.

The preferred stacked file has 26,679 rows, 34 stacks, and 149 distinct panel institutions. The strict file has 23,186 rows, 29 stacks, and 149 distinct panel institutions.

## Key variables

- `stack` / `event_id`: policy-revision stack identifier.
- `event_institution`: university whose policy revision defines the stack.
- `event_year`: documented revision year used to center event time.
- `event_direction_meta`: upward/supportive or downward/restrictive PCSI revision.
- `delta_pcsi`: change in PCSI from predecessor to successor policy.
- `institution`, `year`: panel university-year.
- `event_time`: calendar year minus event year; main window is -4 through +5.
- `treated`: 1 for the revising university in that stack, 0 for clean controls.
- `control`: 1 for clean controls.
- `size_tercile`, `private`, `ln_research_exp`: main design controls / fixed-effect strata inputs.
- `ln_licenses`, `filing_margin`, `ln_new_patent_apps`, `ln_patents_issued`, `ln_disclosures`: five main outcomes.

Outcome-specific regressions drop rows with missing values required for that outcome and the common regression covariates, so the reported regression N is smaller than the raw number of stacked rows.

## Construction

Generated from `data/merged_autm.csv`, the pinned Paper 1 observed-policy sequence, `data/revision_codes_manual.csv`, and `data/revision_codes_rereview37.csv` using the same panel, revision-universe, clean-control, and event-window code used by the manuscript.
