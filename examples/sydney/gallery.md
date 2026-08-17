---
theme: ../../
routerMode: hash
title: Sydney Template Gallery
author: Slidev Theme Touying
date: August 2026
transition: fade
layout: cover
align: left
subtitle: Copy-ready compositions for interviews, strategy, research, and technology

touying:
  preset: sydney
  footer: Sydney template gallery · Illustrative
  sectionFooter: false
---

# Sydney template gallery

<div class="syd-lede">Thirty-two reusable compositions. One calm, recognisable design system.</div>

<!-- All organisations, metrics, quotations, and results are illustrative. -->

---
layout: cover
align: left
subtitle: Pure typography for a direct, confident opening
author: Your name or team
date: Month 2026
---

<div class="syd-gallery-index">Cover · Pure typography</div>

# Make the central idea the first visual.

---
layout: cover-image
image: /assets/sydney/shared/campus-modern.jpg
imageAlt: Modern university building under a clear sky
imagePosition: 58% center
subtitle: A split cover balances a concise proposition with a strong sense of place
author: Strategy and Research Office
date: August 2026
---

<div class="syd-gallery-index">Cover · Split image</div>

# Heritage gives the idea gravity. Modernity gives it momentum.

<!-- [Sources] Photo: Jeremy Huang / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: image-overlay
image: /assets/sydney/shared/harbour.jpg
imageAlt: Aerial view of Sydney Harbour
imagePosition: center
align: bottom-left
---

<div class="syd-gallery-index">Cover · Full image</div>

# A place worth designing for

Annual city futures briefing · August 2026

<!-- [Sources] Photo: Toni Pomar / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: focus
accent: charcoal
align: left
---

<div class="syd-gallery-index">Cover · Dark</div>

# Quiet confidence carries further than visual noise.

A restrained opening for technology, strategy, or a decisive recommendation.

---
layout: cover
align: left
image: /assets/sydney/shared/campus-tower.jpg
imageAlt: Historic sandstone university building
imagePosition: center 40%
subtitle: Faculty of Example Studies · Seminar series
author: Dr Alex Morgan
date: 17 August 2026
---

<div class="syd-gallery-index">Cover · University</div>

# Research question stated plainly

<!-- [Sources] Photo: Jeremy Huang / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
eyebrow: Contents
---

<div class="syd-gallery-index">Agenda · Numbered</div>

# Four questions guide the conversation

<div class="syd-rule-list">
  <div><span>01</span><strong>What changed?</strong><small>Context</small></div>
  <div><span>02</span><strong>What did we learn?</strong><small>Evidence</small></div>
  <div><span>03</span><strong>What should we do?</strong><small>Decision</small></div>
  <div><span>04</span><strong>How will we deliver?</strong><small>Action</small></div>
</div>

---
eyebrow: Contents
---

<div class="syd-gallery-index">Agenda · Three part</div>

# A simple arc keeps the audience oriented

<div class="syd-agenda">
  <div><span>01</span><strong>Understand</strong><p>Frame the context and the question that matters.</p></div>
  <div><span>02</span><strong>Decide</strong><p>Interpret the evidence and select a direction.</p></div>
  <div><span>03</span><strong>Act</strong><p>Translate the choice into owned next steps.</p></div>
</div>

---
eyebrow: Contents
---

<div class="syd-gallery-index">Agenda · Timeline</div>

# The story unfolds across four moments

<div class="syd-timeline">
  <div><span>Now</span><strong>Baseline</strong><p>Establish the current experience.</p></div>
  <div><span>Next</span><strong>Insight</strong><p>Show what the evidence changes.</p></div>
  <div><span>Then</span><strong>Choice</strong><p>Make the trade-off explicit.</p></div>
  <div><span>Finally</span><strong>Action</strong><p>Leave with one owned move.</p></div>
</div>

---
layout: focus
accent: ochre
---

<div class="syd-gallery-index">Insight · One big idea</div>

# Retention is the growth strategy hiding in plain sight.

Use a focus slide only after the evidence has earned the conclusion.

---
eyebrow: Insight
---

<div class="syd-gallery-index">Insight · Title and explanation</div>

