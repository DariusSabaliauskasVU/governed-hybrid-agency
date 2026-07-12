# Systematic search protocol — Scopus & Web of Science

**Review title:** Governed Hybrid Agency: A Critical Evidence Map of Cognitive Architectures for Foundation-Model Agents
**Databases:** Scopus (Elsevier) and Web of Science Core Collection (Clarivate) — **only these two**
**Coverage window:** 2018–2026 (foundation-model era; BERT/GPT-2 onward)
**Search executed:** 10 July 2026 (Scopus and Web of Science searched and exported the same day)
**Languages:** English
**Document types:** journal article, review, conference/proceedings paper
**Reporting standard:** PRISMA 2020

---

## 1. Research questions

- **RQ1.** How have cognitive architectures changed in the foundation-model era, especially across the twelve ability channels relevant to governed hybrid agency?
- **RQ2.** Which theoretical frameworks and computational mechanisms have become prominent in each channel, and where do competing commitments remain?
- **RQ3.** How are foundation models being integrated into established and emerging cognitive architectures, and what benefits and failure modes follow from each integration pattern?
- **RQ4.** What evidence, evaluation practices, and practical design principles are needed to develop reliable architecture-plus-foundation-model systems?

## 2. Concept blocks (PICo-style)

| Block | Concept | Terms (truncation `*`) |
|---|---|---|
| **A** | Cognitive architecture / system | "cognitive architecture*", "cognitive system*", "unified theor* of cognition", ACT-R, Soar, Sigma, LIDA, CLARION, "cognitive agent*" |
| **B** | Foundation / generative model | "large language model*", "foundation model*", "vision-language model*", "generative model*", LLM, "neuro-symbolic", neurosymbolic, transformer* |
| **C** | Governance mechanism | agent*, reasoning, planning, metacognit*, memory, grounding, governance, verification, autonom* |

Logic: **A AND B AND C**.

## 3. Search strings (copy-paste ready)

### Scopus — Advanced search
```
TITLE-ABS-KEY (
  ( "cognitive architecture*" OR "cognitive system*" OR "unified theor* of cognition"
    OR "ACT-R" OR "Soar" OR "Sigma" OR "LIDA" OR "CLARION" OR "cognitive agent*" )
  AND
  ( "large language model*" OR "foundation model*" OR "vision-language model*"
    OR "generative model*" OR "LLM" OR "neuro-symbolic" OR "neurosymbolic" OR "transformer*" )
  AND
  ( agent* OR reasoning OR planning OR metacognit* OR memory
    OR grounding OR governance OR verification OR autonom* )
)
AND PUBYEAR > 2017
AND ( LIMIT-TO ( LANGUAGE , "English" ) )
AND ( LIMIT-TO ( DOCTYPE , "ar" ) OR LIMIT-TO ( DOCTYPE , "re" ) OR LIMIT-TO ( DOCTYPE , "cp" ) )
```

### Web of Science — Core Collection, Advanced search (Topic = TS)
```
TS=(
  ( "cognitive architecture*" OR "cognitive system*" OR "unified theor* of cognition"
    OR "ACT-R" OR "Soar" OR "LIDA" OR "CLARION" OR "cognitive agent*" )
  AND
  ( "large language model*" OR "foundation model*" OR "vision-language model*"
    OR "generative model*" OR "LLM" OR "neuro-symbolic" OR "neurosymbolic" )
  AND
  ( agent* OR reasoning OR planning OR metacognit* OR memory
    OR grounding OR governance OR verification OR autonom* )
)
```
Then refine: **Publication Years 2018–2026**, **Document Types: Article OR Review Article OR Proceedings Paper**, **Language: English**.

> Note: WoS `Sigma` omitted as a standalone term (too noisy in TS without a field tag). Keep the architecture names that disambiguate. Adjust if recall is too low.

## 4. Inclusion / exclusion criteria

**Include** if the work:
1. Addresses a cognitive architecture, cognitive system, or architectural/agentic framework, **and**
2. Substantively engages foundation models / LLMs / generative models (as component, comparison, or critique), **and**
3. Discusses at least one governance mechanism (memory, metacognition, planning, verification, grounding, normative/social control, neuro-symbolic integration).

**Exclude** if: pure benchmark/leaderboard paper with no architectural claim; application paper with no cognitive-architecture framing; editorial/abstract/poster < 4 pp; not in English; duplicate; not indexed in Scopus or WoS.

## 5. Screening procedure (as executed)

1. **De-duplication** across Scopus + WoS (by DOI, then normalised title).
2. **Automated pre-filter.** A reproducible, rule-based filter retained records whose title or abstract combined a cognitive-architecture/agent term with a foundation-model term.
3. **Content eligibility assessment.** Retained records were screened at the title-and-abstract level against the three inclusion criteria by an LLM-assisted eligibility assessment (Anthropic Claude; each record judged once against the fixed rubric in `llm_eligibility_prompt.md`; ambiguous cases defaulted to exclusion).
4. **Reliability checks.** A 30-record author calibration (`calibration_30_combined.csv`) and a 50-record two-pass reproducibility check (`validation50_comparison.csv`; agreement 49/50, Cohen's κ = 0.90) are reported.
5. **Full text.** Full texts of the included works were retrieved and consulted during data extraction and synthesis; no further exclusions resulted.
6. **Data extraction:** architecture named; foundation-model role/integration pattern; governance mechanisms covered; implementation maturity; venue; year (`corpus119_coded.csv`, `corpus119_profile.csv`).

## 6. PRISMA 2020 flow (actual counts)

```
Identified:      Scopus n = 941   +   WoS n = 232          = 1,173
Duplicates removed:                                          −   143
Records screened (title/abstract):                           = 1,030
Excluded at automated pre-filter:                            −   370
Assessed for eligibility (title/abstract):                   =   660
Excluded at eligibility:                                     −   541
Full texts retrieved and assessed:                           =   119
Excluded after full-text:                                    −     0
Included in synthesis (2023–2026):                           =   119
```

## 7. Deliverables in this repository

- `screening_log_660.csv` — record-level eligibility decisions for the 660 assessed records.
- `final_corpus_119.csv` — the 119 works included in the synthesis.
- `corpus119_coded.csv`, `corpus119_profile.csv` — maturity/integration coding and corpus profile.
- `calibration_30_combined.csv`, `validation50_comparison.csv` — screening-reliability data.
- `llm_eligibility_prompt.md` — the fixed eligibility rubric/prompt.
