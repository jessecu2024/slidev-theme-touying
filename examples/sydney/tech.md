---
theme: ../../
routerMode: hash
title: Technology Template — Relay Workflow Automation
author: Illustrative Product Team
date: August 2026
transition: fade
layout: cover-image
image: /assets/sydney/shared/laboratory.jpg
imageAlt: Researcher working in a modern laboratory
imagePosition: 64% center
subtitle: A quieter way to automate high-stakes operational work

touying:
  preset: sydney
  footer: Technology template · Illustrative
  sectionFooter: false
---

# Relay turns a manual hand-off into a dependable workflow

<!-- [Sources] Photo: Nathan Rimoux / Unsplash. See public/assets/sydney/ATTRIBUTION.md. Product and results are fictional. -->

---
layout: big-number
value: 14 → 3
label: minutes per request, from intake to a ready decision
accent: ochre
---

Today, analysts copy information across four tools before the actual work can begin.

<div class="syd-data-note">Illustrative workflow benchmark, shown in minutes</div>

---
layout: split
title: Relay assembles the context before a person makes the decision
ratio: 40/60
---

<Eyebrow>Product</Eyebrow>

## Automate the preparation, preserve human judgment

Relay captures a request, validates required evidence, and routes one decision-ready record.

<div class="syd-data-note"><strong class="text-ochre">Design principle ·</strong> Explain every automated step; keep the final decision human.</div>

::right::

<div class="syd-screen syd-screen-compact">
  <div class="syd-screen-bar"><i></i><i></i><i></i></div>
  <div class="syd-screen-body">
    <div class="syd-screen-nav"><strong>Relay</strong><span>Inbox</span><span>Workflows</span><span>Evidence</span><span>Settings</span></div>
    <div class="syd-screen-main"><h3>Request ready for review</h3><div class="syd-screen-metric">94%</div><div class="syd-screen-lines"><i></i><i></i><i></i></div></div>
  </div>
</div>

---
eyebrow: User journey
---

# One calm path replaces repeated searching and re-entry

<div class="syd-process">
  <div><span>01</span><strong>Capture</strong><p>Request arrives through a structured intake.</p></div>
  <div><span>02</span><strong>Verify</strong><p>Relay checks required fields and evidence.</p></div>
  <div><span>03</span><strong>Prepare</strong><p>Context is assembled into one review record.</p></div>
  <div><span>04</span><strong>Decide</strong><p>A person reviews, resolves, and records rationale.</p></div>
</div>

---
eyebrow: Architecture
---

# The workflow is modular at the edges and opinionated at the decision point

<div class="syd-issue-tree">
  <div class="syd-issue-root">Policy-aware orchestration layer</div>
  <div class="syd-issue-branches">
    <div><strong>Inputs</strong><span>Forms · email · APIs · documents</span></div>
    <div><strong>Decision record</strong><span>Evidence · checks · recommendation · audit trail</span></div>
    <div><strong>Outputs</strong><span>Case systems · notifications · analytics</span></div>
  </div>
</div>

<Caption>Illustrative logical architecture; connectors represent data flow rather than deployment topology.</Caption>

---
eyebrow: Feature overview
---

# Three capabilities make automation trustworthy enough for daily use

<div class="syd-insights">
  <div><strong>Explainable checks</strong><p>Every validation shows the rule, evidence, and outcome.</p></div>
  <div><strong>Human control</strong><p>Users can override a recommendation with recorded rationale.</p></div>
  <div><strong>Operational learning</strong><p>Exceptions become visible patterns, not hidden manual work.</p></div>
</div>

---
eyebrow: Product view
---

# Decision readiness is visible before the case enters the queue

<div class="syd-screen syd-screen-compact">
  <div class="syd-screen-bar"><i></i><i></i><i></i></div>
  <div class="syd-screen-body">
    <div class="syd-screen-nav"><strong>Relay</strong><span>Overview</span><span style="color: var(--color-primary); font-weight: 700;">Evidence</span><span>History</span><span>Decision</span></div>
    <div class="syd-screen-main"><h3>Evidence completeness</h3><div class="syd-screen-metric">8 / 9</div><div class="syd-screen-lines"><i></i><i></i><i></i></div><div class="syd-data-note"><strong class="text-blue">Next check ·</strong> Confirm the supplier declaration before review.</div></div>
  </div>
</div>

<div class="syd-data-note">Illustrative product interface</div>

---
eyebrow: Adoption
---

# Weekly active use accelerates after teams see the first time saving

<SydneyLineChart
  :labels="['W1', 'W2', 'W3', 'W4', 'W5', 'W6']"
  :series="[
    { name: 'Active teams', values: [3, 5, 8, 12, 17, 21], accent: 'ochre' },
    { name: 'Enabled teams', values: [8, 10, 13, 17, 22, 24], accent: 'blue' }
  ]"
  :min="0"
  :max="25"
/>

<div class="syd-data-note">Illustrative six-week pilot adoption</div>

---
eyebrow: Technical insight
---

# Policy is versioned as data, not buried in workflow code

<div class="syd-code-insight">

```ts
const decision = evaluate({
  policy: 'supplier-risk@2026-08',
  evidence,
})

await recordDecision({ decision, rationale })
```

<div class="syd-code-insight-copy"><strong>Every decision remains reproducible.</strong><p>The record binds policy version, evidence, actor, and any human override.</p></div>
</div>

---
layout: comparison
title: Relay reduces manual coordination without creating a black box
leftLabel: Scripted automation
rightLabel: Relay workflow
---

## Fast until conditions change

- Logic distributed across integrations
- Exceptions fall back to email
- Limited decision provenance
- Hard to review policy changes

::right::

## Designed for governed change

- Policy versioned explicitly
- Exceptions visible in one queue
- Evidence linked to every outcome
- Human override recorded by design

---
eyebrow: Roadmap
---

# The roadmap prioritises trust before breadth

<div class="syd-roadmap">
  <div><span>Now</span><strong>Prove</strong><ul><li>One workflow</li><li>Two teams</li></ul></div>
  <div><span>Next</span><strong>Harden</strong><ul><li>Access controls</li><li>Failure recovery</li></ul></div>
  <div><span>Later</span><strong>Extend</strong><ul><li>Workflow builder</li><li>New evidence types</li></ul></div>
  <div><span>Then</span><strong>Scale</strong><ul><li>Reusable policies</li><li>Portfolio analytics</li></ul></div>
</div>

---
eyebrow: Risks and challenges
---

# Trust will fail if the product is accurate but operationally opaque

| Risk | Product response | Proof point |
| --- | --- | --- |
| Incorrect source evidence | Preserve source and confidence | Reviewer can inspect origin |
| Policy changes silently | Version and diff every rule set | Decision shows active version |
| Automation stalls | Explicit retry and human queue | No request disappears |
| Adoption becomes mandatory | Start with opt-in pilot teams | Usage grows through value |

<div class="syd-data-note">Illustrative product risk framework</div>

---
eyebrow: Next steps
---

# Three decisions unlock the next 12 weeks

<div class="syd-rule-list">
  <div><span>01</span><strong>Select the first governed workflow</strong><small>Product + Operations</small></div>
  <div><span>02</span><strong>Nominate two pilot teams</strong><small>Business sponsor</small></div>
  <div><span>03</span><strong>Approve the evidence and audit standard</strong><small>Risk + Technology</small></div>
</div>

---
layout: focus
accent: charcoal
align: left
---

# Automate the preparation. Keep the decision human.

Relay is ready for a focused pilot with one workflow, two teams, and one measurable promise: reduce preparation time without weakening control.
