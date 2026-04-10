# Expert Rater Qualifications

**Version:** 2.0
**Date:** 2026-04-10
**Study:** Prompt Compression x Clinical Fidelity
**Purpose:** Define qualifications, target N, recruitment approach, and ideal profile for the expert raters who will blind-evaluate simulated therapeutic conversations in Hebrew. **Voluntary collaboration -- no monetary compensation.**

---

## 1. Honest Note on Sources

**What the literature actually says (and doesn't say):**

The sources I reviewed (Kobak et al. 2005 on rater training, Muse & McManus on CBT competence, Beck Institute CTRS-R guidelines, Koo & Li 2016 on ICC, Cicchetti 1994) discuss rater **training and calibration**, not fixed minimum experience thresholds. **There is no single source I found that mandates "X years post-specialization"** as a universal floor.

What the literature consistently emphasizes:
- **Construct familiarity** matters more than raw years of experience (a junior clinician who understands the rating construct is often more reliable than a senior one who doesn't)
- **Training and calibration** against expert benchmarks is the standard quality control
- **Reliability is measured empirically** (ICC) rather than assumed from credentials

So any numerical threshold I recommend below is a **reasonable synthesis**, not a verified requirement. The final call on "who counts as an expert" is a judgment call that depends on who is actually available and willing.

---

## 2. Background

Raters will blind-evaluate 20 simulated client conversations (10 with a 33K prompt, 10 with a 3K prompt) on clinical fidelity, realism, and therapeutic usefulness. The simulations are in Hebrew, the client persona is depressed (Sara -- 38, teacher, moderate unipolar depression), and the therapist inputs span four skill tiers.

Raters need enough clinical expertise to recognize:
1. Whether Sara behaves like a real depressed Israeli client
2. Whether her response pattern is clinically appropriate to the therapist's skill level

---

## 3. What Actually Matters for This Study

Ranked in descending order of importance:

### 3.1 Must-haves (non-negotiable)

**Hebrew first-language clinical proficiency.** The stimuli are in Hebrew and depend on nuanced body-language descriptions ("מבט מזוגג", "קול שטוח", "עוטפת את עצמה"). A rater who needs translation loses the signal. This is the one non-negotiable requirement.

**Clinical experience with depression or mood-related presentations.** The persona has major depression. The rater needs to recognize authentic depressive presentation vs. caricature.

**Working knowledge of psychotherapy as a process.** The rater needs to understand what an alliance rupture looks like, what premature pushing looks like, what containment looks like. This can come from any therapeutic orientation.

### 3.2 Strong preferences

**Familiarity with CBT or structured therapy for depression.** Sara is designed as a CBT case. Raters who know CBT will recognize appropriate and inappropriate interventions faster. A rater from a purely psychodynamic background can still rate clinical authenticity, but will be less confident on "therapeutic utility" items.

**Experience with training or supervision of trainees.** Raters who have supervised role-plays or watched therapy recordings adapt faster to the "evaluate a simulated session" task.

### 3.3 Nice-to-haves

**Licensure** (Israeli psychologist, social worker, psychiatrist). Licensure is a useful signal of clinical maturity, but is not strictly required. A licensed psychodynamic therapist with no CBT experience may be less useful than a senior doctoral student with strong CBT training.

**Prior exposure to AI/simulation tools in clinical training.** Not required but helpful.

### 3.4 Does NOT matter much

- Specific number of years of experience
- Academic rank
- Research publications

---

## 4. Target N and Reliability

### 4.1 How many raters?

- **Target: 5 raters**
- **Minimum: 3 raters**
- **Maximum useful: 7 raters**

This range is consistent with published competence-rating studies (Kobak et al. 2005; Muse & McManus). Fewer than 3 is not enough to detect disagreement; more than 7 yields diminishing returns and adds coordination overhead.

### 4.2 Reliability targets

Based on Cicchetti (1994) and Koo & Li (2016) ICC guidelines:
- **Primary target: ICC(2,k) >= 0.70** ("good" reliability) on aggregate dimension ratings
- **Per-dimension floor: ICC(2,k) >= 0.60** ("moderate" reliability)
- **Forced-choice task: Cohen's kappa >= 0.60** across raters

If reliability is below these targets, the analysis plan includes sensitivity analysis and calibration discussion.

---

## 5. Recruitment Approach

### 5.1 Framing

**This is a voluntary, collegial collaboration** -- not a paid research gig. Raters will be asked to donate 2-4 hours of their time to review 10 conversation pairs. The framing matters: we are asking for a professional favor from colleagues who care about clinical training quality.

### 5.2 What raters get

- **Acknowledgment in the published paper** (by name, in the Acknowledgments section or as contributors, depending on venue policy)
- **Early access to results** and to the evaluation platform
- **Potential co-authorship** if their contribution meets ICMJE criteria (substantial intellectual contribution to the study design, analysis, or interpretation beyond rating). This is evaluated at the end; rating alone does not guarantee authorship.
- **Access to the trained MENTI model** if it is eventually built
- **Professional connection to the research** for future collaboration

### 5.3 What raters give

- ~2-4 hours of their time (10 pair evaluations at ~15-20 min each, plus reading instructions and consent)
- Careful, honest clinical judgment on the evaluation dimensions
- Willingness to be contacted for one clarification discussion if needed

### 5.4 Recruitment channels

Elad's clinical network, Yuval Holzman's network, Bar-Ilan clinical psychology faculty, Israeli clinical psychology mailing lists. Yuval has been asked to suggest 2-3 names from her own network.

### 5.5 Recruitment sequence

1. Personal WhatsApp or email from Elad to each candidate with a brief description and the platform link
2. If interested, candidate receives:
   - Link to study protocol (public on GitHub)
   - Link to consent form (`protocol/consent-form.md`)
   - Personalized link to the evaluation platform
3. Candidate can ask clarifying questions before committing
4. If candidate agrees, they complete the evaluation at their own pace (deadline: ~2 weeks from invitation)
5. Follow-up thank-you with preliminary results summary

### 5.6 What to do if raters decline

If fewer than 3 raters agree, the study pauses until additional raters are found. We do not run with N<3 because reliability cannot be meaningfully computed.

---

## 6. IRB/Ethics Considerations

Key points for IRB submission:

1. **No real patient data.** All stimulus conversations are synthetic, generated by AI agents from fictional persona descriptions. No patient information is involved.
2. **Raters are research collaborators, not subjects.** The study is evaluating AI-generated content, not the raters themselves. Rater demographic data is minimal (name, role, years of experience) and used only to describe the sample.
3. **Voluntary participation with informed consent.** Raters consent via the consent form. They can withdraw at any time.
4. **No risk of harm.** Reviewing fictional therapeutic dialogue poses no risk beyond that of normal clinical work.
5. **Data handling.** Rater-identifiable data is stored only in the private Google Sheets backend. Published data is aggregated and anonymized.

This should qualify for **expedited IRB review** or potentially an exemption, depending on the reviewing institution's interpretation.

---

## 7. Profile of the Ideal Rater

Someone who:
- Is a Hebrew-first clinician practicing in Israel
- Has treated adults with depression
- Has at least some familiarity with CBT or structured therapy
- Is curious about AI in clinical training
- Has the intellectual rigor to give honest ratings (not just say "it's all fine")
- Has 2-4 hours of time to donate over the next 2 weeks
- Is willing to be acknowledged by name in a published paper

The ideal rater does NOT need to be:
- A tenured professor
- Internationally known
- A specific number of years post-specialization
- Published in AI or simulation research

---

## 8. Alternative Tiers (if ideal raters unavailable)

**Tier A (preferred):** Licensed Israeli clinical psychologists or senior social workers with CBT experience and depression treatment background. Target for all 5 raters.

**Tier B (acceptable):** Advanced clinical psychology trainees ("מתמחים קליניים") in their 3rd or 4th year of specialization, supervised by a licensed clinical psychologist. Acceptable up to 2 of the 5 slots.

**Tier C (minimum viable):** A mix including MA-level clinicians with supervised practice experience, psychiatrists with psychotherapy background, or doctoral students specializing in clinical psychology. Use only if Tiers A and B cannot yield 3 raters.

**Not acceptable:**
- Non-clinicians (academic researchers without clinical training)
- Clinicians who cannot read Hebrew fluently
- Clinicians with no therapy experience of any kind

---

## 9. Key Sources (what I actually read)

The sources below shaped my thinking but **none of them mandate a specific "years of experience" threshold**. I cite them for general methodological grounding, not for prescriptive requirements.

- [Kobak et al. -- Rater Training and Certification for Clinical Trials](https://pmc.ncbi.nlm.nih.gov/articles/PMC4301026/) -- consensus on training and calibration protocols
- [Muse & McManus -- Introducing the QACP](https://pmc.ncbi.nlm.nih.gov/articles/PMC9422322/) -- CBT competence assessment
- [Beck Institute CTRS-R](https://beckinstitute.org/cbt-resources/resources-for-professionals-and-students/cognitive-therapy-rating-scale-revised-ctrs-r/) -- the standard CBT competence rating scale
- [Koo & Li 2016 -- ICC Reliability Guidelines](https://pmc.ncbi.nlm.nih.gov/articles/PMC4913118/) -- ICC interpretation (0.5 poor, 0.5-0.75 moderate, 0.75-0.9 good, >0.9 excellent)
- [Cicchetti 1994 -- Guidelines for Reliability Measures](https://psycnet.apa.org/record/1995-22020-001) -- foundational reliability thresholds
- [Hallgren 2012 -- Inter-Rater Reliability Tutorial](https://pmc.ncbi.nlm.nih.gov/articles/PMC3402032/)
- [ICMJE Authorship Criteria](https://www.icmje.org/recommendations/) -- for deciding when raters qualify as authors

---

## 10. Change Log

- **2026-04-10 v1.0:** Initial version with compensation (1,000 ILS honorarium) and "3 years post-specialization" as minimum
- **2026-04-10 v2.0:** **Revised per Elad's direction.** Compensation removed (voluntary collaboration only). "3 years post-specialization" threshold removed (not supported by any specific source -- it was a reasonable synthesis, not a verified requirement). Focus shifted from credentials to actually-relevant factors: Hebrew fluency, depression experience, therapy-process understanding. Added explicit "honest note on sources" at the top acknowledging the limits of what the literature mandates.
