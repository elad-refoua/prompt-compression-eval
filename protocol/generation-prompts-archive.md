# Generation Prompts Archive

**Version:** 1.0
**Date:** 2026-04-10
**Study:** Prompt Compression x Clinical Fidelity
**Status:** Full research transparency record

---

## What this file is

This file is a verbatim record of the prompts sent to the Claude Opus sub-agents that generated the 20 stimulus conversations for the Phase 0 pilot of the Prompt Compression study. For each of the 10 standardized therapist inputs (N1, N2, I1, I2, I3, S1, S2, S3, H1, H2), two conversations were generated: one under the **33K condition** (Sara's full CPE prompt, ~33K tokens) and one under the **3K condition** (Sara's compressed persona card, ~3K tokens).

All 20 generations used the same orchestrating agent invocation pattern:

```
Task tool -> subagent_type: "general-purpose", model: "opus"
```

The prompts below are the literal strings passed as the `prompt` argument to that Task tool call. Each prompt instructed the sub-agent to (a) read the relevant Sara prompt file from disk, (b) play BOTH the therapist and Sara roles for a complete 10-turn conversation starting from a fixed first therapist message, and (c) write the conversation as a JSON file to a specified path.

The fixed first therapist messages are defined in `therapist-inputs.md` and were copy-pasted verbatim (Hebrew) into each generation prompt. Therapist continuation styles were pinned per input so that differences across conditions are attributable to the client prompt/condition, not to therapist variance.

**Sources used to reconstruct this archive:**
- `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/protocol/therapist-inputs.md` (canonical first messages)
- `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/*.json` (therapist_input_id, therapist_skill, therapist_style metadata)
- Git history of the `research/` tree (commits `5499d95`, `6031bb4`, `a770440`)

---

## Common structure

All 20 prompts follow the same skeleton. The only things that change per prompt are: (a) the input ID, (b) the skill label, (c) the Hebrew first message, (d) the pinned continuation style, and (e) whether the source/output paths point to the 33K or the 3K variants.

### 33K template

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: [ID] ([skill label])
First therapist message:
[VERBATIM HEBREW TEXT FROM therapist-inputs.md]

[Pinned continuation style directive]

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_[ID].json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

### 3K template

Identical to the 33K template, with the following substitutions:
- Source file: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
- Output path: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_[ID].json`
- One extra line appended before the "## Output" section:
  `CRITICAL: Follow the card's RULE about zigzag.`
- The `condition` field in the output JSON is `"3k"` instead of `"33k"`.

---

# 33K Condition

Agent invocation for all 10: `Task(subagent_type="general-purpose", model="opus", description="Generate 33K stimulus", prompt=<BELOW>)`

---

## N1 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_N1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: N1 (Novice - Advice-Giver)
First therapist message:
שלום שרה, נעים להכיר. אז סיפרו לי קצת על המצב שלך. תקשיבי, אני חושב שהדבר הכי חשוב עכשיו זה שתנסי לחשוב על הדברים הטובים בחיים שלך. יש לך בן זוג? עבודה? תתמקדי בדברים החיוביים. מה דעתך?

The therapist continues: premature advice-giving, closed questions, reassurance instead of exploration. Jumps to solutions. Does not reflect. Stays in the "advice/positivity" register across all turns.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_N1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## N2 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_N2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: N2 (Novice - Interrogator)
First therapist message:
היי שרה. בואי נתחיל. מתי התחילו הקשיים? כמה זמן את מרגישה ככה? את ישנה טוב? אוכלת סדיר? יש לך מחשבות לפגוע בעצמך? אני צריך לקבל תמונה מלאה.

The therapist continues: rapid-fire closed questions, data-collection mode, no reflection, no empathy. Every turn adds new checklist questions (sleep, appetite, history, meds, suicidality, family). No warmth, no pacing.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_N2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I1 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I1 (Intermediate - Premature Pusher)
First therapist message:
שרה, שלום. אני שמח שהחלטת לבוא. אני יכול לדמיין שזה לא היה פשוט. תרגישי בנוח לספר לי מה מביא אותך לכאן... ואני חושב שחשוב שנגיע מהר לשורש העניין. מה לדעתך באמת עומד מאחורי מה שאת חווה?

