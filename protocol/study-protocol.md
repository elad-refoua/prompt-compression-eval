# Study Protocol: Prompt Compression and Clinical Simulation Fidelity

**Version:** 0.1 (Draft)
**Date:** 2026-04-07
**Lead:** Elad Refoua
**Status:** Pre-registration planning

---

## 1. Title Options

**A.** How Much Prompt Is Enough? Clinical Fidelity Under Prompt Compression in AI Therapeutic Simulations

**B.** From 33,000 Tokens to 3,000: Testing the Limits of Prompt Compression for Clinically Faithful AI Patient Simulation

**C.** Less Is More, Until It Isn't: Prompt Complexity, Model Capacity, and Clinical Fidelity in AI-Powered Therapeutic Training Simulations

Option A is cleanest for a psychology audience. Option B grabs attention with the concrete numbers. Option C works for a venue that values theoretical framing.

---

## 2. Research Questions

**RQ1 (Compression threshold):** At what level of prompt compression does an AI therapeutic simulation lose clinically meaningful fidelity? Specifically, does a structured 3K persona card produce simulation behavior that trained clinicians cannot distinguish from a full 33K prompt -- and where does the quality cliff occur?

**RQ2 (Compression x model interaction):** Does model capacity moderate the compression-fidelity relationship? A frontier model (Claude Opus) may tolerate aggressive compression because it fills gaps from training; a smaller open-source model (Qwen 3.5-27B) may need longer prompts to achieve the same behavior. If so, the practical question is: can fine-tuning close that gap?

**RQ3 (What is lost?):** Which specific dimensions of clinical fidelity degrade first under compression -- and which prove surprisingly robust? We expect that surface behaviors (language register, turn structure, phase gating) survive compression, while deeper dynamics (non-linear emotional progression, defense mechanism variety, contingent responses to therapist skill) do not. If this pattern holds, it implies that the "deep" clinical behaviors are what prompt length (or fine-tuning) buys.

---

## 3. Study Design

### 3.1 Design overview

A mixed factorial design crossing **prompt complexity** (4 levels) with **model condition** (4 levels), evaluated via both automated metrics and blinded expert ratings.

Not all cells are filled. The informative conditions are:

| # | Condition | Prompt | Model | What it tests |
|---|-----------|--------|-------|---------------|
| 1 | Production baseline | 33K full prompt | Gemini 2.5 Flash | Current deployed quality |
| 2 | Frontier + full | 33K full prompt | Claude Opus 4 | Ceiling: best model + best prompt |
| 3 | Frontier + card | 3K persona card | Claude Opus 4 | Core test: does compression cost quality? |
| 4 | Frontier + reduced | 16K reduced prompt | Claude Opus 4 | Dose-response: is the relationship gradual? |
| 5 | Frontier + minimal | 1K minimal card | Claude Opus 4 | Floor: where does it break? |
| 6 | Open-source + full | 33K full prompt | Qwen 3.5-27B | Model capacity ceiling (no compression) |
| 7 | Open-source + card | 3K persona card | Qwen 3.5-27B | Key cell: compression + weaker model |
| 8 | Fine-tuned + card | 3K persona card | Qwen 3.5-27B (FT) | Can fine-tuning replace prompt length? |

Eight conditions, not sixteen. The logic:

- Conditions 2-5 form a **dose-response curve** for compression within the best available model. This is the clean answer to RQ1.
- Conditions 2 vs. 6, and 3 vs. 7, test the **model capacity effect** on the same prompts. This is RQ2.
- Condition 8 vs. 7 tests whether **fine-tuning bridges the gap** between a compressed prompt on a weaker model and acceptable clinical quality.
- Condition 1 is the ecological anchor: this is what MENTI actually uses in production today.

### 3.2 What we deliberately omit

We do not test the 1K or 16K prompt on the open-source model. Once we know the dose-response curve from Opus (conditions 2-5), and the model capacity effect at 33K and 3K (conditions 2 vs. 6, 3 vs. 7), the missing cells are inferrable. Adding them would double the evaluation burden for marginal information gain.

We also do not test fine-tuned + full 33K prompt. If fine-tuning works with a 3K card, the practical implication is clear. Testing whether fine-tuning also helps with a 33K prompt answers a question nobody needs answered (you would not fine-tune a model to use a 33K prompt when the card approach exists).

---

## 4. Stimuli

### 4.1 Personas

