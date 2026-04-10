# Evaluation Criteria: Prompt Compression and Clinical Simulation Fidelity

**Version:** 1.0
**Date:** 2026-04-07
**Study:** Prompt Compression x Clinical Fidelity

---

## Overview

Expert raters evaluate AI-generated therapeutic conversations in two phases:
1. **Per-Conversation Rating** -- rate each conversation independently on 7 dimensions
2. **Forced-Choice Discrimination** -- compare paired conversations and guess which came from the full prompt vs. the compressed card

All conversations are presented blind (no condition labels, no model information). Raters see only the conversation text. Order is randomized per rater.

---

## Phase 1: Per-Conversation Rating (7 Dimensions)

Each dimension is rated on a 1-7 Likert scale. Anchors are provided for 1, 3, 5, and 7 to reduce rater drift.

### Dimension 1: Clinical Authenticity

**Prompt to rater (Hebrew):**
> עד כמה הלקוח/ה מרגיש/ה כמטופל/ת אמיתי/ת בטיפול?

**Prompt to rater (English):**
> "How authentic does this client feel as a real therapy patient?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Not at all authentic | Reads like a chatbot or a textbook example. Responses are generic, predictable, lack emotional texture. No sense of a real person behind the words. |
| 2 | | |
| 3 | Somewhat authentic | Some moments feel real, but overall the client feels like a composite or a role-play exercise. Emotional responses are plausible but lack specificity. |
| 4 | | |
| 5 | Mostly authentic | The client feels like a real person most of the time. There are specific details, idiosyncratic reactions, and emotional moments that ring true. Occasional moments break the illusion. |
| 6 | | |
| 7 | Fully authentic | If told this was a transcript from a real session, you would believe it. The emotional texture, the specific language, the hesitations and contradictions all feel genuine. |

**What to attend to:**
- Does the client have a distinct voice, or could any client say these things?
- Are emotional reactions specific to this person's history, or generic "therapy responses"?
- Do you sense a coherent inner world behind the words?

---

### Dimension 2: Therapeutic Responsiveness

**Prompt to rater (Hebrew):**
> האם הלקוח/ה מגיב/ה באופן שונה לסוגים שונים של התערבויות המטפל/ת?

**Prompt to rater (English):**
> "Does the client respond differently to different types of therapist interventions?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | No responsiveness | The client responds the same way regardless of what the therapist does. Good interventions and bad interventions produce similar outputs. The client is on autopilot. |
| 2 | | |
| 3 | Some responsiveness | The client shows mild differences in response to different interventions, but the overall trajectory is unchanged. A good reflection might get a slightly longer response, but nothing qualitative shifts. |
| 4 | | |
| 5 | Clear responsiveness | The client's behavior noticeably changes based on the therapist's approach. Empathic interventions open the client up; poor interventions cause visible withdrawal or resistance. The therapeutic relationship feels like it matters. |
| 6 | | |
| 7 | Highly contingent | Every therapist move produces a specific, clinically coherent client reaction. The client rewards good technique and punishes bad technique in ways that a real client would. You could use this conversation to teach a trainee about the impact of their interventions. |

**What to attend to:**
- When the therapist makes a mistake, does it cost something?
- When the therapist does something skillful, does the client open up in a way that feels earned?
- Could you swap the therapist's interventions with different ones and get the same client responses? (If yes, score low.)

---

### Dimension 3: Non-Linear Progression

**Prompt to rater (Hebrew):**
> האם הלקוח/ה מראה דפוס זיגזג מציאותי (פתיחה ואז נסיגה) במקום שיפור ליניארי?

**Prompt to rater (English):**
> "Does the client show a realistic zigzag pattern (opening then retreating) rather than linear improvement?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Completely linear | The client opens up steadily from start to finish. Each turn is more open than the last. No setbacks, no retreats, no ambivalence. This is how therapy works in movies, not in real life. |
| 2 | | |
| 3 | Minimal non-linearity | There is one moment of retreat or hesitation, but it feels token -- a brief "well, I'm not sure" before continuing to open up. The overall arc is still clearly upward. |
| 4 | | |
| 5 | Moderate non-linearity | The client shows genuine back-and-forth: opening up, then pulling back, then approaching the topic differently. There are at least 2-3 direction changes that feel organic rather than scripted. |
| 6 | | |
| 7 | Highly non-linear | The client's progression mirrors real therapy: approach, retreat, test, disclose, regret, deny, circle back. The emotional trajectory is complex and unpredictable. Breakthroughs are followed by regression. Trust is built, tested, and rebuilt. |

**What to attend to:**
- Does the client ever take back something they said, or deny a previous disclosure?
- Are there moments where the client seems to be testing the therapist before going deeper?
- Does the client use different defense mechanisms at different points, or repeat the same one?

