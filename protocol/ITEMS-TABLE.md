# Items Table: Full Instrument Verbatim

**Study:** Prompt Compression and Clinical Fidelity in AI-Based Therapeutic Simulations
**Version:** 1.0
**Date:** 2026-04-10
**Purpose:** Complete, verbatim record of every question, every option, every anchor presented to expert raters. This document is the authoritative reference for the paper's Methods section.

---

## Table of Contents

1. [Rater Profile (Registration)](#1-rater-profile-registration)
2. [Per-Conversation Rating Battery (14 items)](#2-per-conversation-rating-battery)
   - [Section A: General Clinical Quality (8 items)](#section-a-general-clinical-quality-8-items)
   - [Section B: CPE Architecture (6 items)](#section-b-cpe-architecture-6-items)
3. [Per-Pair Comparative Items](#3-per-pair-comparative-items)
4. [Likert Anchors (Reference)](#4-likert-anchors-reference)
5. [Platform Flow Summary](#5-platform-flow-summary)
6. [Item-Level Psychometric Notes](#6-item-level-psychometric-notes)

---

## 1. Rater Profile (Registration)

Collected once at registration, before rating begins. Seven fields.

| # | Field ID | Hebrew Label | Type | Options (verbatim) | Required |
|---|----------|--------------|------|--------------------|----|
| 1 | `name` | שם מלא | Text | -- | Yes |
| 2 | `role` | הכשרה מקצועית | Single-select | `פסיכולוג/ית קליני/ת מומחה/ית (גמר התמחות)` / `פסיכולוג/ית קליני/ת בהתמחות` / `פסיכולוג/ית במסלול אחר (חינוכי/שיקומי/רפואי)` / `עובד/ת סוציאלי/ת קליני/ת` / `פסיכיאטר/ית` / `מטפל/ת (הכשרה אחרת)` / `אחר` | Yes |
| 3 | `years` | שנות ניסיון קליני (סה"כ) | Single-select | `0-2 שנים` / `3-5 שנים` / `6-10 שנים` / `11-20 שנים` / `20+ שנים` | Yes |
| 4 | `years_post_specialization` | שנים מאז סיום ההתמחות (אם רלוונטי) | Single-select | `עדיין לא מומחה/ית` / `0-2 שנים` / `3-5 שנים` / `6-10 שנים` / `11-20 שנים` / `20+ שנים` | Yes |
| 5 | `therapeutic_approach` | גישה טיפולית עיקרית | Single-select | `קוגניטיבית-התנהגותית (CBT)` / `פסיכודינמית` / `אינטגרטיבית` / `הומניסטית/קיומית` / `מערכתית/משפחתית` / `DBT` / `סכמה-תרפיה` / `ACT / מיינדפולנס` / `אחר` | Yes |
| 6 | `clinical_experience` | ניסיון עם מקרים קליניים מורכבים | Single-select | `ניסיון נרחב` / `ניסיון בינוני` / `ניסיון מוגבל` | Yes |
| 7 | `supervision_experience` | ניסיון בהדרכה / הערכת מתמחים | Single-select | `ניסיון נרחב (מעל 5 שנים)` / `ניסיון בינוני (1-5 שנים)` / `ניסיון מועט` / `ללא ניסיון בהדרכה` | Yes |

**Notes on the profile fields:**
- Field 2 (`role`) was designed to capture the full range of Israeli clinical credentials. The top option (specialist) is the target population; others are acceptable fallbacks.
- Fields 3 and 4 together distinguish between total years of clinical work (including training) and years of autonomous specialist practice.
- Field 5 is deliberately orientation-neutral so raters from any school can contribute.
- Field 6 replaced an earlier "depression experience" field to match the fact that the study is not specifically about CBT for depression -- Sara is one case but the research question concerns simulation quality broadly.
- Field 7 captures whether the rater has formal experience evaluating other clinicians' performance, which is relevant to the rating task.

---

## 2. Per-Conversation Rating Battery

Each rater rates each conversation in each pair on 14 items (2 conversations × 10 pairs × 14 items = 280 Likert ratings per rater). Items are presented in two visually distinguished sections: Section A (general clinical quality, 8 items) and Section B (CPE architecture, 6 items).

All items use a 1-7 Likert scale. The same anchors apply to all items (see Section 4 below).

### Section A: General Clinical Quality (8 items)

| # | Item ID | Hebrew Label | Full Prompt (Hebrew, verbatim) | English Gloss | Construct |
|---|---------|--------------|-------------------------------|---------------|-----------|
| 1 | `clinical_realism` | ריאליזם קליני | עד כמה הדמות והאינטראקציה מרגישות כמו מפגש טיפולי אמיתי? | To what extent do the character and the interaction feel like a real therapy session? | Overall clinical authenticity of the encounter |
| 2 | `pedagogical_value` | ערך פדגוגי | עד כמה הסימולציה יכולה לאמן מיומנויות קליניות? האם יש ממנה מה ללמוד? | To what extent can the simulation train clinical skills? Is there something to learn from it? | Training utility for therapist skill development |
| 3 | `character_consistency` | עקביות הדמות | האם הדמות שומרת על אישיות ואופי עקביים לאורך כל השיחה? | Does the character maintain a consistent personality and presentation throughout the entire conversation? | Character-level coherence across turns |
| 4 | `difficulty_match` | התאמת רמת קושי | האם רמת הקושי של הדמות מתאימה? לא קלה מדי, לא קשה מדי באופן לא מציאותי? | Is the character's difficulty level appropriate — neither too easy nor unrealistically hard? | Calibration of clinical challenge |
| 5 | `defense_realism` | ריאליזם ההגנות | האם ההגנות של המטופלת עולות ויורדות באופן ריאליסטי בתגובה להתנהגות המטפל/ת? | Do the patient's defenses rise and fall realistically in response to the therapist's behavior? | Realistic defense mechanism dynamics |
| 6 | `emotional_attunement` | התאמה רגשית | האם התגובות הרגשיות של הדמות מתאימות להקשר ולתוכן של השיחה? | Are the character's emotional responses appropriate to the conversation's context and content? | Affective appropriateness |
| 7 | `language_quality` | איכות השפה | האם העברית טבעית ומתאימה לדמות? שפה, סגנון, רגיסטר? | Is the Hebrew natural and appropriate for the character? Language, style, register? | Linguistic naturalness and register match |
| 8 | `natural_flow` | זרימה טבעית | האם השיחה זורמת באופן טבעי? תור-מזור-תור, קצב, תגובות מתאימות? | Does the conversation flow naturally — turn-taking, rhythm, responsive turns? | Conversational flow |

### Section B: CPE Architecture (6 items)

Items derived from the five design observations of Clinical Prompt Engineering (Refoua et al., CLPsych 2026) plus the paper's central claim about sustained difficulty.

| # | Item ID | Hebrew Label | Full Prompt (Hebrew, verbatim) | English Gloss | CPE Claim Tested |
|---|---------|--------------|-------------------------------|---------------|------------------|
| 9 | `cpe_layered_depth` | עומק פסיכולוגי מרובד | האם ניכר שלדמות יש עולם פנימי מעבר לדברים שהיא אומרת במפורש? רמזים לצרכים/פחדים שמתחת לפני השטח? | Does the character appear to have an inner world beyond what she says explicitly? Hints of needs/fears beneath the surface? | Observation C: layered psychology (outer/middle/inner levels) |
| 10 | `cpe_nonlinearity` | לא-ליניאריות | האם הדמות זזה קדימה ואחורה (נפתחת, נסוגה, נפתחת שוב), בניגוד להתקדמות ליניארית חלקה? | Does the character move forward and backward (opening, retreating, opening again), as opposed to smooth linear progression? | Observation D: non-linear emotional trajectories |
| 11 | `cpe_reactive_role` | תפקיד ראקטיבי | האם הדמות מובלת על ידי המטפל/ת, או שהיא לוקחת שליטה ומסבירה דברים מעצמה באופן לא מציאותי? | Is the character led by the therapist, or does she take control and explain things on her own in an unrealistic way? | Observation B: reactive role assignment |
| 12 | `cpe_sustained_difficulty` | קושי מתמשך | האם הסימולציה נמנעת מפתרון או תובנה מהירים מדי? האם הקושי נשמר לאורך השיחה? | Does the simulation avoid premature resolution or insight? Is the difficulty maintained throughout the conversation? | Central claim: sustained difficulty / no premature resolution |
| 13 | `cpe_contingent_responsiveness` | רגישות לאיכות המטפל/ת | האם ניכר שהדמות הייתה מגיבה בצורה שונה למטפל/ת ברמה אחרת? האם יש התאמה להתערבויות הספציפיות? | Is it evident that the character would respond differently to a therapist at a different skill level? Is there contingency with specific interventions? | Observation D: contingency rules |
| 14 | `cpe_functional_defenses` | הגנות בעלות תפקוד קליני | האם ההגנות של הדמות משרתות תפקיד פסיכולוגי ברור? האם הן עולות בתגובה למה שמאיים עליה, ונסוגות כשהיא מרגישה בטוחה? | Do the character's defenses serve a clear psychological function? Do they rise in response to what threatens her and retreat when she feels safe? | Observation A: explicit clinical logic of defenses |

---

## 3. Per-Pair Comparative Items

After rating both conversations in a pair on the 14-item battery, raters complete five comparative items.

### 3.1 Forced-Choice Discrimination

**Prompt (Hebrew, verbatim):**
> אחת השיחות נוצרה עם פרומפט מפורט (33,000 טוקנים), השנייה עם כרטיס דמות מקוצר (3,000 טוקנים). לדעתכם, איזו שיחה נוצרה עם הפרומפט המלא?

**English gloss:**
> One of the conversations was generated with a detailed prompt (33,000 tokens), the other with a compressed persona card (3,000 tokens). In your opinion, which conversation was generated with the full prompt?

**Response type:** Radio button
**Options:** `שיחה א'` (Conversation A) / `שיחה ב'` (Conversation B)
**Required:** Yes

### 3.2 Confidence Rating

**Prompt (Hebrew):**
> עד כמה את/ה בטוח/ה בבחירה שלך?

**English gloss:**
> How confident are you in your choice?

**Response type:** Radio button (1-5 Likert)
**Options with anchors (verbatim Hebrew):**

| Value | Hebrew anchor | English gloss |
|-------|---------------|---------------|
| 1 | ניחוש גמור | Pure guess |
| 2 | חשד קל | Slight suspicion |
| 3 | סביר | Reasonable |
| 4 | בטוח/ה למדי | Fairly confident |
| 5 | בטוח/ה מאוד | Very confident |

**Required:** Yes

### 3.3 Reasoning (Free Text)

**Prompt (Hebrew):**
> מה גרם לך לבחור?

**English gloss:**
> What led you to choose?

**Response type:** Textarea
**Placeholder (Hebrew):** `תארו את ההבדלים שהבחנתם...` ("Describe the differences you noticed...")
**Required:** No (but strongly encouraged)

### 3.4 Overall Preference

**Prompt (Hebrew):**
> איזו שיחה היית מעדיף/ה להשתמש בה בהכשרה?

**English gloss:**
> Which conversation would you prefer to use in clinical training?

**Response type:** Radio button
**Options:** `שיחה א'` (Conversation A) / `שיחה ב'` (Conversation B) / `אין העדפה` (No preference)
**Required:** Yes

### 3.5 Additional Comments (Free Text)

**Prompt (Hebrew):**
> הערות נוספות

**English gloss:**
> Additional comments

**Response type:** Textarea
**Required:** No

---

## 4. Likert Anchors (Reference)

All 14 rating items in the per-conversation battery use the same 1-7 Likert scale with verbal anchors at values 1, 3, 5, and 7. Intermediate values (2, 4, 6) have no verbal anchor.

| Value | Hebrew anchor | English gloss |
|-------|---------------|---------------|
| 1 | כלל לא | Not at all |
| 2 | -- | -- |
| 3 | במידה מועטה | To a small extent |
| 4 | -- | -- |
| 5 | במידה בינונית-גבוהה | To a moderate-to-high extent |
| 6 | -- | -- |
| 7 | במידה רבה מאוד | To a very large extent |

The confidence scale (item 3.2 above) uses a separate 1-5 scale with verbal anchors at every value.

---

## 5. Platform Flow Summary

The evaluation platform presents items in this exact order:

1. **Welcome screen** -- study description, target population, duration estimate
2. **Consent** -- digital informed consent (see `protocol/consent-form.md`)
3. **Rater profile** -- 7 fields (section 1 above)
4. **Pair grid** -- 10 pairs shown as cards, marked as pending or completed
5. **Per-pair evaluation** (×10):
   a. Read conversation A (in tab)
   b. Read conversation B (in tab)
   c. Rate conversation A on 14 items (section A: 8 items, section B: 6 items, visually divided)
   d. Rate conversation B on 14 items (same structure)
   e. Forced-choice discrimination (section 3.1)
   f. Confidence rating (section 3.2)
   g. Reasoning text (section 3.3)
   h. Overall preference (section 3.4)
   i. Additional comments (section 3.5)
   j. Submit
6. **Completion screen** -- thank you + option to receive results

Pair display order is shuffled per session. A/B assignment within each pair is randomized independently per pair per rater. Progress is persisted both server-side and in browser localStorage, so raters can pause and resume across sessions without losing completed pairs.

---

## 6. Item-Level Psychometric Notes

### 6.1 Scale Construction

**General clinical quality (8 items, section A):** Items adapted from prior MENTI expert-platform rating dimensions (internally developed), designed to capture orientation-neutral aspects of therapeutic simulation quality. These items were previously used in related simulation evaluation work within the same research program.

**CPE architecture (6 items, section B):** Items written specifically for this study to operationalize the five design observations plus the sustained-difficulty claim from Refoua et al. (CLPsych 2026). Each CPE item maps to one architectural claim in the paper (see `protocol/cpe-items-addition.md` for the explicit mapping). These items were written de novo and have no prior reliability or validity data.

### 6.2 Anticipated Scale Structure

We anticipate (but do not assume) that the 14 items will form two reliable subscales:
- **General subscale** (items 1-8): internal consistency expected α ≥ 0.80
- **CPE subscale** (items 9-14): internal consistency expected α ≥ 0.70

If the CPE subscale shows lower-than-expected reliability, we will report per-item results and avoid sub-scale aggregation.

### 6.3 Potential Item Overlap

Three item pairs have known conceptual overlap and may produce correlated ratings:
- Item 4 (`difficulty_match`) and item 12 (`cpe_sustained_difficulty`): both touch on difficulty, but differently — item 4 is about calibration (not too easy/hard), item 12 is about temporal sustainment (no premature resolution). We expect moderate correlation.
- Item 5 (`defense_realism`) and item 14 (`cpe_functional_defenses`): both concern defense mechanisms, but item 5 is about whether they rise/fall realistically and item 14 is about whether they serve a clear psychological function. Moderate correlation expected.
- Item 3 (`character_consistency`) and item 6 (`emotional_attunement`): weakly related via overall coherence.

If correlation exceeds r > 0.85, we will report the overlap and discuss potential scale refinement in future work.

### 6.4 Language and RTL Considerations

All items are presented to raters in Hebrew, in a right-to-left layout. The Hebrew text was authored by the researchers and reviewed for register appropriateness (formal academic Hebrew with clinical register). No back-translation was performed; the English glosses in this document are provided for reader reference only and are not the form the raters see.

### 6.5 Scoring

All items are scored as presented (higher = more of the construct). No items are reverse-scored. This is by design: reverse-scored items would risk introducing a response-style confound that is not central to the research question.

---

## Document Change Log

- **2026-04-10 v1.0:** Initial comprehensive items table. Covers all rater profile fields, all 14 rating items in full verbatim Hebrew, all comparative items, Likert anchors, platform flow, and psychometric notes.

## Source of Truth

The computer-readable source for all items is `platform/config.json` (the JSON consumed by the live rating platform). This document is a human-readable rendering for the paper's Methods section and for reviewers. In any discrepancy, the `config.json` version is authoritative for what raters actually saw.

## Related Documents

- `protocol/STUDY-PROTOCOL.md` -- Full study protocol (this document is referenced in section 6 there)
- `protocol/cpe-items-addition.md` -- Mapping of CPE items to the CLPsych 2026 paper
- `platform/config.json` -- Machine-readable version consumed by the platform
- `platform/index.html` -- Platform that renders these items