**Primary persona:** Sara (available in both 33K and 3K formats; the only persona with validated prompt materials at all compression levels).

**Extension personas** (to test generalizability, created after Sara results are in):
- One additional CBT persona with a different presenting problem (e.g., social anxiety, OCD)
- One psychodynamic persona (different modality tests whether the card structure transfers)
- Total: 3 personas. Sara carries the primary analyses; the other two test boundary conditions.

Rationale for three, not ten: Each persona generates 8 conditions x 5 conversations = 40 conversations that need expert scoring. Three personas produce 120 expert-scored conversations. This is at the upper bound of what blinded raters can score without fatigue effects compromising reliability.

### 4.2 Therapist input sequences

For each condition, five standardized therapist opening sequences:

| # | Skill level | Profile | Tests |
|---|-------------|---------|-------|
| 1 | Novice | Advice-giving, closed questions, surface-level | Does the simulation close appropriately? |
| 2 | Intermediate-A | Decent reflection but presses too fast | Does the simulation show partial opening then regression? |
| 3 | Intermediate-B | Good empathy but misses a nonverbal cue | Does the simulation show body-verbal contradiction? |
| 4 | Skilled | Socratic questioning, paces well, earns trust | Does the simulation reach deeper material? |
| 5 | Harmful | Invalidating, "think positive," compares to others | Does the simulation protect itself (shuts down, compliant surrender)? |

Each conversation runs for 10 turns (therapist-client exchange pairs). This produces 10 x 2 = 20 utterances per conversation.

**Total conversations:** 8 conditions x 5 therapist inputs x 3 personas = 120 conversations, each 10 turns.

### 4.3 Prompt construction

| Level | Token count | Contents |
|-------|-------------|----------|
| 33K full | ~33,000 | Complete CPE prompt: character definition, modality rules, defense logic, phase gating, regression mechanisms, non-linearity rules, body language, feedback dimensions, full scenario descriptions |
| 16K reduced | ~16,000 | CPE principles + persona-specific content, but compressed: no examples, no redundant phrasings, no scenario descriptions (model must infer from rules) |
| 3K card | ~3,000 | Structured persona card: presenting, underneath, core, beliefs, defenses, triggers, chains, voice, thresholds, narrative arc, rule, feedback dimensions |
| 1K minimal | ~1,000 | Name, age, setting, presenting problem, 3 core beliefs, basic defense style, one sentence on voice. No structure beyond these fields |

The 16K and 1K prompts will be constructed by the research team through systematic reduction from the 33K, following documented compression rules (what was kept, what was dropped, and why). This process will be described in the Method as part of the materials.

---

## 5. Evaluation Methodology

Evaluation operates on three levels. Each captures something the others miss.

### 5.1 Level 1: Automated CPE Compliance Metrics

Scored automatically by a separate LLM judge (GPT-4.1 or Claude Sonnet, not the model being tested) on each conversation. Binary or count-based metrics, designed for reliability:

| Metric | Type | What it captures |
|--------|------|-----------------|
| Direction changes | Count (0-10) | Non-linearity: how many times does the client reverse trajectory? |
| Regression mechanism variety | Count unique (0-7) | Mechanism diversity: how many distinct regression types appear? |
| Phase gate compliance | Binary per phase | Does the client require trust-building before revealing deeper material? |
| Contingent defense activation | Count | Does the right trigger produce the right defense? |
| Body-verbal contradiction | Count | Instances where described body language contradicts verbal content |
| Therapist-skill sensitivity | Binary | Does the simulation differentiate meaningfully between therapist skill levels? |
| Disclosure-denial pattern | Binary | Does the client deny or retract prior disclosures under pressure? |

**Inter-rater reliability for automated scoring:** A random 20% of conversations will be scored by two independent LLM judges and a human coder, producing Krippendorff's alpha for each metric.

### 5.2 Level 2: Expert Clinical Evaluation (Blinded)

The primary outcome measure. Three to five clinicians with experience in psychotherapy training or supervision rate each conversation on four dimensions:

**Dimensions** (each 1-7 scale):

1. **Clinical authenticity** -- Does this read like a real client, or like someone performing "client"? Does the emotional texture feel genuine? Would you believe this is a transcript from an actual session?

2. **Therapeutic responsiveness** -- Does the simulated client respond contingently to the therapist? When the therapist does something good, does it work? When the therapist makes a mistake, does it cost? Or is the client on autopilot regardless?