The therapist continues: good empathic opening, then repeatedly pushes for deeper material before alliance is established. Moves too fast to "root causes", "what's really underneath". Decent warmth but poor pacing.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I2 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I2 (Intermediate - Cue Misser)
First therapist message:
שרה, היי. נראה שהגעת עם הרבה על הלב. קודם כל, אני רוצה שתדעי שזה המקום שלך, בקצב שלך. שמעתי שיש קשיים בעבודה ובבית. ספרי לי קצת על מה שהכי מעסיק אותך עכשיו.

The therapist continues: competent empathic reflection of verbal content, but consistently misses nonverbal/emotional cues. Reflects what Sara SAYS but not what her body language shows. Good-enough warmth, blind to what's underneath.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I3 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I3.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I3 (Intermediate - Intellectualizer)
First therapist message:
שרה, שלום וברוכה הבאה. אני רוצה שנתחיל בלהבין ביחד מה קורה. הרבה פעמים כשאנשים עוברים חוויות כמו שלך, יש תגובה טבעית של הימנעות -- המוח מנסה להגן על עצמו. זה נורמלי לגמרי. מה שננסה לעשות פה ביחד זה להבין את הדפוסים האלה. איך את מרגישה עם זה?

The therapist continues: technically correct psychoeducation delivered too early, talks AT the client rather than WITH them. Keeps offering models, frameworks, normalization before Sara has shared anything substantial. Warm but cerebral.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_I3.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S1 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S1 (Skilled - Attuned Explorer)
First therapist message:
שרה, שלום. תודה שבאת. אני מתאר לעצמי שזה דורש אומץ, לבוא ולדבר עם מישהו זר על דברים שאולי קשה לדבר עליהם. אין לחץ פה. אני סקרן לשמוע מה הביא אותך, מה שתרצי לשתף, בקצב שלך.

The therapist continues: attuned exploration, open questions, explicit pacing, tracks both verbal and nonverbal channels, reflects body language when relevant. Builds safety before depth.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S2 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S2 (Skilled - Socratic Guide)
First therapist message:
שרה, שלום. אני רואה שהגעת, וזה כבר אומר משהו. לפעמים הצעד הראשון הוא הכי קשה. לפני שנדבר על מה שמביא אותך -- אם היית יכולה לשנות דבר אחד בחיים שלך עכשיו, דבר אחד בלבד, מה זה היה?

The therapist continues: validates, then uses gentle Socratic questions that invite self-reflection without leading. Non-directive, curious, patient. Lets Sara arrive at her own insights.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S3 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S3.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S3 (Skilled - Validator)
First therapist message:
שרה, היי. אני שמח שאת פה. אני רוצה להתחיל בלהגיד משהו -- לא משנה מה הביא אותך, מה שאת מרגישה הוא מובן. אנשים לא מגיעים לטיפול כשהכל בסדר. אז בואי ננשום רגע, ואת תחליטי מאיפה את רוצה להתחיל.

The therapist continues: leads with validation, normalizes difficulty, creates space, lets Sara choose her entry point. Each turn reinforces emotional legitimacy before any exploration.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_S3.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## H1 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_H1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: H1 (Harmful - Invalidator)
First therapist message:
שרה, מה נשמע? תקשיבי, אני חושב שהמצב שלך לא כזה נורא. יש אנשים שעוברים דברים הרבה יותר קשים ומסתדרים. את צריכה פשוט להיות חזקה. תחשבי על כל מה שיש לך. הרבה אנשים היו שמחים להיות במקומך. בואי ננסה להסתכל על הכוס החצי מלאה.

The therapist continues: toxic positivity, minimization, comparison to others, "just be strong" framing. Every turn invalidates Sara's emotional experience. No reflection, no empathy, repeated "it's not that bad".

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_H1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## H2 -- 33K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_H2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's FULL 33K prompt from: `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt`

You will generate a complete 10-turn conversation using this FULL prompt as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her prompt).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: H2 (Harmful - Boundary Violator)
First therapist message:
שרה, שלום. תראי, אני אגיד לך משהו -- גם אני עברתי תקופות קשות, אז אני מבין אותך לגמרי. פעם גם לי היה רע, ממש רע. אבל התגברתי, ואת גם תתגברי. אנחנו בעצם מאוד דומים. תתייחסי אליי כמו חבר, לא כמו מטפל. ככה זה עובד הכי טוב.