# A message title should remove the need to guess the point

The supporting sentence clarifies scope or consequence. It does not repeat the title, introduce a second argument, or become a paragraph.

---
eyebrow: Insight
---

<div class="syd-gallery-index">Insight · Three findings</div>

# Three findings can form one coherent answer

<div class="syd-insights">
  <div><strong>Demand is present</strong><p>The market is expanding at a stable, attractive rate.</p></div>
  <div><strong>Value leaks early</strong><p>Most avoidable churn occurs before a habit forms.</p></div>
  <div><strong>One behaviour predicts success</strong><p>Shared workflow completion is the clearest signal.</p></div>
</div>

<div class="syd-data-note">Illustrative findings</div>

---
eyebrow: Insight
---

<div class="syd-gallery-index">Insight · Takeaway and evidence</div>

# The conclusion should remain visually distinct from its proof

<div class="syd-evidence">
  <div class="syd-evidence-claim">Most projected upside comes from keeping customers active through day 90.</div>
  <div class="syd-evidence-copy">Cohort analysis, service interviews, and unit economics all point to the same early activation gap. Use Ochre for the conclusion and Charcoal or Blue for the supporting evidence.</div>
</div>

<div class="syd-data-note">Illustrative evidence pattern</div>

---
layout: split
title: A symptom becomes useful only when its implication is explicit
ratio: 50/50
---

<div class="syd-gallery-index">Insight · Problem and implication</div>

<Eyebrow>Problem</Eyebrow>

## Response time is rising

Requests cross three queues and ownership changes twice before work begins.

::right::

<Eyebrow color="blue">Implication</Eyebrow>

## Redesign the hand-off first

Adding capacity will mask the coordination failure without resolving it.

---
eyebrow: Decision framing
---

<div class="syd-gallery-index">Insight · Question and answer</div>

# Put the question and the answer in the same visual field

<div class="syd-qa">
  <div><span>Question</span><strong>Where should the next investment create proof fastest?</strong></div>
  <div><span>Answer</span><strong>Fund a focused activation pilot before increasing acquisition spend.</strong><p>The answer is specific enough to approve, reject, or refine.</p></div>
</div>

---
eyebrow: Data · Line chart
---

<div class="syd-gallery-index">Data · Chart and takeaway</div>

# The gap emerges after the initial experience

<SydneyLineChart
  :labels="['Week 0', 'Week 2', 'Week 4', 'Week 8']"
  :series="[
    { name: 'Priority cohort', values: [54, 67, 73, 79], accent: 'ochre' },
    { name: 'Baseline', values: [54, 61, 63, 64], accent: 'charcoal' }
  ]"
  :min="50"
  :max="80"
  suffix="%"
/>

<div class="syd-data-note">Illustrative cohort index</div>

---
layout: split
title: One segment accounts for most of the addressable opportunity
ratio: 65/35
---

<div class="syd-gallery-index">Data · Chart with commentary</div>

<SydneyBarChart
  :items="[
    { label: 'Core', value: 62, display: '62%', accent: 'ochre' },
    { label: 'Growth', value: 23, display: '23%', accent: 'blue' },
    { label: 'Emerging', value: 10, display: '10%', accent: 'charcoal' },
    { label: 'Other', value: 5, display: '5%', accent: 'gray' }
  ]"
  :max="70"
/>

::right::

<Callout label="So what">Prioritise the core segment first; it offers the strongest combination of value and evidence.</Callout>

<div class="syd-data-note">Illustrative share of upside</div>

---
eyebrow: Data · Two-chart comparison
---

<div class="syd-gallery-index">Data · Two charts</div>

# Volume grows in both segments, but quality diverges

<div class="syd-two-chart">
  <div><h3>New accounts</h3><SydneyBarChart compact :items="[{ label: '2025', value: 74, display: '740', accent: 'charcoal' }, { label: '2026', value: 92, display: '920', accent: 'blue' }]" :max="100" /></div>
  <div><h3>90-day retained accounts</h3><SydneyBarChart compact :items="[{ label: '2025', value: 58, display: '580', accent: 'charcoal' }, { label: '2026', value: 55, display: '550', accent: 'red' }]" :max="100" /></div>
