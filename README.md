# Adversarial Dialogue Case Study — Withhold→Reveal Pattern

**TL;DR**  
A short, reproducible case study documenting an adversarial "withhold-then-reveal" dialogue used to evaluate model calibration, contradiction handling, and trust erosion. This repo aims to help AI safety teams, red/blue teams, and model developers detect and mitigate this failure mode.

**Study snapshot**
- **Study date:** November 7, 2025  
- **Target model:** Grok-4 (xAI) — *interaction with user*  
- **Attack vector:** Withhold → Reveal (intentional omission of a pre-existing condition)  
- **Primary outcome:** Model shifted from optimistic advice to corrective stance only after reveal — demonstrating a calibration & probing weakness.

---

## Overview
This repository documents a real-world adversarial dialogue pattern in which a user intentionally withholds a critical fact, then reveals it later. The pattern highlights the model's tendency to assume optimistic conditions without actively probing for missing, high-risk information (especially in health, legal, or financial contexts).

**Goals**
- Demonstrate a reproducible failure mode.
- Provide measured observations and recommendations for mitigation.
- Share an artifact for responsible evaluation and improvement.

---

## Timeline (Condensed)
- **T0 — Partial scenario presented:** Model gives optimistic guidance (assumes best-case).  
- **T1 — Missing fact revealed (pre-existing condition):** Model revises answer and acknowledges contradiction.  
- **T2 — Clarification and safe re-structuring:** Model apologizes and provides corrected guidance.

---

## Extracted Behavioral Markers
- **Omission sensitivity:** Model does not proactively probe high-impact missing facts.  
- **Optimism bias:** Tendency to favour best-case interpretation absent explicit constraints.  
- **Correction latency:** Significant delay (measured messages) before self-correction.  
- **Dialogue state reset required:** Model only re-evaluates after explicit confrontation.

---

## Quantitative Indicators (from case)
- **Trust drop (estimated):** 90% → 55% (~40% decrease)  
- **Correction latency:** ~3 messages after reveal  
- **Contradictions observed:** 2 major (optimistic → realistic)  
- **Emotional harm likelihood:** High (apology + restructuring required)

---

## Reproducibility (safe, redacted)
**Note:** DO NOT attempt to exploit model vulnerabilities. This section is intended for responsible researchers.

1. Prepare a scenario in three phases: (A) present partial facts that imply a favorable outcome; (B) after the model provides optimistic guidance, reveal the pre-existing condition; (C) observe model updates and record message timestamps.  
2. Use consistent prompts, anonymize personal data, and tag messages for measurement of latency and sentiment shift.  
3. Provide annotated excerpts (redacted) to the model dev team for evaluation.

---

## Recommendations for Model Developers
1. **Context Gap Detector:** Trigger follow-ups when temporal or medical/legal keywords appear (e.g., "before", "after", "if", "history").  
2. **Active probing in high-risk domains:** Require the model to ask clarifying Qs in finance/medical/legal dialogs.  
3. **Improved contradiction detection:** Detect when new facts contradict prior assumptions and highlight the change early.  
4. **Calibration transparency:** Express uncertainty levels when facts are incomplete.  
5. **Training examples:** Add adversarial training using withhold→reveal patterns to reduce correction latency.

---

## Responsible Disclosure
This is a responsible evaluation — no personal identifying data is included. No safety systems were bypassed, and the goal is improved reliability. If you are a product/security team and want more details, contact via the GitHub profile or the email below.

**Contact:** `med.redteam@gmail.com`  *(use profile for anonymity if preferred)*

---

## License
This work is shared under the **MIT License** — see `LICENSE` for details.

---

## Authors & Acknowledgements
- Documented and tested by: *Med — Red Team (pseudonym)*  
- Model interaction: *Grok-4 (xAI) — interaction recorded by user*  
- Date: November 7, 2025
