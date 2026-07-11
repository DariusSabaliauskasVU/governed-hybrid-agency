# Systematic search protocol — Scopus & Web of Science

**Review title (working):** Cognitive architectures after foundation models: from unified cognition to governed hybrid agency
**Databases:** Scopus (Elsevier) and Web of Science Core Collection (Clarivate) — **only these two**
**Coverage window:** 2018–2026 (foundation-model era; BERT/GPT-2 onward)
**Languages:** English
**Document types:** journal article, review, conference/proceedings paper
**Reporting standard:** PRISMA 2020

---

## 1. Research questions

- **RQ1.** How have cognitive architectures been conceptualised and redesigned in relation to foundation models (LLMs/VLMs) since 2018?
- **RQ2.** Which architectural mechanisms — persistent memory, metacognitive control, planning, verification, perceptual grounding, normative/social modelling — are proposed to *govern* foundation-model agents?
- **RQ3.** What evidence exists for integrating symbolic / architectural control with generative models (neuro-symbolic integration, retrieval-augmented control loops, hybrid agency)?

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

## 5. Screening procedure (two-stage, dual-reviewer)

1. **De-duplication** across Scopus + WoS (by DOI, then normalised title).
2. **Stage 1 — title/abstract** against inclusion criteria. Two reviewers; Cohen's κ reported on a 20% calibration sample; conflicts resolved by discussion.
3. **Stage 2 — full text** of passing records.
4. **Data extraction:** architecture named; foundation-model role; governance mechanisms covered; evidence type; venue; year.
5. **PRISMA 2020 flow** with exact counts at each stage; reasons for full-text exclusions logged.

## 6. PRISMA flow (to be filled with real numbers)

```
Identified:      Scopus n = ___   +   WoS n = ___          = ___
Duplicates removed:                                          − ___
Screened (title/abstract):                                   = ___
Excluded at screening:                                       − ___
Full-text assessed:                                          = ___
Excluded (with reasons):                                     − ___
Included in synthesis:                                       = ___
```

## 7. Deliverables produced from the export

- De-duplicated corpus (`corpus.csv`) with screening decisions.
- PRISMA flow diagram + counts.
- Rewritten **Methods** section replacing "Elicit-centered retrieval" with the Scopus+WoS PRISMA protocol.
- Updated reference base (only Scopus/WoS-indexed items).