</div>

<div class="syd-data-note">Illustrative account counts</div>

---
layout: split
title: A big number earns attention; the chart explains its shape
ratio: 35/65
---

<div class="syd-gallery-index">Data · Big number and chart</div>

<Metric value="28%" label="faster response time" note="Illustrative pilot result" />

::right::

<SydneyLineChart :labels="['W1', 'W2', 'W3', 'W4']" :series="[{ name: 'Median minutes', values: [19, 17, 15, 14], accent: 'ochre' }]" :min="12" :max="20" />

---
eyebrow: Data · KPI row
---

<div class="syd-gallery-index">Data · KPI row</div>

# Four metrics create a balanced view of progress

<div class="syd-kpis">
  <div><strong>72%</strong><span>activation</span></div>
  <div><strong>4.6</strong><span>customer effort score</span></div>
  <div><strong>−18%</strong><span>handling time</span></div>
  <div><strong>94%</strong><span>evidence completeness</span></div>
</div>

<div class="syd-data-note">Illustrative operating metrics</div>

---
eyebrow: Data · Clean table
---

<div class="syd-gallery-index">Data · Analytical table</div>

# A light table keeps attention on the numbers

| Scenario | Revenue | Cost | Contribution | Margin |
| --- | ---: | ---: | ---: | ---: |
| Base | $18.4m | $12.7m | $5.7m | 31% |
| Retention-led | $20.1m | $13.2m | $6.9m | 34% |
| Acquisition-led | $20.6m | $14.8m | $5.8m | 28% |

<div class="syd-data-note">Illustrative financial analysis</div>

---
eyebrow: Data · Highlighted table
---

<div class="syd-gallery-index">Data · Highlighted row</div>

# Highlight the decision row, not every interesting cell

<table>
  <thead><tr><th>Option</th><th>Impact</th><th>Confidence</th><th>Time to proof</th></tr></thead>
  <tbody>
    <tr><td>Increase acquisition</td><td>Medium</td><td>Medium</td><td>6 months</td></tr>
    <tr class="syd-key-row"><td>Redesign activation</td><td>High</td><td>High</td><td>12 weeks</td></tr>
    <tr><td>Expand service capacity</td><td>Low</td><td>Medium</td><td>4 months</td></tr>
  </tbody>
</table>

<div class="syd-data-note">Illustrative option assessment</div>

---
layout: comparison
title: A before-and-after comparison should expose the operating change
leftLabel: Before
rightLabel: After
---

<div class="syd-gallery-index">Comparison · Before and after</div>

## Work is located

- Three intake channels
- Ownership changes twice
- Escalation after delay
- Reporting built manually

::right::

## Work is prepared

- One structured intake
- Owner visible at entry
- Triggered early support
- Evidence captured automatically

---
layout: image-right
image: /assets/sydney/shared/scientist.jpg
imageAlt: Scientist examining a sample through a microscope
imagePosition: 58% center
imageCaption: Use the crop to preserve the subject's attention
---

<div class="syd-gallery-index">Image · Right</div>

# Let the image show the work; let the text explain why it matters

Keep the copy narrow and resist filling every available line.

<!-- [Sources] Photo: Navy Medicine / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: image-left
image: /assets/sydney/shared/students.jpg
imageAlt: Students collaborating around a laptop
imagePosition: center 45%
imageCaption: Human context can precede the explanation
---

<div class="syd-gallery-index">Image · Left</div>

# Collaboration is the subject, not a decoration

Use an image-left composition when the human context should be encountered first.

<!-- [Sources] Photo: Vitaly Gariev / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: image-full
image: /assets/sydney/shared/campus-arches.jpg
imageAlt: Historic sandstone arches and green lawn
imagePosition: center 46%
imageCaption: Jeremy Huang · Unsplash
overlay: true
---

<div class="syd-gallery-index">Image · Editorial full bleed</div>

# Give a strong image enough room to become the argument

