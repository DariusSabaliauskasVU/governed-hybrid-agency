# Language-model settings for the eligibility assessment

The title/abstract eligibility assessment was performed with a large language model
via the Claude Agent SDK.

| Setting | Value |
|---|---|
| Provider | Anthropic |
| Model | Claude Sonnet 5 |
| Access date | July 2026 |
| Passes per record | 1 (each record judged once) |
| Prompt | Fixed rubric in `llm_eligibility_prompt.md` |
| Output | Structured `INCLUDE` / `EXCLUDE` + short reason |
| Ambiguous handling | Defaulted to `EXCLUDE` |
| Decoding parameters | Default SDK settings (temperature, top-p, and max tokens were not overridden by the caller) |

Notes:
- The model's single-pass INCLUDE/EXCLUDE decision on each of the 660 pre-filtered
  records was the eligibility decision; the author did not independently re-screen
  all 660 records (see manuscript Sections 3.3 and 3.6). The author defined the
  eligibility criteria and rubric and consulted the full texts of all 119 included works.
- Reliability was assessed with a 30-record purposive author calibration
  (`calibration_30_combined.csv`) and a 50-record two-pass reproducibility check
  (`validation50_comparison.csv`; agreement 49/50, Cohen's kappa = 0.90).
