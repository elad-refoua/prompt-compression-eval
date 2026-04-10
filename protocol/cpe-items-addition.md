# CPE Architecture Items Added to Evaluation

**Date:** 2026-04-10
**Version:** 2.0 (added CPE items)
**Status:** Live in production platform

## Background

The original evaluation used 7 ad-hoc dimensions I (Claude, research coordinator) built without grounding in published work. After discussion with Elad:

1. **Replaced** the 7 ad-hoc dimensions with **8 validated dimensions** borrowed from Elad's prior MENTI expert platform (`Gemini-menti/src/expert/main.js`, `DEFAULT_BOT_DIMENSIONS`).
2. **Added** 6 **new items** specifically grounded in the CPE paper (Refoua et al., CLPsych 2026) to directly test whether the CPE architectural claims transfer across compression conditions.

The 6 CPE items turn this study from "AI simulation quality comparison" into **empirical validation of CPE itself**. If the CPE items differentiate the 33K vs. 3K conditions, it proves CPE principles are identifiable and measurable in generated output.

## The 14 Dimensions

Each conversation is rated on 14 dimensions (1-7 Likert, Hebrew):

### Section A: General Quality (8 items -- from Gemini-MENTI)

| # | ID | Hebrew Label | Construct |
|---|----|------|-----------|
| 1 | clinical_realism | ריאליזם קליני | Does the encounter feel like real therapy? |
| 2 | pedagogical_value | ערך פדגוגי | Is there something to learn from it? |
| 3 | character_consistency | עקביות הדמות | Does the persona stay coherent? |
| 4 | difficulty_match | התאמת רמת קושי | Is the difficulty calibrated? |
| 5 | defense_realism | ריאליזם ההגנות | Do defenses rise/fall realistically? |
| 6 | emotional_attunement | התאמה רגשית | Are emotional responses fitting? |
| 7 | language_quality | איכות השפה | Is the Hebrew natural and appropriate? |
| 8 | natural_flow | זרימה טבעית | Does the conversation flow naturally? |

### Section B: CPE Architecture (6 new items -- grounded in the paper)

| # | ID | Hebrew Label | CPE Paper Claim Tested |
|---|----|------|------------------------|
| 9 | cpe_layered_depth | עומק פסיכולוגי מרובד | "Layered psychology: outer/middle/inner levels" (§ Design Observation C) |
| 10 | cpe_nonlinearity | לא-ליניאריות | "Non-linear emotional trajectories" (§ Design Observation D) |
| 11 | cpe_reactive_role | תפקיד ראקטיבי | "Assign the model to reactive roles" (§ Design Observation B) |
| 12 | cpe_sustained_difficulty | קושי מתמשך | "Sustained difficulty and resistance, not rapid resolution" (§ Key Claims) |
| 13 | cpe_contingent_responsiveness | רגישות לאיכות המטפל/ת | "Contingency rules for transitions" (§ Design Observation D) |
| 14 | cpe_functional_defenses | הגנות בעלות תפקוד קליני | "Defenses with developmental/clinical logic" (§ Design Observation A) |

## Why These Six (and not others)

The CPE paper identifies **five design observations** (A-E) and several key claims. The items map as follows:

- **Observation A (explicit clinical knowledge)** → item 14 (functional defenses)
- **Observation B (reactive role)** → item 11 (reactive role)
- **Observation C (layered psychology)** → item 9 (layered depth)
- **Observation D (non-linear trajectories + contingencies)** → items 10 (nonlinearity) + 13 (contingent responsiveness)
- **Observation E (expert knowledge)** → not rated (it's a process claim, not an observable output feature)
- **Sustained difficulty** (the paper's central pedagogical claim) → item 12

Each item asks raters to directly assess whether the generated conversation exhibits the CPE architectural feature. Positive ratings across conditions = the feature transfers. Systematic 33K > 3K differences = compression erodes that feature. 33K ≈ 3K = the feature survives compression (supports the prompt distillation hypothesis).

## Rater Burden

- 14 items x 2 conversations = 28 ratings per pair
- 10 pairs = 280 ratings per rater
- Each rating: ~10 seconds (slider + reading the prompt)
- Total time for ratings: ~47 minutes
- Plus reading conversations, forced-choice, comments: 2-4 hours per rater

This is within the acceptable burden for expert competence rating in published studies (Kobak et al. 2005).

## How This Strengthens the Paper

### Without the CPE items
"We compared two prompt conditions on general simulation quality."

### With the CPE items
"We empirically tested whether the architectural claims of Clinical Prompt Engineering (Refoua et al., 2026) transfer across prompt compression conditions. We operationalized the five CPE design observations into six rating items and found [X]."

This is a direct empirical validation of your own prior theoretical work. It makes the paper a **methodological sequel** to CLPsych 2026, not just a standalone comparison.

## Open Question: The "Difficulty Match" Overlap

Item 4 (difficulty_match) and item 12 (sustained difficulty) partially overlap. They measure different things but may confuse raters:
- **difficulty_match**: Is the difficulty CALIBRATED (not too easy, not unrealistically hard)?
- **sustained_difficulty**: Is the difficulty MAINTAINED throughout (no premature resolution)?

Both are relevant. If rater confusion appears in the data, sensitivity analyses can collapse them.

## Files Updated

- `scripts/build_config.py` -- 14 dimensions with `section: "general"` or `section: "cpe"` tags
- `platform/index.html` -- section dividers between general and CPE, updated counts (8 → 14)
- `platform/config.json` -- regenerated with new dimensions
- `protocol/evaluation-criteria.md` -- needs update (pending)

## Sources

- Refoua, E. (2026). Clinical Prompt Engineering: Encoding Clinical Knowledge into AI Training Simulations. Proceedings of CLPsych 2026.
  - PDF: `C:/Users/user/Desktop/projects/help in war time/מאגר מאמרים/overleaf/CLPsych_FINAL.pdf`
- Gemini-MENTI DEFAULT_BOT_DIMENSIONS: `C:/Users/user/Desktop/projects/Gemini-menti/src/expert/main.js` lines 41-50
