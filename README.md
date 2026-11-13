# Human checks (fill in the CSVs, keep the file names)

Please do not open `work/m4/human_sheet2_ab_key.json` or the result files while rating.
If two people rate, each fills a separate copy (`..._rater2.csv`) without discussing.

## Sheet 1 - benchmark check (30 issues, ~1.5 h) - `sheet1_benchmark_check_30.csv`
For each row open the Jira issue and the fix commit, then answer:
- `plausible(Y/N)`: overall, is this a usable benchmark item?
- `Q1_genuine_bug_fix(Y/N/?)`: is the commit a real bug fix for this issue (not a refactoring, test-only or feature change)?
- `Q2_gt_methods_are_root_cause(Y/Partial/N)`: are the listed ground-truth methods where the defect was (Partial = some are incidental edits)?
- `Q3_logs_relevant_to_bug(Y/N)`: do the pasted logs relate to this failure?
- `Q4_leak_remaining(Y/N)`: does the masked title/description still give away the faulty method or the fix?
- `Q5_masking_removed_needed_symptom_info(Y/N)`: did masking delete information needed to understand the symptom?
- `Q6_...emitted(Y/N/?)`: is any ground-truth method the method that printed the error/log line or sits at the top of the stack trace?

## Sheet 2 - explanation check (30 issues x 2 anonymous systems, ~2 h, optional) - `sheet2_explanation_check_30.csv`
A and B are two systems in random order per row. Score each with the rubric the LLM judge used:
- `evidence_alignment`: 0 = invents or contradicts log events / empty; 1 = partly reflects the logs or is generic; 2 = accurately and specifically reflects the log/stack symptoms.
- `causal_coherence`: 0 = no causal link or just restates the error; 1 = plausible partial link with gaps; 2 = clear mechanism from code behaviour to the symptom.
- `gt_mechanistic_match`: 0 = unrelated to the real defect; 1 = partial overlap (right file / caller / callee, imprecise); 2 = identifies the real defective region and mechanism.