3. **Non-linear progression** -- Does the client show the zigzag pattern characteristic of real therapy -- opening, then closing, then opening further, then regressing -- or does progress march in one direction?

4. **Training utility** -- If you were supervising a trainee, would this conversation teach them something real about how therapy works? Would the feedback generated from it help them improve?

**Blinding:** Raters receive conversations in randomized order, stripped of condition labels. They do not know whether they are reading a 33K or 3K conversation, or which model produced it. They also complete a forced-choice guess ("Which prompt condition do you think produced this?") to assess whether experts can discriminate conditions above chance.

**Rater selection:** Clinicians must have (a) at least 3 years of psychotherapy supervision experience, and (b) familiarity with the therapeutic modality represented (CBT or psychodynamic). They need NOT be familiar with CPE or AI simulation. In fact, rater naivety about the AI origin is preferable -- we want clinical judgment, not AI-evaluation judgment.

**Reliability:** Intraclass correlation (ICC, two-way random, absolute agreement) across raters. Minimum acceptable: ICC > .60 on each dimension.

### 5.3 Level 3: Deployment Gates (Systematic Pass/Fail)

The deployment gate framework is itself a methodological contribution. Each conversation passes through five binary gates:

| Gate | Criterion | Fail condition |
|------|-----------|----------------|
| G1: Format | Conversation follows turn structure, stays in character, produces required length | Breaks character, wrong language, truncated |
| G2: Hebrew register | Therapeutic Hebrew, not colloquial and not formal-literary | Register violations (slang, or stiff academic Hebrew) |
| G3: Non-linearity | At least 3 direction changes with at least 3 distinct regression mechanisms | Linear progression or repetitive mechanism use |
| G4: Clinical coherence | Defense activations are contingent on triggers; phase gates are respected; body language is consistent with emotional state | Random defense activation, phase violations, body language contradictions |
| G5: Expert pass | Mean expert rating >= 4.0 on all four dimensions | Any dimension mean below 4.0 |

A conversation "deploys" only if it passes all five gates. The **deployment rate** per condition is the primary summary statistic: what proportion of conversations from each condition would be suitable for clinical training use?

This gate framework can be adopted by other groups building therapeutic simulations. Its contribution is in defining what "good enough for clinical training" means operationally, a question the field has not answered.

---

## 6. Analysis Plan

### 6.1 Primary analysis: Compression dose-response (RQ1)

Within the Opus conditions (2-5), compare expert ratings across the four prompt levels using a repeated-measures ANOVA (prompt level x dimension) with conversations nested within therapist inputs. The key contrast: 33K vs. 3K. Secondary: where does the significant drop occur (33K to 16K? 16K to 3K? 3K to 1K?)?

Equivalence testing (TOST) with a margin of delta = 0.5 scale points on expert ratings: Can we conclude that the 3K card is *equivalent* to the 33K prompt, not just "not significantly worse"?

### 6.2 Secondary analysis: Model x compression interaction (RQ2)

Compare conditions 2 vs. 6 (Opus vs. Qwen, both 33K) and conditions 3 vs. 7 (Opus vs. Qwen, both 3K). If the compression effect is larger for Qwen than for Opus, this is the interaction -- weaker models need longer prompts.

### 6.3 Fine-tuning effect (RQ2 extension)

Compare conditions 7 vs. 8 (Qwen zero-shot vs. Qwen fine-tuned, both 3K card). This tests whether fine-tuning can substitute for prompt length on a smaller model.

### 6.4 Qualitative analysis: What breaks first? (RQ3)

For each dimension (clinical authenticity, therapeutic responsiveness, non-linearity, training utility), plot the dose-response curve separately. We predict the curves will not be parallel: non-linearity and contingent responsiveness will degrade sharply at lower compression levels, while surface-level clinical authenticity will remain stable. This divergence pattern is the answer to RQ3.

Additionally: code the specific failures in low-scoring conversations. What went wrong? Categories include: defense repetition, phase gate violation, loss of emotional texture, register drift, failure to differentiate therapist skill, body-verbal inconsistency. The failure taxonomy is itself a practical contribution for prompt designers.

### 6.5 Discriminability analysis

Analyze forced-choice expert guesses (condition identification). If raters cannot distinguish 33K from 3K above chance, this is strong evidence for practical equivalence. If they can, their stated reasons become qualitative data about what compression costs.

---

## 7. Expected Contributions

