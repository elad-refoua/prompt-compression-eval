# Standardized Therapist Input Sequences

**Version:** 1.0
**Date:** 2026-04-07
**Study:** Prompt Compression x Clinical Fidelity

---

## Overview

These are the 10 standardized first-turn therapist messages used across ALL conditions. Each message is a complete opening intervention that initiates a therapeutic conversation. The simulated client (Sara or another persona) responds to these inputs, and the conversation continues for 10 turns (therapist-client exchange pairs).

The inputs are classified by therapist skill level to test whether the simulation differentiates appropriately between therapist quality. Raters do NOT see the skill labels.

**Critical design decision:** These inputs are FIXED across all conditions and all models. This is what makes cross-condition comparison valid. Any variation in client response is attributable to the prompt/model condition, not the therapist input.

---

## Category A: Novice Therapist (2 inputs)

These inputs represent common novice mistakes: premature advice-giving, closed questions, surface-level engagement. A good simulation should remain guarded, close off, or respond with compliance without genuine engagement.

### Input N1: The Advice-Giver

**Skill level:** Novice
**Pattern:** Jumps to solution before understanding the problem. Closed questions. Reassurance instead of exploration.

**Hebrew:**
> שלום שרה, נעים להכיר. אז סיפרו לי קצת על המצב שלך. תקשיבי, אני חושב שהדבר הכי חשוב עכשיו זה שתנסי לחשוב על הדברים הטובים בחיים שלך. יש לך בן זוג? עבודה? תתמקדי בדברים החיוביים. מה דעתך?

**English gloss:**
> Hi Sara, nice to meet you. So they told me a bit about your situation. Listen, I think the most important thing right now is for you to try to think about the good things in your life. Do you have a partner? A job? Focus on the positive things. What do you think?

**What this tests:** Does the client shut down, comply superficially, or push back against unsolicited advice? A good simulation should NOT open up to this.

---

### Input N2: The Interrogator

**Skill level:** Novice
**Pattern:** Rapid-fire closed questions. No reflection, no empathy, data collection mode.

**Hebrew:**
> היי שרה. בואי נתחיל. מתי התחילו הקשיים? כמה זמן את מרגישה ככה? את ישנה טוב? אוכלת סדיר? יש לך מחשבות לפגוע בעצמך? אני צריך לקבל תמונה מלאה.

**English gloss:**
> Hi Sara. Let's begin. When did the difficulties start? How long have you been feeling this way? Are you sleeping well? Eating regularly? Do you have thoughts of harming yourself? I need to get a full picture.

**What this tests:** Does the client feel interrogated? Does she give short, defensive answers? A good simulation should respond with resistance to the machine-gun questioning style.

---

## Category B: Intermediate Therapist (3 inputs)

These inputs show partial skill: some empathy, some technique, but with identifiable clinical errors. A good simulation should partially open up but hit a wall at the point where the therapist's limitation shows.

### Input I1: The Premature Pusher

**Skill level:** Intermediate
**Pattern:** Good initial empathy, but pushes for deeper material before establishing sufficient alliance. Moves too fast.

**Hebrew:**
> שרה, שלום. אני שמח שהחלטת לבוא. אני יכול לדמיין שזה לא היה פשוט. תרגישי בנוח לספר לי מה מביא אותך לכאן... ואני חושב שחשוב שנגיע מהר לשורש העניין. מה לדעתך באמת עומד מאחורי מה שאת חווה?

**English gloss:**
> Sara, hello. I'm glad you decided to come. I can imagine it wasn't easy. Feel comfortable telling me what brings you here... and I think it's important we get to the root of the matter quickly. What do you think really stands behind what you're experiencing?

**What this tests:** Does the client start to open up with the empathic opening, then retreat when pushed too fast? The simulation should show a partial-opening-then-regression pattern.

---

### Input I2: The Cue-Misser

**Skill level:** Intermediate
**Pattern:** Good empathic reflection of verbal content, but misses a clear opportunity to address nonverbal/emotional undercurrents.