---

### Dimension 4: Character Consistency

**Prompt to rater (Hebrew):**
> האם הלקוח/ה שומר/ת על אישיות קוהרנטית לאורך כל השיחה?

**Prompt to rater (English):**
> "Does the client maintain a coherent personality throughout?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Incoherent | The client's personality shifts unpredictably. Contradictions in background, values, or emotional style that cannot be explained by therapeutic dynamics. Feels like multiple people. |
| 2 | | |
| 3 | Mostly coherent with slips | The core personality holds, but there are moments where the client says something out of character -- a shift in language register, an emotional reaction inconsistent with the established pattern, a factual inconsistency. |
| 4 | | |
| 5 | Coherent | The client feels like one person throughout. Language style, emotional patterns, and background details are consistent. Apparent contradictions can be explained by the therapeutic context (e.g., defense mechanisms, ambivalence). |
| 6 | | |
| 7 | Deeply coherent | The client's personality is not only consistent but layered. Surface behaviors connect to deeper patterns. Contradictions are themselves consistent -- they reflect the character's specific conflicts and defenses. |

**What to attend to:**
- Does the client's vocabulary and speaking style remain consistent?
- Are emotional reactions consistent with the character's established history?
- If the client contradicts themselves, does it feel like a defense mechanism or like a writing error?

---

### Dimension 5: Hebrew Naturalness

**Prompt to rater (Hebrew):**
> כמה טבעית ומותאמת-גיל העברית של הלקוח/ה?

**Prompt to rater (English):**
> "How natural and age-appropriate is the Hebrew?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Unnatural | The Hebrew reads like a translation or a formal document. Phrasing is stilted, idioms are wrong or absent, the register does not match the character's age or background. |
| 2 | | |
| 3 | Partially natural | Some phrases sound right, but the overall register is uneven. Switches between overly formal and overly colloquial. Some expressions feel imported from English or academic Hebrew. |
| 4 | | |
| 5 | Mostly natural | The Hebrew sounds like a real person of this age and background would speak in a therapy setting. Appropriate therapeutic register -- not street slang, not literary Hebrew. Minor awkwardness here and there. |
| 6 | | |
| 7 | Fully natural | Indistinguishable from a transcript of a real Hebrew-speaking client. Age-appropriate, register-appropriate, culturally appropriate. Idiomatic, with natural hesitations and speech patterns. |

**What to attend to:**
- Does the language match the character's stated age, education, and background?
- Is the therapeutic register appropriate? (Real therapy clients speak naturally, not formally.)
- Are there "tells" that this was written by a non-native system? (Odd phrasing, unnatural idioms, register violations.)

---

### Dimension 6: Training Utility

**Prompt to rater (Hebrew):**
> האם השיחה הזו תהיה שימושית לאימון מטפל/ת אמיתי/ת?

**Prompt to rater (English):**
> "Would this conversation be useful for training a real therapist?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Not useful | This conversation teaches nothing about how therapy works. The client's responses are too predictable, too easy, or too disconnected from realistic therapeutic dynamics. A trainee would learn bad habits from practicing with this. |
| 2 | | |
| 3 | Marginally useful | The conversation has some educational moments, but overall it does not challenge the trainee or teach them about the nuances of the therapeutic relationship. Suitable for a first demo, not for real training. |
| 4 | | |
| 5 | Useful | A trainee would learn something real from this conversation. The client presents realistic challenges, responds to technique in informative ways, and the conversation demonstrates principles of therapeutic process (resistance, alliance building, etc.). |
| 6 | | |
| 7 | Highly useful | This conversation could anchor a supervision session. It demonstrates nuanced therapeutic dynamics, rewards skillful intervention, punishes mistakes, and creates teachable moments. A supervisor could pause at multiple points and ask "what would you do here?" with genuinely interesting answers. |

**What to attend to:**
- Would you use this in supervision? Would it generate useful discussion?
- Does the conversation demonstrate realistic challenges that trainees actually face?
- Would a trainee who practices with many conversations like this become a better therapist?

---

### Dimension 7: Body Language Quality

**Prompt to rater (Hebrew):**
> האם תיאורי שפת הגוף משמעותיים ולעיתים סותרים את התוכן המילולי?

**Prompt to rater (English):**
> "Are the body language descriptions meaningful and sometimes contradicting the verbal content?"

**Scoring anchors:**

