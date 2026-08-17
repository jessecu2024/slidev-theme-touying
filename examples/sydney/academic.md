---
theme: ../../
routerMode: hash
title: Academic Template — Retrieval Practice in Introductory Statistics
author: Illustrative Learning Sciences Group
date: August 2026
transition: fade
layout: cover
align: left
image: /assets/sydney/shared/campus-tower.jpg
imageAlt: Historic sandstone university building and clock tower
imagePosition: center 42%
subtitle: An illustrative field study of low-stakes retrieval and durable learning

touying:
  preset: sydney
  footer: Academic template · Illustrative study
  sectionFooter: false
---

# Does spaced retrieval improve first-year statistics learning?

<!-- [Sources] Photo: Jeremy Huang / Unsplash. See public/assets/sydney/ATTRIBUTION.md. Study design and results are illustrative. -->

---
layout: focus
accent: light
---

# Research question

Does adding brief, spaced retrieval prompts to weekly tutorials improve delayed conceptual performance relative to guided review?

---
eyebrow: Background
---

# Immediate fluency can conceal fragile understanding

Students may perform well during guided practice yet struggle to retrieve the same concepts after a delay.

<div class="syd-evidence">
  <div class="syd-evidence-claim">The instructional challenge is not exposure alone; it is making knowledge accessible when support is removed.</div>
  <div class="syd-evidence-copy">
    <div class="syd-rule-list">
      <div><span>01</span><strong>Worked examples</strong><small>High support</small></div>
      <div><span>02</span><strong>Independent retrieval</strong><small>Effortful access</small></div>
      <div><span>03</span><strong>Delayed application</strong><small>Durable use</small></div>
    </div>
  </div>
</div>

---
eyebrow: Literature and context
---

# Prior evidence supports practice testing, but implementation conditions matter

<div class="syd-insights">
  <div><strong>Broad utility</strong><p>Practice testing has been rated a high-utility learning technique across varied contexts.</p></div>
  <div><strong>Positive synthesis</strong><p>A meta-analysis found practice tests outperform restudy and other non-testing conditions.</p></div>
  <div><strong>Open implementation question</strong><p>Course context, feedback, timing, and dosage may shape the realised effect.</p></div>
</div>

<Caption>Dunlosky et al. (2013), doi:10.1177/1529100612453266 · Adesope et al. (2017), doi:10.3102/0034654316689306</Caption>

<!-- [Sources] https://journals.sagepub.com/doi/10.1177/1529100612453266 ; https://journals.sagepub.com/doi/10.3102/0034654316689306 -->

---
eyebrow: Methodology
---

# A tutorial-level field experiment balances credibility and feasibility

<div class="syd-process">
  <div><span>01</span><strong>Assign</strong><p>Randomise 12 tutorial groups within teaching weeks.</p></div>
  <div><span>02</span><strong>Deliver</strong><p>Use retrieval prompts or time-matched guided review.</p></div>
  <div><span>03</span><strong>Measure</strong><p>Assess immediate and three-week delayed performance.</p></div>
  <div><span>04</span><strong>Estimate</strong><p>Model outcomes with tutorial-clustered uncertainty.</p></div>
</div>

<div class="syd-data-note">Illustrative pre-registered design</div>

---
eyebrow: Conceptual framework
---

# Retrieval should strengthen access to later application

<div class="syd-issue-tree">
  <div class="syd-issue-root">Spaced, effortful retrieval with feedback</div>
  <div class="syd-issue-branches">
    <div><strong>Accessible knowledge</strong><span>Concepts are easier to retrieve after a delay</span></div>
    <div><strong>Calibrated confidence</strong><span>Feedback exposes gaps before summative assessment</span></div>
    <div><strong>Transfer opportunity</strong><span>Retrieved concepts can be applied to unfamiliar problems</span></div>
  </div>
</div>

<div class="syd-data-note">Illustrative mechanism; the proposed links do not establish causality.</div>

---
eyebrow: Data and sample
---

# The illustrative sample is balanced at baseline

<div class="syd-sample-grid">
  <div class="syd-sample-row syd-sample-head"><strong>Measure</strong><strong>Retrieval</strong><strong>Guided review</strong><strong>Std. difference</strong></div>
  <div class="syd-sample-row"><span>Students</span><span>148</span><span>151</span><span>—</span></div>
  <div class="syd-sample-row"><span>Prior quantitative score</span><span>72.1</span><span>71.6</span><span>0.03</span></div>
  <div class="syd-sample-row"><span>Weekly attendance</span><span>83%</span><span>82%</span><span>0.02</span></div>
  <div class="syd-sample-row"><span>Baseline concept score</span><span>54.8</span><span>55.2</span><span>−0.02</span></div>
