---
theme: ../
routerMode: hash
authors: Alpha and Bravo and Charlie
date: July 23
transition: slide-left

touying:
  preset: simple-serif
---

# Keep it simple — Serif

---
layout: section
---

# Overview

---

# Origin

The **Simple Serif** preset pairs the same restrained layout system with a traditional serif typeface for editorial, academic, and formal presentations.

It keeps the repeated contents pages, compact chapter progress bar, semantic highlights, and focused single-color visual system.

---
layout: section
---

# Configuration

---

# Configuration

```yaml
touying:
  preset: simple-serif

themeConfig:
  primary: '#105ca4' # Overrides the default primary color
```

---

# Layouts

| Layout | Description |
|--------|-------------|
| `cover` | Centered title, subtitle, author, date |
| `default` | Content slide · page counter · chapter bar |
| `section` | Repeated contents overview with current chapter |
| `focus` | Full-screen primary-color accent |

Built-in layouts such as `two-cols` also work seamlessly with the theme.

---
layout: section
---

# Typography

---

# Typography

## Level 2 Heading

Body text uses Georgia with serif fallbacks. **Bold** is rendered in the primary color. *Italic*, `inline code`, and ~~strikethrough~~ are all supported.

> Blockquotes use a neutral background and the same primary-blue accent.

---

# Emphasis Styles

Use <TextHighlight color="red">red for risks or critical exceptions</TextHighlight> and <TextHighlight color="green">green for validated gains or positive outcomes</TextHighlight> inside a paragraph.

<EmphasisBox>
Key takeaway: the serif edition keeps the same rounded blue emphasis box and white text.
</EmphasisBox>

---

# Lists & Links

- Square bullets by default
- Nested items are supported
  - Second level

1. First item
2. Second item
3. Third item

[Links are colored](https://github.com/touying-typ/touying) and underlined.

---
layout: section
---

# Code & Data

---

# Code Blocks

```python
from dataclasses import dataclass

@dataclass
class Slide:
    title: str
    layout: str = "default"
```

```ts
const sum = (a: number, b: number): number => a + b
```

---

# Tables

| Name | Type | Default | Description |
|------|------|---------|-------------|
| `--slidev-theme-primary` | color | `#105ca4` | Accent color |
| `chapterProgress` | boolean | `true` | Show the chapter bar on content slides |

---
layout: section
---

# Motion & Focus

---

# Animations

- Always visible

<v-click>

- Appears on first click

</v-click>

<v-click>

- Appears on second click <span v-mark.underline.orange>highlighted</span>

</v-click>

---
layout: focus
---

_Focus!_

This is very important.