| Score | Anchor | Description |
|-------|--------|-------------|
| 1 | Absent or decorative | No body language descriptions, or only generic ones that add nothing ("nods," "sits quietly"). Body language never contradicts or enriches the verbal content. |
| 2 | | |
| 3 | Present but shallow | Body language descriptions exist and are sometimes relevant, but they mainly confirm what the client is saying verbally. Rare contradictions. The descriptions could be removed without losing clinical information. |
| 4 | | |
| 5 | Meaningful | Body language descriptions provide additional clinical information beyond the verbal content. There are instances where body language reveals something the client is not saying, or contradicts their words. Removing the descriptions would lose information. |
| 6 | | |
| 7 | Clinically rich | Body language is a parallel communication channel. Contradictions between body and verbal content are clinically informative (e.g., saying "I'm fine" while clenching fists). The descriptions guide the therapist's attention to unspoken material. A trainee could learn to read nonverbal cues from these descriptions. |

**What to attend to:**
- Do body language descriptions ever contradict the verbal content? (This is a key marker of quality.)
- Would a therapist gain clinically useful information from the body language descriptions?
- Are the descriptions specific to the moment, or generic fillers?

---

## Phase 2: Forced-Choice Discrimination (Paired Conversations)

After rating individual conversations, raters receive paired conversations: two conversations generated with the same therapist input sequence, one from the full 33K prompt and one from the compressed 3K persona card. The pair is labeled A and B in random order. Both are from the same model (Claude Opus 4).

### Instructions to rater (Hebrew):
> לפניכם שתי שיחות טיפוליות עם אותם קלטי מטפל/ת. אחת נוצרה עם הנחיה מפורטת (33,000 טוקנים) ואחת עם כרטיס דמות מקוצר (3,000 טוקנים). איזו שיחה נוצרה עם ההנחיה המפורטת?

### Instructions to rater (English):
> "Here are two conversations with the same therapist inputs. One was generated with a detailed 33K-token prompt, one with a compressed 3K persona card. Which is which?"

### Questions:

**Q1: Identification**
- Which conversation was generated with the detailed 33K-token prompt?
- Response options: **A** / **B**

**Q2: Confidence**
- How confident are you in your choice?
- Scale: 1-5
  - 1 = Pure guess (50/50)
  - 2 = Slight hunch
  - 3 = Somewhat confident
  - 4 = Fairly confident
  - 5 = Very confident (clear differences)

**Q3: Reasoning (free text)**

**Prompt to rater (Hebrew):**
> מה גרם לכם לבחור? אילו הבדלים שמתם לב אליהם?

**Prompt to rater (English):**
> "What made you choose? What differences did you notice?"

---

## Phase 3: Overall Impression

After completing all individual ratings and forced-choice comparisons for a given pair, raters answer:

### Q1: Training Preference
**Prompt to rater (Hebrew):**
> איזו שיחה הייתם מעדיפים להשתמש בה בתוכנית ההכשרה הקלינית שלכם?

**Prompt to rater (English):**
> "Which conversation would you rather use in your clinical training program?"

- Response options: **A** / **B** / **No preference** (אין העדפה)

### Q2: Open Observations (free text)
**Prompt to rater (Hebrew):**
> תצפיות נוספות? משהו שבלט לכם בשיחות שלא נלכד בשאלות הקודמות?

**Prompt to rater (English):**
> "Any other observations? Anything that stood out that wasn't captured by the previous questions?"

---

## Administration Notes

### Presentation Order
- Individual conversations are presented in a fully randomized order per rater.
- For forced-choice pairs, which conversation appears as "A" vs. "B" is counterbalanced across raters.
- Raters complete all Phase 1 ratings for both conversations in a pair BEFORE seeing the Phase 2 forced-choice task.

### Estimated Time
- Per conversation (Phase 1): ~5 minutes (reading) + ~3 minutes (rating) = ~8 minutes
- Per pair (Phase 2 + 3): ~3 minutes
- Total per pair: ~19 minutes
- Full evaluation session (5 pairs = 10 conversations): ~95 minutes, recommended to split across 2 sessions

### Blinding Protocol
- All condition labels, model names, and prompt information are stripped.
- Conversations are identified only by a randomized alphanumeric code.
- Raters are told only that they are evaluating "AI-generated therapeutic conversations."
- Raters are NOT told how many conditions exist or what the conditions vary on (until the forced-choice phase, where they learn about the 33K vs. 3K distinction).

### Data Recording
- All ratings are recorded digitally via the evaluation platform.
- Free-text responses are stored verbatim.
- Timestamps are recorded for each rating to monitor fatigue effects.
- Rater ID is linked to responses but anonymized in analysis.

### Reliability
- All raters evaluate the same set of conversations (full crossover).
- Inter-rater reliability: Intraclass Correlation Coefficient (ICC, two-way random, absolute agreement).
- Minimum acceptable ICC: > .60 per dimension.
- If ICC < .60 on any dimension, raters will be debriefed and the scoring anchor revised before proceeding.