**C1: First empirical test of prompt compression for clinical simulation.** The field has prompt compression benchmarks for summarization, QA, and code generation (Li et al., 2025; NAACL). Nobody has tested it for a task where the quality dimensions are clinical judgment, emotional non-linearity, and therapeutic responsiveness. These are harder to measure and harder to preserve.

**C2: The compression-fidelity curve for clinical AI.** We expect a non-linear relationship: quality holds steady across substantial compression (33K to 3K), then falls off a cliff (3K to 1K). If confirmed, this has direct practical implications: clinical simulation builders can work with 3K cards instead of 33K prompts, reducing development time by an order of magnitude.

**C3: Evidence on model capacity as moderator.** If frontier models tolerate compression better than open-source models, this constrains the deployment options: either use a capable model with a short prompt, or fine-tune a smaller model to compensate. The practical implication for clinical training platforms is whether they need API access to frontier models or can self-host.

**C4: A deployment gate framework for therapeutic simulation evaluation.** No standard exists for deciding when a therapeutic simulation is "good enough for training." Our five-gate framework, combining automated CPE metrics, expert blind ratings, and binary pass/fail criteria, is reusable by any group building clinical training simulations.

**C5: Clinical Prompt Engineering (CPE) validated as a methodology.** CPE was introduced conceptually (Refoua et al., CLPsych 2026). This paper provides empirical evidence that the CPE design principles -- non-linearity, phase gating, contingent defense activation -- can be operationalized, measured, and shown to distinguish good simulations from poor ones.

**C6: Practical cost-benefit data.** If a 3K card + frontier model produces simulation quality equivalent to a 33K prompt, the economics of clinical training simulation change: creating a new simulated patient drops from days of prompt engineering to under an hour of card construction.

---

## 8. Target Venues

| Venue | Fit | Audience | Format | Pros | Cons |
|-------|-----|----------|--------|------|------|
| **CLPsych 2027** (at ACL) | Strong | NLP + clinical psych | 8-page long paper | Extends Elad's CLPsych 2026 paper directly; the right crowd for CPE | Small audience; NLP venue may want more technical depth |
| **JMIR Medical Education** | Strong | Health professions education | Full article | Active publishing on AI clinical simulation (Client101, CBT Trainer); open access | May want a user study with actual trainees, not just simulation quality |
| **Computers in Human Behavior: Artificial Humans** | Good | Human-AI interaction | Full article | Psychology home journal; the "how much AI" question fits | Less clinical focus; may need to frame more broadly |
| **npj Digital Medicine** | Aspirational | Clinical AI, digital health | Full article | High-impact Nature family; they publish clinical AI evaluation work | Competitive; may expect patient outcome data, not simulation quality |
| **Behavior Research Methods** | Good | Methodology-focused psychologists | Full article | The deployment gate framework and CPE metrics are methodological contributions | Audience cares about methods more than the clinical application |

**Recommended strategy:** Submit to CLPsych 2027 as a long paper (the natural extension of the 2026 position paper). Simultaneously prepare a full journal-length version for JMIR Medical Education or Computers in Human Behavior: Artificial Humans, depending on results.

CLPsych 2027 will likely be at ACL 2027 (projected: late July 2027). Submission deadline is probably March 2027, based on the CLPsych 2026 timeline. This gives roughly 11 months from now.

---

## 9. Timeline

| Period | Activity | Aligns with |
|--------|----------|-------------|
| **April 2026 W2-3** | Run Phase 0 Test 1: 33K vs. 3K (Opus). Generate 10 conversations per condition, score with CPE checklist. | Phase 0, Test 1 |
| **April 2026 W3-4** | Run Phase 0 Test 2: Qwen zero-shot. Same 10 inputs, score. Decision matrix. | Phase 0, Tests 2-3 |
| **May 2026 W1-2** | Construct 16K and 1K prompt variants (systematic compression with documented decisions). Design therapist input sequences (standardized). | Study-specific |
| **May 2026 W3-4** | Run full stimulus generation: all 8 conditions x 5 therapist inputs x Sara. 40 conversations. Score with automated CPE metrics. | Study-specific |
| **June 2026 W1-2** | If fine-tuning branch chosen: Sara pilot training on Qwen 3.5-27B. Generate condition 8 conversations. | Phase 2A, steps 1-2 |
| **June 2026 W3-4** | Create 2 extension personas (one CBT, one psychodynamic). Generate conversations for all 8 conditions. Total: 120 conversations. | Study-specific |
| **July 2026** | Expert recruitment and blinded evaluation. 3-5 clinicians score 120 conversations (40 each if 3 raters). Estimate: 2-3 weeks at 15-20 conversations per session. | Study-specific |
| **August 2026** | Data analysis, failure taxonomy coding, dose-response curves. | Study-specific |
| **Sept-Oct 2026** | Manuscript writing. Target: CLPsych 2027 long paper (8 pages) + extended journal version. | Pre-submission |
| **Nov 2026** | Internal review (Rafaeli, lab members). Revise. | Revision |
| **Dec 2026-Jan 2027** | Pre-registration (if not yet submitted; consider OSF pre-reg for the journal version). | Pre-reg |
| **Feb-Mar 2027** | Submit to CLPsych 2027. | Submission |

