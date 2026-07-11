# Language-model settings for the eligibility assessment

The title/abstract eligibility assessment was performed with a large language model
via the Claude Agent SDK.

| Setting | Value |
|---|---|
| Provider / model family | Anthropic Claude |
| Access date | July 2026 |
| Passes per record | 1 (each record judged once) |
| Prompt | Fixed rubric in `llm_eligibility_prompt.md` |
| Output | Structured `INCLUDE` / `EXCLUDE` + short reason |
| Ambiguous handling | Defaulted to `EXCLUDE` |
| Decoding parameters | Default SDK settings (temperature, top-p, and max tokens were not overridden by the caller) |

Notes:
- Final inclusion decisions were made by the author; the model provided title/abstract
  eligibility decisions for the pre-filtered records (see manuscript Section 3.3).
- Reliability was assessed with a 30-record author calibration
  (`calibration_30_combined.csv`) and a 50-record two-pass reproducibility check
  (`validation50_comparison.csv`; agreement 49/50, Cohen's kappa = 0.90).
