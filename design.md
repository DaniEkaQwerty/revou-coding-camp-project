# Design system

Visual design token system for this project. This file is the single source of truth for all color, typography, spacing, and component decisions. Read this before writing any HTML, CSS, or Tailwind class.

---

## Aesthetic direction

Minimal. Clean. Quiet confidence. Blue is the only accent — used with restraint, not decoration. White space does the structural work. Nothing appears unless it earns its place.

---

## Color palette

| Token name | Hex | Role |
|---|---|---|
| `--color-bg` | `#ffffff` | Page background |
| `--color-surface` | `#f0f6ff` | Subtle tinted surface (cards, inputs) |
| `--color-border` | `#dde8f5` | Hairline borders, dividers |
| `--color-accent` | `#2563eb` | Primary blue — buttons, links, highlights |
| `--color-accent-hover` | `#1d4ed8` | Accent on hover |
| `--color-accent-light` | `#eff6ff` | Accent tint — badge bg, hover state |
| `--color-text` | `#0f172a` | Primary text (near-black) |
| `--color-text-secondary` | `#475569` | Supporting text, captions |
| `--color-text-muted` | `#94a3b8` | Placeholder, disabled, hints |
| `--color-text-on-accent` | `#ffffff` | Text placed on accent-filled bg |

**Rule:** never introduce a color not listed above. If something feels like it needs a new color, use `--color-text-muted` or `--color-surface` first.

---

## Typography

### Font families

```css
--font-sans: 'Inter', ui-sans-serif, system-ui, sans-serif;
--font-mono: 'JetBrains Mono', 'Fira Code', ui-monospace, monospace;
```

Load Inter from Google Fonts:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

### Type scale

| Token | Size | Weight | Line height | Usage |
|---|---|---|---|---|
| `--text-xs` | 12px | 400 | 1.5 | Captions, labels, meta |
| `--text-sm` | 14px | 400 | 1.6 | Secondary body, UI labels |
| `--text-base` | 16px | 400 | 1.7 | Body text, default |
| `--text-lg` | 18px | 500 | 1.5 | Card titles, subheadings |
| `--text-xl` | 24px | 600 | 1.3 | Section headings (h2) |
| `--text-2xl` | 36px | 600 | 1.15 | Hero heading (h1) |

**Rules:**
- Sentence case everywhere. Never Title Case on common nouns.
- No decorative font changes — Inter only throughout.
- `font-weight: 600` is reserved for headings only. UI labels and buttons use 500.

---

## Spacing scale

All spacing derives from a base unit of 8px.

| Token | Value | Usage |
|---|---|---|
| `--space-1` | 4px | Tight internal gaps (icon + label) |
| `--space-2` | 8px | Component-internal padding |
| `--space-3` | 12px | Small gaps between related elements |
| `--space-4` | 16px | Default padding, card padding |
| `--space-6` | 24px | Section sub-gaps, grid gaps |
| `--space-8` | 32px | Between unrelated groups |
| `--space-12` | 48px | Section top/bottom padding (mobile) |
| `--space-24` | 96px | Section top/bottom padding (desktop) |

---

## Layout

```css
--max-width: 720px;       /* Content container max width */
--max-width-wide: 1080px; /* Wide layouts (feature grids) */
--gutter: 24px;           /* Side padding on mobile */
--gutter-lg: 48px;        /* Side padding on desktop */
```

**Rules:**
- All page content is centered in `--max-width` unless explicitly wide.
- No full-bleed color sections. Background is always `--color-bg` (white).
- Sections breathe — use `--space-24` (96px) vertical padding on desktop, `--space-12` (48px) on mobile.

---

## Border radius

| Token | Value | Usage |
|---|---|---|
| `--radius-sm` | 4px | Badges, tags, small pills |
| `--radius-md` | 8px | Buttons, inputs, small cards |
| `--radius-lg` | 12px | Cards, panels |
| `--radius-full` | 9999px | Fully rounded (avatars, toggles) |

---

## Shadows

Minimal. Only one level of elevation is used — for cards when they need separation from the page.

```css
--shadow-card: 0 1px 3px rgba(15, 23, 42, 0.06), 0 1px 2px rgba(15, 23, 42, 0.04);
```

**Rule:** use `--shadow-card` or a `--color-border` border — never both on the same element. Prefer border for flat surfaces; shadow only when the card floats above the page.