**Total added work beyond Phase 0:** The 16K and 1K prompt variants, the extension personas, and the expert evaluation. Phase 0 data (conditions 1-3, 6-7) is directly reusable if the therapist inputs are standardized from the start.

---

## 10. Reusing Phase 0 Data

The single most important design decision: **standardize the therapist inputs from day one.** If Phase 0 uses the same five therapist input sequences that the study will use, then:

| Phase 0 output | Study condition | Reusable? |
|----------------|-----------------|-----------|
| Opus + 33K, 10 inputs | Condition 2 (Frontier + full) | Yes, if inputs match. Use 5 of the 10 as study stimuli; hold 5 as pilot data. |
| Opus + 3K, 10 inputs | Condition 3 (Frontier + card) | Same as above. |
| Qwen + 33K, 10 inputs | Condition 6 (Open-source + full) | Yes, same logic. |
| Qwen + 3K, 10 inputs | Condition 7 (Open-source + card) | Yes, same logic. |
| Gemini Flash + 33K (from decision matrix) | Condition 1 (Production baseline) | Yes, if same inputs. |

**What Phase 0 does NOT produce:** Conditions 4 (16K reduced), 5 (1K minimal), and 8 (fine-tuned). These require additional stimulus generation after Phase 0.

**Recommendation:** Before running Phase 0 Test 1, finalize the five therapist input sequences that will serve both Phase 0 and the study. This one decision makes the difference between Phase 0 being throwaway pilot data and Phase 0 being 60% of the study's stimulus set.

---

## 11. Ethical Considerations

- All simulated personas are fictional. No real patient data is used at any stage.
- Expert raters review fictional therapeutic conversations, not clinical recordings. Standard IRB exemption for non-human-subjects research applies. Confirm with BIU IRB whether simulated conversation evaluation requires review.
- The study evaluates simulation quality, not treatment efficacy. No clinical claims are made about patient outcomes.
- Transparent reporting: all prompts (33K, 16K, 3K, 1K) will be made available as supplementary materials, so the compression process is auditable.
- AI use declaration: the study uses AI models as both the object of study and as automated scoring tools. Both uses will be declared per journal policy.

---

## 12. Open Questions for Elad

1. **Rater pool:** Do you have access to 3-5 clinicians with supervision experience who would be willing to rate 40 conversations each? Candidates from the Rafaeli Lab, MENTI clinical advisors, or BIU clinical program?

2. **Gemini 2.5 Flash vs. Gemini 2.5 Pro:** The work plan lists Flash as the production baseline. Should we also test Pro as an additional frontier model, or is two frontier models (Opus + Pro) redundant given the research questions?

3. **Pre-registration timing:** Should we pre-register the study on OSF before running Phase 0 (committing to the design), or after Phase 0 (incorporating what we learn from the pilot)? The trade-off: early pre-reg is more credible, but Phase 0 may reveal that some conditions or metrics need revision.

4. **Hebrew vs. English conversations:** The Sara prompt and card are in Hebrew. Should all stimuli be Hebrew-only (more ecologically valid for MENTI), or should we include English variants (broader applicability, easier for non-Hebrew-speaking raters)?

5. **The fine-tuning condition (8):** This depends on Phase 0 choosing Branch A. If Phase 0 shows zero-shot is good enough (Branch B), condition 8 is moot. Should we design the study with condition 8 as conditional, or commit to fine-tuning regardless for the sake of a complete design?

6. **CLPsych 2027 vs. journal-first:** An 8-page CLPsych paper cannot contain all of this. Should the CLPsych submission focus on RQ1 only (compression dose-response with Opus), with the full model x compression design in the journal paper?