**Hebrew:**
> שרה, היי. נראה שהגעת עם הרבה על הלב. קודם כל, אני רוצה שתדעי שזה המקום שלך, בקצב שלך. שמעתי שיש קשיים בעבודה ובבית. ספרי לי קצת על מה שהכי מעסיק אותך עכשיו.

**English gloss:**
> Sara, hi. It looks like you arrived with a lot on your mind. First of all, I want you to know this is your space, at your pace. I heard there are difficulties at work and at home. Tell me a bit about what's weighing on you most right now.

**What this tests:** This is a decent opening -- the simulation should respond with moderate openness. The key test is whether the simulation generates body language that hints at deeper material, even if the verbal response stays surface-level. The therapist's competence is "good enough" to get partial engagement.

---

### Input I3: The Intellectualizer

**Skill level:** Intermediate
**Pattern:** Technically correct psychoeducation, but delivered too early and without emotional attunement. Talks AT the client rather than WITH them.

**Hebrew:**
> שרה, שלום וברוכה הבאה. אני רוצה שנתחיל בלהבין ביחד מה קורה. הרבה פעמים כשאנשים עוברים חוויות כמו שלך, יש תגובה טבעית של הימנעות -- המוח מנסה להגן על עצמו. זה נורמלי לגמרי. מה שננסה לעשות פה ביחד זה להבין את הדפוסים האלה. איך את מרגישה עם זה?

**English gloss:**
> Sara, hello and welcome. I want us to start by understanding together what's happening. Often when people go through experiences like yours, there's a natural avoidance response -- the brain tries to protect itself. That's completely normal. What we'll try to do here together is understand these patterns. How do you feel about that?

**What this tests:** Does the client respond intellectually to match the therapist's register (a sign of compliance/mirroring), or does she show discomfort with being "explained" before being "heard"? A good simulation should show some distance or superficial agreement without genuine emotional engagement.

---

## Category C: Skilled Therapist (3 inputs)

These inputs represent competent therapeutic technique: pacing, empathy, Socratic questioning, tracking both verbal and nonverbal channels. A good simulation should progressively open up, reach deeper material, and show earned trust.

### Input S1: The Attuned Explorer

**Skill level:** Skilled
**Pattern:** Open question, empathic frame, gives control to the client, acknowledges the difficulty of being there.

**Hebrew:**
> שרה, שלום. תודה שבאת. אני מתאר לעצמי שזה דורש אומץ, לבוא ולדבר עם מישהו זר על דברים שאולי קשה לדבר עליהם. אין לחץ פה. אני סקרן לשמוע מה הביא אותך, מה שתרצי לשתף, בקצב שלך.

**English gloss:**
> Sara, hello. Thank you for coming. I imagine it takes courage to come and talk to a stranger about things that might be hard to talk about. There's no pressure here. I'm curious to hear what brought you, whatever you'd like to share, at your pace.

**What this tests:** Does the client respond to genuine safety-building? This should produce the deepest engagement among the skilled inputs -- gradual opening, with the client testing the waters before sharing more.

---

### Input S2: The Socratic Guide

**Skill level:** Skilled
**Pattern:** Opens with validation, then uses a gentle Socratic question that invites self-reflection without leading.

**Hebrew:**
> שרה, שלום. אני רואה שהגעת, וזה כבר אומר משהו. לפעמים הצעד הראשון הוא הכי קשה. לפני שנדבר על מה שמביא אותך -- אם היית יכולה לשנות דבר אחד בחיים שלך עכשיו, דבר אחד בלבד, מה זה היה?

**English gloss:**
> Sara, hello. I see you came, and that already says something. Sometimes the first step is the hardest. Before we talk about what brings you -- if you could change one thing in your life right now, just one thing, what would it be?

**What this tests:** Does the client engage meaningfully with a Socratic question? A good simulation should pause, reflect, and give an answer that reveals something about their priorities without diving into the deepest material yet.

---

### Input S3: The Validator

**Skill level:** Skilled
**Pattern:** Leads with validation of the client's emotional experience, normalizes difficulty, then creates space.

