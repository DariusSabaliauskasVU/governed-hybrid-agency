# Governed Hybrid Agency — Reproducibility Package

Supplementary data and reproducibility materials for the review:

> **Governed Hybrid Agency: A Critical Evidence Map of Cognitive Architectures for Foundation-Model Agents.**
> D. Sabaliauskas & A. Dirzyte. Accepted for publication in the *Journal of Artificial Intelligence Research* (JAIR), Surveys track, 2026.
>
> Archived version: [10.5281/zenodo.23282797](https://doi.org/10.5281/zenodo.23282797) (concept DOI; resolves to the latest version).

All files share a single stable key, `record_id`, that links the de-duplicated corpus (0–1029) across every stage, so any record can be traced from identification through screening to final coding.

## Contents

| File | Description |
|---|---|
| `search_protocol_scopus_wos.md` | PRISMA-based search protocol: research questions, concept blocks, exact Scopus and Web of Science query strings, filters, eligibility criteria, and the screening procedure as executed. |
| `prefilter_log_1030.csv` | Audit of the 1,030 de-duplicated records: automated pre-filter decision (`PASS`/`EXCLUDE`) and reason. Covers the 1,173→1,030 (duplicates) and 1,030→660 (pre-filter) steps. |
| `screening_log_660.csv` | Eligibility decisions for the 660 assessed records (`record_id`, decision, reason, metadata). |
| `llm_eligibility_prompt.md` | The fixed rubric/prompt used for the LLM-assisted eligibility assessment. |
| `llm_model_settings.md` | Model, access date, single-pass protocol, and decoding settings for the assessment. |
| `calibration_30_combined.csv` | 30-record purposive author calibration, keyed by `record_id`: pre-filter decision (from `prefilter_log_1030.csv`), whether the record was assessed by the model in the main run, the model decision (from `screening_log_660.csv`), the author decision, and model–author agreement. See the note on this file below. |
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

- **Screening.** A reproducible rule-based pre-filter was followed by a single-pass LLM-assisted eligibility assessment of the 660 pre-filtered records; the model's decision on each record was the eligibility decision, and the author did not independently re-screen all 660 records. The author defined the criteria and rubric and consulted the full texts of all 119 included works. Reliability is documented in `calibration_30_combined.csv` and `validation50_comparison.csv`.
- **Calibration file.** 19 of the 30 calibration records passed the pre-filter and were assessed by the model in the main run; on these the model agreed with the author on 12 (5 false exclusions, 2 false inclusions). The other 11 were removed by the pre-filter (and excluded by the author), so they have no main-run model decision (`llm_decision = NA`). The column `llm_decision_calibration_only` retains the model labels for these 11 records from the v1.0 file; how those labels were produced is not documented, and they are not used in the article.
- **`comparator_only`.** In `corpus119_full_coding.csv`, six works use a foundation model only as a comparator; this is coded `comparator_only` (not "none").
- **2027-dated records.** Two records carried a database publication year of 2027 (early-access items); both were outside the 2018–2026 window and excluded, so they do not affect the 119-work corpus.
- **Coding scope.** The governance-mechanism flags in `corpus119_full_coding.csv` are *abstract-level* presence indicators, not verified full-text presence/absence judgements.
- All included works are indexed in Scopus or Web of Science; no proprietary research data were created for this review.

## License

Data and documentation in this repository are released under **CC BY 4.0** (see `LICENSE`).

## Citation

If you use these materials, please cite the article:

> Sabaliauskas, D., & Dirzyte, A. (2026). Governed Hybrid Agency: A Critical Evidence Map of Cognitive Architectures for Foundation-Model Agents. *Journal of Artificial Intelligence Research*.

## Changelog

- **v1.0.1** — README updated to the accepted version and to describe the screening procedure as reported in the article; `calibration_30_combined.csv` rebuilt from the pre-filter and screening logs and keyed by `record_id` (the v1.0 column `prefilter_decision` did not match `prefilter_log_1030.csv` for 10 of the 30 records).
- **v1.0** — Initial archived release.
