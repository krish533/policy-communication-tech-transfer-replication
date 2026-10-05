# Generated results

This directory is populated by the replication code. Publication-facing event-study outputs include:

- `expanded_manual_sample_results.csv`
- `expanded_manual_sample_summary.json`
- `expanded34_event_list.csv`
- `strict29_event_list.csv`
- `expanded_event_time_paths.csv`
- `expanded34_balance.csv`
- `expanded34_event_level_balance_data.csv`
- `expanded34_stack_composition.csv`
- `expanded34_leave_one_out.csv`
- `expanded34_diagnostics_summary.json`

Sample-construction and descriptive outputs:

- `mechanical_screen.csv`
- `descriptive_table1.csv`, `descriptive_tableA2.csv`, `descriptive_tableA10.csv`, `descriptive_tableA11.csv`
- `descriptive_summary.json` (Table 1 panel facts and Table 2 counts)
- `revision_content_keywords.csv` (Table 5)

Supporting annual-panel outputs include:

- `supporting_annual_lags.csv`
- `supporting_annual_robustness.csv`
- `revision_predictors.csv`
- `supporting_annual_summary.json`

The frozen benchmark script additionally writes `table3_reproduced.csv` and `table3_reproduced.json`.

Generated numerical outputs are rebuilt in CI rather than treated as immutable source files. The manuscript contains rounded publication values; CI checks the underlying regenerated outputs and uploads them with the replication artifact.