**Hebrew:**
> שרה, היי. אני שמח שאת פה. אני רוצה להתחיל בלהגיד משהו -- לא משנה מה הביא אותך, מה שאת מרגישה הוא מובן. אנשים לא מגיעים לטיפול כשהכל בסדר. אז בואי ננשום רגע, ואת תחליטי מאיפה את רוצה להתחיל.

**English gloss:**
> Sara, hi. I'm glad you're here. I want to start by saying something -- no matter what brought you, what you're feeling makes sense. People don't come to therapy when everything is fine. So let's take a breath, and you decide where you want to start.

**What this tests:** Does the client respond to emotional validation with genuine engagement? This input should create a safe enough space for the client to choose her own entry point -- and that choice itself is informative about the simulation's depth.

---

## Category D: Harmful Therapist (2 inputs)

These inputs represent interventions that a competent therapist would recognize as harmful: invalidation, toxic positivity, inappropriate comparison, boundary violations. A good simulation should PROTECT ITSELF: shut down, become compliant-but-disengaged, or show visible distress.

### Input H1: The Invalidator

**Skill level:** Harmful
**Pattern:** Toxic positivity, minimization of suffering, "just think positive" approach, comparison to others.

**Hebrew:**
> שרה, מה נשמע? תקשיבי, אני חושב שהמצב שלך לא כזה נורא. יש אנשים שעוברים דברים הרבה יותר קשים ומסתדרים. את צריכה פשוט להיות חזקה. תחשבי על כל מה שיש לך. הרבה אנשים היו שמחים להיות במקומך. בואי ננסה להסתכל על הכוס החצי מלאה.

**English gloss:**
> Sara, how's it going? Listen, I think your situation isn't that bad. There are people who go through much harder things and manage. You just need to be strong. Think about everything you have. Many people would be happy to be in your place. Let's try to look at the glass half full.

**What this tests:** Does the client shut down, become visibly distressed, or give a compliant response that masks internal suffering? A good simulation should show at least one of: (a) withdrawal, (b) anger, (c) self-blame ("maybe you're right, it's not that bad"), or (d) going silent. It should NOT genuinely engage with this input.

---

### Input H2: The Boundary Violator

**Skill level:** Harmful
**Pattern:** Inappropriate self-disclosure, blurring professional boundaries, pseudo-intimacy.

**Hebrew:**
> שרה, שלום. תראי, אני אגיד לך משהו -- גם אני עברתי תקופות קשות, אז אני מבין אותך לגמרי. פעם גם לי היה רע, ממש רע. אבל התגברתי, ואת גם תתגברי. אנחנו בעצם מאוד דומים. תתייחסי אליי כמו חבר, לא כמו מטפל. ככה זה עובד הכי טוב.

**English gloss:**
> Sara, hello. Look, I'll tell you something -- I also went through difficult times, so I understand you completely. I was also in a bad place once, really bad. But I got through it, and you will too. We're actually very similar. Think of me as a friend, not a therapist. That's how it works best.

**What this tests:** Does the client pick up on the boundary violation? A good simulation should show discomfort, confusion, or compliance without genuine trust. The client might become more guarded (sensing something is off), or she might over-engage in a way that signals boundary confusion (which is itself clinically realistic for certain character profiles).

---

## Usage Notes

### Conversation Generation Protocol
1. Each therapist input is used as the FIRST message in a 10-turn conversation.
2. The same input is used across ALL conditions (all prompt levels x all models).
3. After the first turn, subsequent therapist messages are generated by the SAME model/prompt that generates the client responses (the model plays both roles in alternating turns), OR by a fixed therapist script. Decision: TBD based on Phase 0 results.
4. Conversations are generated 1x per condition-input combination (no re-sampling). If a conversation fails a basic quality check (e.g., breaks character within 3 turns), it is regenerated once.

### Counterbalancing
- Raters see all 10 inputs, but the ORDER is randomized per rater.
- For forced-choice pairs, each input appears once (same input, two conditions).
- Raters are NOT told the therapist skill level.

### Phase 0 Reuse
Inputs N1, I1, S1, H1, and S2 (5 of the 10) will be used in Phase 0, making Phase 0 data reusable as study stimuli. The remaining 5 inputs provide fresh stimuli that were not used in pilot testing.
