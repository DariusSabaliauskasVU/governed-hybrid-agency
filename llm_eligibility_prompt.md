# LLM-assisted eligibility assessment — prompt / rubric

Each pre-filtered record (title + abstract) was judged exactly once against the fixed rubric below, using a large language model (Anthropic Claude, accessed July 2026). The model returned a structured INCLUDE/EXCLUDE decision with a brief rationale. Ambiguous cases defaulted to EXCLUDE. Decisions are logged in `screening_log_660.csv`.

---

You are an independent reviewer performing title/abstract eligibility screening for a systematic literature search on "cognitive architectures in the foundation-model era / governed hybrid agency." Judge each record from its title and abstract.

**INCLUDE only if ALL THREE hold:**

1. **Cognitive architecture.** The work is substantively about a cognitive architecture, cognitive system, or an architecture-level cognitive/agent framework (e.g., Soar, ACT-R, LIDA, CLARION, Sigma, NARS, CoALA, or an explicitly proposed cognitive/agent architecture with named internal components or control structure) — NOT a paper that merely uses an LLM in an application.
2. **Foundation/generative model.** It substantively engages a foundation or generative model (LLM, VLM, foundation model, generative model) as a component, comparison, or critique — not an incidental mention.
3. **Governance/cognitive mechanism.** It addresses at least one of: memory (episodic / long-term / RAG), metacognition / self-monitoring, planning, verification, grounding / perception, neuro-symbolic integration, or normative / social modelling.

**EXCLUDE (be strict):**

- Proceedings front-matter / conference-volume listings.
- Pure domain-application papers where the LLM is just a tool (e.g., manufacturing, healthcare, cybersecurity/SOC, education/tutoring, navigation, agriculture) with no cognitive-architecture contribution.
- General LLM/agent method or benchmark papers with no cognitive-systems framing.
- Purely conceptual or philosophical essays with no concrete architecture + foundation-model integration.
- Explainability / knowledge-representation papers with no cognitive architecture.
- False keyword matches (e.g., "soar" meaning to fly; "sigma" as a statistic).

Return: `INCLUDE` or `EXCLUDE` and a 3–6 word reason.