---

## Components

### Buttons

**Primary button** — solid accent fill, white text.

```
background:        --color-accent
background (hover): --color-accent-hover
color:             --color-text-on-accent
padding:           10px 20px
border-radius:     --radius-md
font-size:         --text-sm
font-weight:       500
border:            none
```

**Secondary button** — transparent, accent-colored border and text.

```
background:        transparent
background (hover): --color-accent-light
color:             --color-accent
border:            1px solid --color-accent
padding:           10px 20px
border-radius:     --radius-md
font-size:         --text-sm
font-weight:       500
```

**Ghost button** — no border, accent text, subtle hover.

```
background:        transparent
background (hover): --color-accent-light
color:             --color-accent
border:            none
padding:           8px 16px
font-size:         --text-sm
font-weight:       500
```

**Rules:**
- Verb-first labels. "Get started", "Learn more", "Send message" — not "Submit" or "Click here".
- One primary button per view section maximum.
- Buttons never have uppercase text.

### Cards

```
background:    --color-bg (white) or --color-surface (tinted)
border:        1px solid --color-border
border-radius: --radius-lg
padding:       --space-6 (24px)
```

No shadow on cards unless they need to float above surrounding content.
Card titles use `--text-lg` / weight 500. Card body uses `--text-base` / `--color-text-secondary`.

### Inputs

```
background:      --color-bg
border:          1px solid --color-border
border (focus):  1px solid --color-accent
border-radius:   --radius-md
padding:         10px 14px
font-size:       --text-base
color:           --color-text
outline:         none
```

Placeholder text uses `--color-text-muted`. No filled/tinted input backgrounds.

### Navigation

- Logo on the left, nav links on the right.
- Nav links: `--text-sm`, weight 500, color `--color-text-secondary`.
- Active/current link: color `--color-accent`.
- Nav hover: color `--color-text`.
- No nav background fill or border — floats cleanly above white page.
- Mobile: hamburger icon collapses to a full-width drawer.

### Section divider (signature element)

A single 1px horizontal rule in `--color-border` used only between major page sections. This is the one repeating graphic element in the design — no icons, illustrations, or decorative shapes unless they carry content.

```css
border: none;
border-top: 1px solid var(--color-border);
margin: 0;
```

---

## Dark mode

Dark mode is supported via `prefers-color-scheme: dark`.

| Token | Dark value |
|---|---|
| `--color-bg` | `#0f172a` |
| `--color-surface` | `#1e293b` |
| `--color-border` | `#334155` |
| `--color-accent` | `#3b82f6` |
| `--color-accent-hover` | `#60a5fa` |
| `--color-accent-light` | `#1e3a5f` |
| `--color-text` | `#f1f5f9` |
| `--color-text-secondary` | `#94a3b8` |
| `--color-text-muted` | `#475569` |
| `--color-text-on-accent` | `#ffffff` |

---

## Tailwind extension

Extend `tailwind.config.js` with:

```js
theme: {
  extend: {
    colors: {
      blue: {
        50:  '#eff6ff',
        100: '#dbeafe',
        600: '#2563eb',
        700: '#1d4ed8',
      },
      surface: '#f0f6ff',
      border:  '#dde8f5',
    },
    fontFamily: {
      sans: ['Inter', 'ui-sans-serif', 'system-ui', 'sans-serif'],
    },
    maxWidth: {
      content: '720px',
      wide:    '1080px',
    },
    borderRadius: {
      card: '12px',
    },
    spacing: {
      section:    '96px',
      'section-sm': '48px',
    },
  },
}
```

---

## Voice and copy

- Sentence case on everything. Buttons, headings, nav links, badges.
- Active voice. "Build faster" not "Faster building enabled."
- Short. One idea per sentence. No filler words ("simply", "just", "powerful").
- Contractions are fine ("you'll", "it's", "we've").
- CTAs are verbs: "Get started", "Read the docs", "See the work".

---

## What not to do

- No gradients anywhere.
- No drop shadows heavier than `--shadow-card`.
- No colorful section backgrounds (blue hero sections, etc.).
- No more than one primary button per section.
- No decorative icons or illustrations unless they carry real meaning.
- No font sizes outside the type scale.
- No colors outside the palette.