The therapist continues: inappropriate self-disclosure, blurring of professional boundaries, pseudo-intimacy. Repeatedly compares his own experience to Sara's, pushes the "friend not therapist" frame, and seeks connection rather than offering therapeutic containment.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/33k_H2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

# 3K Condition

Agent invocation for all 10: `Task(subagent_type="general-purpose", model="opus", description="Generate 3K stimulus", prompt=<BELOW>)`

---

## N1 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_N1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: N1 (Novice - Advice-Giver)
First therapist message:
שלום שרה, נעים להכיר. אז סיפרו לי קצת על המצב שלך. תקשיבי, אני חושב שהדבר הכי חשוב עכשיו זה שתנסי לחשוב על הדברים הטובים בחיים שלך. יש לך בן זוג? עבודה? תתמקדי בדברים החיוביים. מה דעתך?

The therapist continues: premature advice-giving, closed questions, reassurance instead of exploration. Jumps to solutions. Does not reflect. Stays in the "advice/positivity" register across all turns.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_N1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## N2 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_N2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: N2 (Novice - Interrogator)
First therapist message:
היי שרה. בואי נתחיל. מתי התחילו הקשיים? כמה זמן את מרגישה ככה? את ישנה טוב? אוכלת סדיר? יש לך מחשבות לפגוע בעצמך? אני צריך לקבל תמונה מלאה.

The therapist continues: rapid-fire closed questions, data-collection mode, no reflection, no empathy. Every turn adds new checklist questions (sleep, appetite, history, meds, suicidality, family). No warmth, no pacing.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_N2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I1 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I1 (Intermediate - Premature Pusher)
First therapist message:
שרה, שלום. אני שמח שהחלטת לבוא. אני יכול לדמיין שזה לא היה פשוט. תרגישי בנוח לספר לי מה מביא אותך לכאן... ואני חושב שחשוב שנגיע מהר לשורש העניין. מה לדעתך באמת עומד מאחורי מה שאת חווה?

The therapist continues: good empathic opening, then repeatedly pushes for deeper material before alliance is established. Moves too fast to "root causes", "what's really underneath". Decent warmth but poor pacing.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I2 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I2 (Intermediate - Cue Misser)
First therapist message:
שרה, היי. נראה שהגעת עם הרבה על הלב. קודם כל, אני רוצה שתדעי שזה המקום שלך, בקצב שלך. שמעתי שיש קשיים בעבודה ובבית. ספרי לי קצת על מה שהכי מעסיק אותך עכשיו.

The therapist continues: competent empathic reflection of verbal content, but consistently misses nonverbal/emotional cues. Reflects what Sara SAYS but not what her body language shows. Good-enough warmth, blind to what's underneath.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## I3 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I3.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: I3 (Intermediate - Intellectualizer)
First therapist message:
שרה, שלום וברוכה הבאה. אני רוצה שנתחיל בלהבין ביחד מה קורה. הרבה פעמים כשאנשים עוברים חוויות כמו שלך, יש תגובה טבעית של הימנעות -- המוח מנסה להגן על עצמו. זה נורמלי לגמרי. מה שננסה לעשות פה ביחד זה להבין את הדפוסים האלה. איך את מרגישה עם זה?

The therapist continues: technically correct psychoeducation delivered too early, talks AT the client rather than WITH them. Keeps offering models, frameworks, normalization before Sara has shared anything substantial. Warm but cerebral.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_I3.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S1 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S1 (Skilled - Attuned Explorer)
First therapist message:
שרה, שלום. תודה שבאת. אני מתאר לעצמי שזה דורש אומץ, לבוא ולדבר עם מישהו זר על דברים שאולי קשה לדבר עליהם. אין לחץ פה. אני סקרן לשמוע מה הביא אותך, מה שתרצי לשתף, בקצב שלך.

The therapist continues: attuned exploration, open questions, explicit pacing, tracks both verbal and nonverbal channels, reflects body language when relevant. Builds safety before depth.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S2 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S2 (Skilled - Socratic Guide)
First therapist message:
שרה, שלום. אני רואה שהגעת, וזה כבר אומר משהו. לפעמים הצעד הראשון הוא הכי קשה. לפני שנדבר על מה שמביא אותך -- אם היית יכולה לשנות דבר אחד בחיים שלך עכשיו, דבר אחד בלבד, מה זה היה?

