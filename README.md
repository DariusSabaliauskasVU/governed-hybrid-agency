# Governed Hybrid Agency — Reproducibility Package

Supplementary data and reproducibility materials for the review:

> **Governed Hybrid Agency: A Critical Evidence Map of Cognitive Architectures for Foundation-Model Agents.**
> D. Sabaliauskas & A. Dirzyte. Submitted to the *Journal of Artificial Intelligence Research* (JAIR), Surveys track.

All files share a single stable key, `record_id`, that links the de-duplicated corpus (0–1029) across every stage, so any record can be traced from identification through screening to final coding.

## Contents

| File | Description |
|---|---|
| `search_protocol_scopus_wos.md` | PRISMA-based search protocol: research questions, concept blocks, exact Scopus and Web of Science query strings, filters, eligibility criteria, and the screening procedure as executed. |
| `prefilter_log_1030.csv` | Audit of the 1,030 de-duplicated records: automated pre-filter decision (`PASS`/`EXCLUDE`) and reason. Covers the 1,173→1,030 (duplicates) and 1,030→660 (pre-filter) steps. |
| `screening_log_660.csv` | Eligibility decisions for the 660 assessed records (`record_id`, decision, reason, metadata). |
| `llm_eligibility_prompt.md` | The fixed rubric/prompt used for the LLM-assisted eligibility assessment. |
| `llm_model_settings.md` | Model, access date, single-pass protocol, and decoding settings for the assessment. |
| `calibration_30_combined.csv` | 30-record author calibration: rule-based pre-filter, model, and author decisions, with agreement flags. |
| `validation50_comparison.csv` | 50-record reproducibility check: two independent model passes (agreement 49/50; Cohen's κ = 0.90). |
| `final_corpus_119.csv` | The 119 included works (`record_id`, year, title, venue, DOI, abstract). |
| `corpus119_full_coding.csv` | Per-record coding of the 119 works, keyed by `record_id`: year, publication type, implementation maturity, primary foundation-model integration pattern, and abstract-level presence flags for nine governance mechanisms. |
| `corpus119_profile.csv` | Aggregate corpus profile (publication types, years). |
| `table3_cell_evidence.csv` | Long-format coverage matrix behind Table 3 (architecture × ability channel × present/absent). |

## PRISMA flow

```
Identified (Scopus 941 + Web of Science 232)      = 1,173
Duplicates removed                                −   143
Records screened                                  = 1,030
Excluded at automated pre-filter                  −   370
Records assessed for eligibility (title/abstract) =   660
Excluded at eligibility                           −   541
Full texts retrieved and assessed                 =   119
Excluded after full-text                          −     0
Studies included in synthesis (2023–2026)         =   119
```

## How to reproduce

1. Run the Scopus and Web of Science query strings in `search_protocol_scopus_wos.md` (institutional access to Scopus and Web of Science is required to re-run the searches).
2. Export the results and de-duplicate by DOI, then by normalized title (audit in `prefilter_log_1030.csv`).
3. Apply the eligibility criteria using the rubric in `llm_eligibility_prompt.md`; the decisions are in `screening_log_660.csv`.
4. The included corpus and its coding are in `final_corpus_119.csv` and `corpus119_full_coding.csv`.

## Notes

- **Screening.** A reproducible rule-based pre-filter was followed by an LLM-assisted eligibility assessment; final inclusion decisions were made by the author. Reliability is documented in `calibration_30_combined.csv` and `validation50_comparison.csv`.
- **`comparator_only`.** In `corpus119_full_coding.csv`, six works use a foundation model only as a comparator; this is coded `comparator_only` (not "none").
- **2027-dated records.** Two records carried a database publication year of 2027 (early-access items); both were outside the 2018–2026 window and excluded, so they do not affect the 119-work corpus.
- **Coding scope.** The governance-mechanism flags in `corpus119_full_coding.csv` are *abstract-level* presence indicators, not verified full-text presence/absence judgements.
- All included works are indexed in Scopus or Web of Science; no proprietary research data were created for this review.

## License

Data and documentation in this repository are released under **CC BY 4.0** (see `LICENSE`).

## Citation

If you use these materials, please cite the article (citation details to be added upon acceptance).
