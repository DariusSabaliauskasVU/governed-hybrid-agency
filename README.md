# Governed Hybrid Agency — Reproducibility Package

Supplementary data and reproducibility materials for the review:

> **Governed Hybrid Agency: Cognitive Architectures as Control Systems for Foundation-Model Agents.**
> D. Sabaliauskas & A. Dirzyte. Submitted to the *Journal of Artificial Intelligence Research* (JAIR), Surveys track.

This repository lets anyone reproduce the systematic search, screening, and coding behind the 119-work evidence map.

## Contents

| File | Description |
|---|---|
| `search_protocol_scopus_wos.md` | Full PRISMA-based search protocol: research questions, concept blocks, exact Scopus and Web of Science Boolean query strings, filters, eligibility criteria, and screening procedure. |
| `screening_log_660.csv` | Record-level eligibility decisions for all 660 pre-filtered records (id, decision, reason, year, title, venue). |
| `llm_eligibility_prompt.md` | The exact fixed rubric/prompt given to the LLM-assisted eligibility assessment. |
| `calibration_30_combined.csv` | 30-record author calibration: rule-based pre-filter decision, model decision, and author decision, with agreement flags. |
| `validation50_comparison.csv` | 50-record reproducibility check: two independent model passes on a random sample (agreement 49/50; Cohen's κ = 0.90). |
| `final_corpus_119.csv` | The 119 works included in the synthesis (year, title, venue, DOI, abstract). |
| `corpus119_coded.csv` | Per-record coding of the 119 works: implementation maturity and primary foundation-model integration pattern. |
| `corpus119_profile.csv` | Aggregate corpus profile (publication types, years). |

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
2. Export the results and de-duplicate by DOI, then by normalized title.
3. Apply the eligibility criteria (Section 3.3 of the article) using the rubric in `llm_eligibility_prompt.md`; the resulting decisions are in `screening_log_660.csv`.
4. The included corpus and its coding are in `final_corpus_119.csv` and `corpus119_coded.csv`.

## Notes

- Screening was executed by a reproducible rule-based pre-filter followed by an LLM-assisted eligibility assessment; a 30-record author calibration and a 50-record two-pass reproducibility check are provided (`calibration_30_combined.csv`, `validation50_comparison.csv`).
- All included works are indexed in Scopus or Web of Science; no proprietary research data were created for this review.

## License

Data and documentation in this repository are released under **CC BY 4.0** (see `LICENSE`).

## Citation

If you use these materials, please cite the article (citation details to be added upon acceptance).