<!-- [Sources] Photo: Jeremy Huang / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: quote-image
image: /assets/sydney/shared/researcher.jpg
imageAlt: Researcher looking through a microscope
imagePosition: 46% center
author: Illustrative interview participant
role: Research program lead
accent: ochre
---

<div class="syd-gallery-index">Image · Photo and quote</div>

“The useful moment is when a complex result becomes a decision someone can act on.”

<!-- [Sources] Photo: Chidera Faustina Okeke / Unsplash. See public/assets/sydney/ATTRIBUTION.md. Quotation is illustrative. -->

---
layout: metric-image
value: 3.4×
label: more likely to reach repeat value
note: Illustrative cohort comparison
accent: blue
image: /assets/sydney/shared/library.jpg
imageAlt: People studying in a grand library
imagePosition: center 48%
---

<div class="syd-gallery-index">Image · Photo and metric</div>

The sentence beneath the metric states the implication, not the calculation.

<!-- [Sources] Photo: Sung Jin Cho / Unsplash. See public/assets/sydney/ATTRIBUTION.md. Metric is illustrative. -->

---
layout: image-grid
images:
  - src: /assets/sydney/shared/campus-courtyard.jpg
    alt: Sandstone courtyard and arches
    position: center 52%
    caption: Place
  - src: /assets/sydney/shared/laboratory.jpg
    alt: Researcher working in a laboratory
    position: center 45%
    caption: Practice
  - src: /assets/sydney/shared/study.jpg
    alt: People working at a shared desk
    position: center 42%
    caption: Community
---

<div class="syd-gallery-index">Image · Hero and support</div>

# One hero image, two supporting moments

<!-- [Sources] Photos: Jeremy Huang, Nathan Rimoux, and Raka Rahmadani / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: image-grid
images:
  - src: /assets/sydney/shared/campus-tower.jpg
    alt: Campus clock tower
    position: center 42%
    caption: Institution
  - src: /assets/sydney/shared/campus-steps.jpg
    alt: People on campus steps
    position: center 62%
    caption: Movement
  - src: /assets/sydney/shared/campus-modern.jpg
    alt: Modern university building
    position: center
    caption: Change
  - src: /assets/sydney/shared/harbour.jpg
    alt: Sydney Harbour aerial view
    position: center
    caption: Place
---

<div class="syd-gallery-index">Image · Four-image gallery</div>

# Four images can establish a visual world without becoming a card grid

<!-- [Sources] Photos: Jeremy Huang and Toni Pomar / Unsplash. See public/assets/sydney/ATTRIBUTION.md. -->

---
layout: comparison
title: Compare options against the decision criteria that actually matter
leftLabel: Option A · Extend
rightLabel: Option B · Redesign
---

<div class="syd-gallery-index">Comparison · Options</div>

## Lower disruption

- Builds on the current workflow
- Faster initial mobilisation
- Preserves fragmented ownership
- Medium confidence in impact

::right::

## Stronger operating change

- Creates one end-to-end journey
- Requires focused transition support
- Makes ownership explicit
- High confidence in durable impact

---
eyebrow: Process · Phased implementation
---

<div class="syd-gallery-index">Process · Roadmap</div>

# The roadmap shows what changes—not only when activity occurs

<div class="syd-roadmap">
  <div><span>Phase 1</span><strong>Understand</strong><ul><li>Baseline</li><li>User evidence</li></ul></div>
  <div><span>Phase 2</span><strong>Prototype</strong><ul><li>New journey</li><li>Measures</li></ul></div>
  <div><span>Phase 3</span><strong>Pilot</strong><ul><li>Two cohorts</li><li>Weekly learning</li></ul></div>
  <div><span>Phase 4</span><strong>Scale</strong><ul><li>Decision gate</li><li>Owned rollout</li></ul></div>
</div>

---
layout: focus
accent: charcoal
align: left
---

<div class="syd-gallery-index">Closing · Recommendation and contact</div>

# Close with the decision or conversation the deck was built to enable.

<div class="syd-contact">
  <div><span>Recommendation</span><strong>State the next move</strong></div>
  <div><span>Q&A</span><strong>Invite the useful question</strong></div>
  <div><span>Contact</span><strong>name@example.com</strong></div>
</div>