</div>

<div class="syd-data-note"><strong>Unit of assignment ·</strong> Tutorial group; illustrative analysis accounts for clustering.</div>

---
eyebrow: Result 1 · Primary outcome
---

# The retrieval group performs eight points higher after three weeks

<SydneyBarChart
  :items="[
    { label: 'Guided review', value: 64, display: '64%', accent: 'charcoal' },
    { label: 'Retrieval', value: 72, display: '72%', accent: 'ochre' }
  ]"
  :max="80"
/>

<Callout label="Estimated difference">+8.1 percentage points; illustrative 95% CI [3.2, 13.0].</Callout>

<div class="syd-data-note">Illustrative delayed conceptual assessment</div>

---
eyebrow: Result 2 · Durability
---

# The initial gap widens as support is removed

<SydneyLineChart
  :labels="['Baseline', 'Immediate', 'Week 1', 'Week 3']"
  :series="[
    { name: 'Retrieval', values: [55, 78, 75, 72], accent: 'ochre' },
    { name: 'Guided review', values: [55, 76, 69, 64], accent: 'charcoal' }
  ]"
  :min="50"
  :max="80"
  suffix="%"
/>

<div class="syd-data-note">Illustrative mean conceptual score by assessment point</div>

---
eyebrow: Result 3 · Model estimates
---

# The adjusted effect remains statistically meaningful

<table>
  <thead><tr><th>Outcome</th><th>Estimate</th><th>Clustered SE</th><th>95% CI</th><th>p</th></tr></thead>
  <tbody>
    <tr class="syd-key-row"><td>Delayed concept score</td><td>+8.1 pp</td><td>2.3</td><td>[3.2, 13.0]</td><td>.004</td></tr>
    <tr><td>Immediate score</td><td>+1.9 pp</td><td>1.8</td><td>[−1.9, 5.7]</td><td>.303</td></tr>
    <tr><td>Calibration error</td><td>−6.4 pp</td><td>2.5</td><td>[−11.7, −1.1]</td><td>.022</td></tr>
  </tbody>
</table>

<Caption>Illustrative linear models with baseline covariates and tutorial-clustered standard errors.</Caption>

---
layout: split
title: The pattern is consistent with a durability mechanism
ratio: 50/50
---

<Eyebrow>What the results support</Eyebrow>

## A delayed advantage

The groups are similar immediately after instruction, but diverge when students must retrieve concepts after a delay.

::right::

<Eyebrow color="blue">What remains uncertain</Eyebrow>

## The active ingredient

The design does not isolate spacing, retrieval effort, feedback, or their interaction.

---
eyebrow: Limitations
---

# Four limitations bound the strength and reach of the conclusion

<div class="syd-rule-list">
  <div><span>01</span><strong>Single course context</strong><small>External validity</small></div>
  <div><span>02</span><strong>Tutorial-level assignment</strong><small>Limited clusters</small></div>
  <div><span>03</span><strong>Short follow-up</strong><small>Three weeks</small></div>
  <div><span>04</span><strong>Composite intervention</strong><small>Mechanism unresolved</small></div>
</div>

---
eyebrow: Implications
---

# The practical next step is a measured extension, not immediate scale-up

<div class="syd-insights">
  <div><strong>For teaching</strong><p>Embed brief retrieval with feedback in high-enrolment tutorials.</p></div>
  <div><strong>For evaluation</strong><p>Retain delayed outcomes and report implementation fidelity.</p></div>
  <div><strong>For research</strong><p>Separate spacing, feedback, and retrieval effort in the next design.</p></div>
</div>

---
layout: focus
accent: charcoal
align: left
---

# Conclusion

In this illustrative study, spaced retrieval improves delayed conceptual performance while leaving immediate scores broadly similar.

The finding supports a larger, multi-course replication focused on durability and mechanism.

---
layout: image-overlay
image: /assets/sydney/shared/campus-courtyard.jpg
imageAlt: Historic sandstone campus courtyard
imagePosition: center 56%
align: center
---

# Questions and discussion

Study materials, analysis plan, and data shown here are illustrative placeholders.

<!-- [Sources] Photo: Jeremy Huang / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->
