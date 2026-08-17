# slidev-theme-touying

A [Slidev](https://sli.dev/) theme inspired by [typst-touying](https://github.com/touying-typ/touying). It includes three restrained Touying ports and the editorial `sydney` preset.

## Presets

| Preset | Character | Demo |
|---|---|---|
| `dewdrop` | Serif, dark green, progressive navigation | [dewdrop.md](./examples/dewdrop.md) ([Preview](https://kermanx.com/slidev-theme-touying/dewdrop/)) |
| `university` | Formal header, progress bar, tri-color footer | [university.md](./examples/university.md) ([Preview](https://kermanx.com/slidev-theme-touying/university/)) |
| `simple` | Minimal section header and page footer | [simple.md](./examples/simple.md) ([Preview](https://kermanx.com/slidev-theme-touying/simple/)) |
| `sydney` | Apple-inspired type, Sydney Ochre, editorial imagery | [sydney.md](./examples/sydney.md) |

## Installation

```bash
npm i slidev-theme-touying
```

Set the theme and preset in the root frontmatter:

```yaml
---
theme: touying

touying:
  preset: sydney
  footer: 'Author · Presentation'
---
```

## Sydney preset

Sydney preserves the restraint of Touying Simple while adding a more complete professional presentation system. It is designed for academic talks, interviews, research communication, technology presentations, and consulting-style recommendations.

The system favors typography, alignment, whitespace, and photography over cards, decoration, gradients, or heavy shadows.

### Typography

Sydney uses a system sans stack and does not bundle Apple fonts:

```css
-apple-system,
BlinkMacSystemFont,
"SF Pro Display",
"SF Pro Text",
"Helvetica Neue",
Inter,
Arial,
sans-serif
```

Code uses `SFMono-Regular`, `SF Mono`, and common system monospace fallbacks. Large headings use tighter tracking and line height; body text remains left-aligned and comfortable for 16:9 presentation viewing.

### Semantic color system

| Role | Token | Value | Use |
|---|---|---:|---|
| Primary | `--color-primary` | `#E64626` | Conclusions and primary emphasis |
| Charcoal | `--color-charcoal` | `#424242` | Structure and occasional dark slides |
| Information | `--color-blue` | `#007AFF` | Evidence, methods, and secondary data |
| Risk | `--color-red` | `#D92D20` | Risk, decline, warnings, and negative values |
| Default surface | `--surface-default` | `#FAF9F7` | Warm slide background |
| White surface | `--surface-white` | `#FFFFFF` | Controlled contrast |
| Dark surface | `--surface-dark` | `#343434` | Section, focus, and closing punctuation |

Soft highlight tokens are also available: `--ochre-soft`, `--blue-soft`, `--red-soft`, and `--charcoal-soft`.

### Layout reference

All normal layouts remain simple to use. Common image settings are `image`, `imageAlt`, `imageFit`, `imagePosition`, and `imageCaption`.

| Layout | Purpose | Main frontmatter |
|---|---|---|
| `cover` | Minimal centered or left-aligned cover; optionally adds a contained image | `subtitle`, `author`, `date`, `align`, `image` |
| `cover-image` | Premium 45/55 text and full-height image cover | `image`, `subtitle`, `author`, `date` |
| `default` | Standard content with a controlled reading width | `eyebrow`, `background`, `footer` |
| `section` | Light or dark section divider | `variant: light \| dark`, `sectionNumber`, `eyebrow` |
| `focus` | One major conclusion | `accent: ochre \| charcoal \| blue \| light`, `align` |
| `image-right` | Text left, dominant image right | common image settings |
| `image-left` | Image first, tuned text column on the right | common image settings |
| `image-full` | Full-bleed image with optional title or caption | common image settings, `overlay` |
| `image-overlay` | Full-bleed photograph with controlled text contrast | common image settings, `align: left \| center \| bottom-left` |
| `image-grid` | Editorial two-, three-, or four-image composition | `images` array |
| `quote-image` | Portrait/photo with editorial quote | `image`, `author`, `role`, `accent` |
| `metric-image` | Large metric with a supporting photograph | `value`, `label`, `note`, `accent`, `image` |
| `big-number` | One large number and a short takeaway | `value`, `label`, `accent` |
| `split` | Flexible two-column composition | `title`, `ratio` |
| `comparison` | Flat A/B comparison with one divider | `title`, `leftLabel`, `rightLabel` |

#### Image layout

```md
---
layout: image-right
image: /images/research.jpg
imageAlt: Researcher examining a sample
imagePosition: 62% center
imageCaption: Evidence becomes more memorable when the work is visible.
---

# Show the work

Explain the implication beside it.
```

#### Image grid

```yaml
---
layout: image-grid
images:
  - src: /images/hero.jpg
    alt: Main campus view
    caption: Place
  - src: /images/lab.jpg
    alt: Research in progress
    caption: Practice
  - src: /images/team.jpg
    alt: Students collaborating
    caption: Community
---
```

For three images, the first image is the hero and the remaining images stack beside it. The four-image layout uses one large image, two smaller images, and one wide supporting image.

#### Split and comparison

`split` supports `50/50`, `40/60`, `60/40`, `35/65`, and `65/35` ratios. Use Slidev's named-slot syntax for the right side:

```md
---
layout: split
title: Evidence and implication
ratio: 40/60
---

The framing argument.

::right::

The larger evidence area.
```

`comparison` uses the same `::right::` slot and adds a single subtle divider instead of two bulky cards.

### Component reference

Components are exposed from the theme's root `components/` directory, so they can be used directly in Slidev Markdown.

| Component | API | Purpose |
|---|---|---|
| `Highlight` | `color="ochre \| blue \| red \| gray"` | Inline editorial background highlight |
| `Callout` | `type="insight \| info \| warning \| risk \| neutral"`, `label` | Semantic interpretation with a left rule |
| `Metric` | `value`, `label`, `note`, `accent`, `align` | Dominant number for executive storytelling |
| `Quote` | `author`, `role`, `accent` | Editorial quotation and attribution |
| `ImageFrame` | `src`, `alt`, `fit`, `position`, `caption`, `radius` | Contained image with predictable cropping |
| `Caption` | `align` | Muted source or explanatory line |
| `Eyebrow` | `color` | Small kicker above a title |

```vue
<Callout type="insight">
  The finding matters because it changes the decision.
</Callout>

<Metric
  value="73%"
  label="of respondents"
  note="+12pp YoY"
  accent="ochre"
/>

<Quote author="Name" role="Position">
  Great presentations communicate one idea at a time.
</Quote>
```

### Emphasis utilities

Bold Markdown remains typographic weight. Color is always intentional.

```html
<span class="text-ochre">Primary conclusion</span>
<span class="text-blue">Supporting evidence</span>
<span class="text-red">Material risk</span>
<span class="text-charcoal">Structural label</span>
<span class="text-muted">Secondary context</span>

<span class="hl-ochre">Primary highlight</span>
<span class="hl-blue">Evidence highlight</span>
<span class="hl-red">Risk highlight</span>
<span class="hl-gray">Neutral highlight</span>
```

### Tables and charts

Tables use strong headers, subtle row rules, and no full grid by default. Semantic cell classes are:

- `cell-primary`
- `cell-info`
- `cell-negative`

The recommended chart palette is deliberately small:

| Series | Token |
|---|---|
| Primary | `--chart-1` |
| Secondary | `--chart-2` |
| Negative/risk | `--chart-negative` |
| Neutral | `--chart-neutral-1`, `--chart-neutral-2`, `--chart-neutral-3` |
| Derived tints | `--chart-tint-ochre`, `--chart-tint-blue` |

### Backgrounds and footer

Supported background classes are `bg-warm`, `bg-white`, `bg-soft-ochre`, `bg-soft-blue`, and `bg-charcoal`.

Sydney's footer contains optional left text, optional section title, and the slide count. Cover, section, focus, full-image, and overlay slides hide it automatically.

```yaml
touying:
  preset: sydney
  footer: 'Author · Conference'
  sectionFooter: true
```

Set `footer: false` on any slide to hide the footer. The `sectionFooter` option is off by default.

## Common configuration

All options go under `touying:` in the root frontmatter.

| Option | Type | Default | Description |
|---|---|---|---|
| `preset` | `'dewdrop' \| 'university' \| 'simple' \| 'sydney'` | `'dewdrop'` | Active preset |
| `footer` | `string` | `''` | Left footer text where supported |
| `footerRight` | `string` | `''` | Dewdrop right footer override |
| `sectionFooter` | `boolean` | `false` | Show the active section in Sydney's footer |

### Dewdrop-specific

```yaml
touying:
  preset: dewdrop
  navigation: mini-slides   # sidebar | mini-slides | none
  footer: My Presentation
  footerRight: ''
  outlineRowsPerCol: 12
  alpha: 0.3
  miniSlides:
    height: '2em'
    linebreaks: auto        # true | false | auto
    subsection: true
  sidebar:
    width: '10em'
```

### University-specific

```yaml
touying:
  preset: university
logo: /logo.svg
```

### Simple-specific

```yaml
touying:
  preset: simple
  footer: 'Author · Conference'
```

## Development and visual QA

```bash
pnpm install
pnpm run build
pnpm run build:sydney
pnpm run dev:sydney
```

The Sydney showcase contains 26 slides and demonstrates every Sydney layout, component, table treatment, chart color, dark slide, image composition, and code treatment. Its photographs are stored locally under `examples/public/images`; attribution is included in each relevant slide's notes.

## License

[MIT](./LICENSE) — original copyright and attribution are preserved.