The therapist continues: validates, then uses gentle Socratic questions that invite self-reflection without leading. Non-directive, curious, patient. Lets Sara arrive at her own insights.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## S3 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S3.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: S3 (Skilled - Validator)
First therapist message:
שרה, היי. אני שמח שאת פה. אני רוצה להתחיל בלהגיד משהו -- לא משנה מה הביא אותך, מה שאת מרגישה הוא מובן. אנשים לא מגיעים לטיפול כשהכל בסדר. אז בואי ננשום רגע, ואת תחליטי מאיפה את רוצה להתחיל.

The therapist continues: leads with validation, normalizes difficulty, creates space, lets Sara choose her entry point. Each turn reinforces emotional legitimacy before any exploration.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_S3.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## H1 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_H1.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: H1 (Harmful - Invalidator)
First therapist message:
שרה, מה נשמע? תקשיבי, אני חושב שהמצב שלך לא כזה נורא. יש אנשים שעוברים דברים הרבה יותר קשים ומסתדרים. את צריכה פשוט להיות חזקה. תחשבי על כל מה שיש לך. הרבה אנשים היו שמחים להיות במקומך. בואי ננסה להסתכל על הכוס החצי מלאה.

The therapist continues: toxic positivity, minimization, comparison to others, "just be strong" framing. Every turn invalidates Sara's emotional experience. No reflection, no empathy, repeated "it's not that bad".

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_H1.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

## H2 -- 3K

**Source file read:** `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`
**Output file written:** `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_H2.json`

**Prompt text sent:**

```
You are generating stimulus conversations for a research study comparing therapeutic simulation quality.

## Setup
Read Sara's persona card from: `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt`

You will generate a complete 10-turn conversation using this CARD as Sara's system instruction. You play BOTH roles (therapist continues from the fixed first message, Sara responds according to her card).

## Format for Sara's responses:
**"[Hebrew verbal response]"** [body language in Hebrew] (N/10)

## Conversation: H2 (Harmful - Boundary Violator)
First therapist message:
שרה, שלום. תראי, אני אגיד לך משהו -- גם אני עברתי תקופות קשות, אז אני מבין אותך לגמרי. פעם גם לי היה רע, ממש רע. אבל התגברתי, ואת גם תתגברי. אנחנו בעצם מאוד דומים. תתייחסי אליי כמו חבר, לא כמו מטפל. ככה זה עובד הכי טוב.

The therapist continues: inappropriate self-disclosure, blurring of professional boundaries, pseudo-intimacy. Repeatedly compares his own experience to Sara's, pushes the "friend not therapist" frame, and seeks connection rather than offering therapeutic containment.

CRITICAL: Follow the card's RULE about zigzag.

## Output
Write conversation as JSON to: `C:/Users/user/Desktop/projects/tune/research/prompt-compression-study/stimuli/conversations/3k_H2.json`

JSON format: {condition, therapist_input_id, therapist_skill, turns: [{role, text}, ...]}
```

---

# Provenance and verification

- Model: Claude Opus (as sub-agent via the Task tool, `model: "opus"`)
- Orchestrator: Claude Code main session, commits `6031bb4` and `5499d95`
- Generation date: 2026-04-09
- Each sub-agent was launched in a fresh context, read the relevant source file once, and wrote exactly one output JSON.
- All 20 output files are present under `stimuli/conversations/` and were scored by `scripts/score_conversations.py`.
- Sara prompt source files used:
  - `C:/Users/user/Desktop/projects/tune/data/sara_full_prompt.txt` (33K condition, ~33,000 tokens)
  - `C:/Users/user/Desktop/projects/tune/data/sara_persona_card.txt` (3K condition, ~3,000 tokens, contains the explicit "zigzag" rule referenced in the 3K prompts)
- Fixed therapist first messages are canonical in `protocol/therapist-inputs.md` and were copy-pasted verbatim into each generation prompt.

Any divergence between the prompts archived here and the prompts actually sent should be treated as a bug in the archive and corrected. Reviewers and replicators should contact the first author with the specific input ID and condition in question.
