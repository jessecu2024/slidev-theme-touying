---
theme: ../
layout: cover
title: Signals in motion
subtitle: A navigated presentation system for technical stories, product reviews, and research updates
author: Product & Research
transition: fade

touying:
  preset: harbour
  navigation: mini-slides
  footer: Harbour · Product review
  outlineRowsPerCol: 10
  miniSlides:
    linebreaks: false
    subsection: true
---

Prepared for clear decisions · 2026

---
layout: outline
depth: 1
---

---
layout: section
depth: 1
---

# Direction

---

## One operating picture keeps the conversation moving

<div class="harbour-three grid grid-cols-3 mt-12">

<div>

### 01 · Signal

Lead with the change the audience needs to understand.

</div>

<div>

### 02 · Meaning

Explain why the evidence changes the current view.

</div>

<div>

### 03 · Move

End with the decision, owner, or next experiment.

</div>

</div>

---

## Evidence should make the priority unmistakable

| Workstream | Current signal | Recommended move |
|---|---|---|
| Discovery | Fragmented inputs | Create one intake path |
| Delivery | Uneven hand-offs | Define one accountable owner |
| Learning | Slow feedback | Review evidence every two weeks |

> The table is illustrative. Harbour uses blue for direction and sea-glass for supporting evidence.

---
layout: section
depth: 1
---

# Evidence

---
layout: two-cols
---

## Technical detail remains readable without taking over the slide

::left::

```ts
type Signal = {
  owner: string
  confidence: number
  nextMove: string
}
```

::right::

### Keep the hierarchy simple

- Show the interface only when it clarifies the decision
- Use short annotations beside the evidence
- Move implementation detail into notes or an appendix

---

## A quotation can slow the pace at the right moment

> A clear signal is useful only when the team agrees what to do next.

**Illustrative workshop principle**

The pale blue field supports commentary without becoming a card-based interface.

---
layout: section
depth: 1
---

# Decision

---
layout: focus
---

Build one shared view of the evidence—then make the next move explicit.
