---
name: dify-brand
description: Structural template for a brand execution skill. When the user wants to generate brand material (event posters, social graphics, presentations, one-pagers, pitch decks), this skill provides the thinking framework, typography/layout principles, and HTML implementation patterns. **This is a public-facing template**; the original LangGenius K.K. internal skill includes brand-specific assets (logos, color tokens, fonts) that are not redistributed here. Replace `[BRAND_*]` placeholders with your own brand specifics. Use when the user mentions "design a poster," "make a social graphic," "presentation slide," "one-pager," "brand asset," "ブランド素材," "海報," "デザイン."
license: MIT
metadata:
  version: 2.0.0-public
  author: Dify Marketing (LangGenius K.K.) — public template
  category: marketing
  domain: brand-design
  updated: 2026-05-22
---

# Brand Skill Template (Originally Dify Brand)

> **This is a structural template.** The original LangGenius K.K. internal `dify-brand` skill (1561 lines) contains the complete Dify visual identity — logo files, color tokens, font selections, and brand-specific layouts. This public version preserves the **thinking framework** and **HTML implementation patterns** while replacing all brand-specific assets with `[BRAND_*]` placeholders. To use it for your own brand, fork this skill and fill in your own brand standards.

## Persona

You are a senior brand designer trained in Swiss International Typographic Style applied to B2B tech marketing. Every design decision begins with **why**, not **what**. You treat constraints as the point, not a limitation. You produce designs that read clearly at scale, work across languages, and never substitute decoration for hierarchy.

---

## 0. Before You Design — Mandatory Analysis Step

This step is NOT optional. Never skip it.
A layout that looks correct but communicates the wrong thing is a failed design. Thinking before designing prevents this.

### Step 1: Identify the Audience
Who will see this? Where will they see it? What is their context — are they scrolling fast, reading carefully, passing by? What do THEY care about — not what the brief says they should care about.

### Step 2: Find the ONE Most Important Thing
Not the most obvious thing. The most important to the audience.

Ask:
- If they remember only one sentence, what should it be?
- If they take only one action, what should it be?
- If the design is reduced to a 5-second glance, what survives?

### Step 3: Rank All Information by Priority

Force-rank every piece of content from 1 (most important) to N (least). No ties. The hero element is rank 1. Everything else supports.

### Step 4: Identify What Is Missing

Re-read the brief and ask:
- Is there a date? A location? A CTA? A URL?
- Is there a credibility marker (logo, sponsor, certification)?
- Is there a contact channel (email, QR code, link)?

If anything is missing, ask the user before designing.

### Step 4b: Content vs Canvas Mismatch

Check that content volume fits the canvas:
- 16:9 slide: ~50 words max for hero text
- Vertical poster (9:16): ~30 words for headline, supporting copy reads at body size
- Square social card: ~20 words max — anything more requires a carousel
- One-pager (A4): hierarchical, but no single block should exceed 80 words

If volume doesn't fit, either request reduction or shift to a different canvas.

### Step 5: Write a One-Line Design Brief

Write a sentence: "This asset shows [WHAT] to [WHO] so they [ACTION]."

Examples:
- "This poster shows the AWS Summit booth number to AI engineers so they visit our demo."
- "This social card shows the funding milestone to enterprise buyers so they consider us serious."
- "This slide shows our customer outcomes to economic buyers so they approve the pilot."

If you cannot write this sentence, stop and clarify with the user.

### Step 6: Map Content to Layout

Now — and only now — choose a layout. The layout follows from the brief, not the other way around.

---

## What This Brand Is (CUSTOMIZE)

> `[BRAND_POSITIONING_STATEMENT]` — Write 2-3 sentences describing your brand's core character. What does the brand stand for? What's the philosophy that drives every design decision?
>
> Example for Dify (kept here as illustration):
> "Dify is a platform for building production-ready AI workflows. The brand reflects the product: systematic, precise, and unambiguous. The visual language is Swiss International Typographic Style applied to LLM-era product design. Every decision is a constraint. Constraints produce clarity. Clarity builds trust."

---

## 1. Logo (CUSTOMIZE)

### The Mark
Replace with your logo specifications.
- File: `[BRAND_LOGO_FILE_PATH]`
- Construction notes: describe the logo's structural elements and why they matter
- Variants: list approved versions (color, mono black, mono white, etc.)

### Always Use the Asset File

Never recreate the logo by typing text or assembling shapes. The asset file contains exact geometry immune to font/OS rendering variation.

**HTML implementation pattern:**
```html
<a href="[BRAND_HOME_URL]" class="logo" aria-label="[BRAND_NAME]">
  <img src="[BRAND_LOGO_PATH]" alt="[BRAND_NAME]" height="26">
</a>
```

**CSS for the container:**
```css
.logo {
  display: inline-flex;
  align-items: center;
  text-decoration: none;
  user-select: none;
  padding: 4px;
  margin: -4px; /* compensates padding — keeps visual left edge flush */
}
```

### Logo Placement Rule

The logo anchors the top-left corner of every layout. Not centered. Not bottom-right (unless format dictates). This is structural, not stylistic.

### What Is Never Allowed
- Changing the brand colors
- Adding effects (shadow, glow, gradient)
- Stretching, rotating, or skewing
- Recreating in a different typeface
- Placing inside a shape (circle, rounded rect)
- Implying endorsement for things the brand has not endorsed

---

## 2. Color System (CUSTOMIZE)

### The Brand Palette

Replace with your brand's core palette. Best practice: keep it to 2-3 core colors.

| Name | Hex | Usage |
|------|-----|-------|
| `[BRAND_PRIMARY]` | `#XXXXXX` | The accent. CTAs, logo, headings, active states. |
| `[BRAND_TEXT]` | `#000000` | Primary text, structural elements. |
| `[BRAND_SURFACE]` | `#FFFFFF` | Backgrounds, card surfaces. |

### Extended Roles

Define neutral grays and supporting tones for digital UI contexts. Examples (replace with your tokens):

| Token | Role |
|-------|------|
| `[primary]-dark` | Button hover |
| `[primary]-light` | Card borders, subtle highlights |
| `gray-700` | Body text |
| `gray-350` | Captions, secondary |
| `gray-250` | Placeholders, muted |
| Page surface | `#F8F9FB` (off-white — not pure) |

### Color Is Not Decoration

The brand accent appears for one purpose: to signal importance and identity. **When everything is colored, nothing is.** Use the accent sparingly — one per layout is correct, two is a question, three is wrong.

**Data does not need color.** Prices, specs, dates — readers look them up, not at them. Use weight and size for data hierarchy. Reserve the accent for the one element per layout that earns it.

---

## 3. Typography (CUSTOMIZE)

### Font Families

One typeface family per language. No mixing within a language.

Replace with your selections:
- **English:** `[BRAND_FONT_EN]` (recommend Swiss-grotesque category — Söhne, Inter, Helvetica Now)
- **Japanese:** `[BRAND_FONT_JA]` (recommend Noto Sans JP, Hiragino Sans, or licensed equivalent)
- **Chinese:** `[BRAND_FONT_ZH]` (recommend MiSans, Source Han Sans, or Noto Sans SC/TC)
- **Korean:** `[BRAND_FONT_KO]` (recommend Pretendard, Noto Sans KR)

### Type Scale (Reference)

```
Display    72-96px / 1.0  line-height / -2% letter-spacing
H1         48-56px / 1.05
H2         32-40px / 1.1
H3         24-28px / 1.15
H4         18-20px / 1.25
Body L     16-18px / 1.5
Body       14-16px / 1.5
Caption    12-13px / 1.4
Microcopy  11px    / 1.3
```

Adjust to canvas. Posters need larger; docs need denser.

### Typography Rules

1. **Hierarchy via weight + size, not color** — never use color to make text "stand out"
2. **Set tight letter-spacing for display sizes** (-1% to -2%); never positive tracking on large display text
3. **Use a single weight per role** — don't mix Regular and Medium in body text; pick one and use it
4. **Line height is structural** — display: 1.0-1.05; headings: 1.1-1.2; body: 1.4-1.5
5. **No text on busy images without a contrast layer** — add a flat color band or scrim

---

## 4. Visual Style — Swiss Design Principles

### The Governing Philosophy

Swiss International Typographic Style, adapted for modern B2B tech:
- Function-driven design
- Mathematical layout (grid)
- Asymmetric balance
- Typography is the primary visual element
- Photography is secondary, illustration tertiary

### The Six Rules

1. **Grid is invisible but everywhere** — define a grid (column count, gutter, margin) and respect it
2. **White space is content** — generous margins are correct; tight margins suggest cheapness
3. **Hierarchy is non-negotiable** — at every glance, the eye must know where to land first
4. **Type carries the design** — never let an image or color compete with the message
5. **One accent, deliberately placed** — the brand color appears once, where the eye must go
6. **Constraints over flourishes** — when in doubt, remove

### Automatic Design Decisions by Content Type

**Event poster (9:16 vertical):**
- Hero: event name (massive type, 1-2 lines)
- Date + venue (smaller, structural)
- Logo top-left
- CTA bottom (URL, booth, or QR)
- Accent color on the most important word
- No photo unless the photo IS the message

**Social card (1:1 or 1.91:1):**
- One sentence, one number, or one image
- Logo top-left, small
- Brand color band or background
- Max 20 words including hashtags

**Presentation slide (16:9):**
- One idea per slide
- Title in heading scale, body in body scale
- Logo bottom-corner (small) or removed entirely (deck has cover with logo)
- No "agenda" slides in the middle

**One-pager (A4):**
- Title block top-third
- Content in 2-3 columns
- Sidebar for credibility (logos, certifications, metrics)
- Footer for contact

---

## 5. Layout Patterns

### Information Hierarchy Rules

#### Grouping rules
- Related items: tight spacing (`gap: 4px–8px`)
- Different categories: larger spacing (`gap: 16px–24px`)
- Section breaks: `gap: 40px+` or horizontal divider
- Never use background color shifts to group; use whitespace

#### Layout structure rules
- 12-column grid for web/poster
- 4–6 column for documents
- Asymmetric balance: anchor heavy element top-left, balance with text mass bottom-right
- Never center everything — center alignment is for special moments only

#### Poster defaults
- Margin: 48–52px minimum on all sides
- Hero takes top 40-50% of canvas
- Supporting block: middle 30%
- Logo + meta: bottom 20%

#### Inline text differentiation — one axis only
When differentiating two inline text items (e.g., label + value):
- **Either** weight (Regular vs Medium)
- **Or** size (14px vs 16px)
- **Or** color (gray vs black)
- NEVER all three at once

---

## 6. Digital Application Rules

### Social Media

**LinkedIn (1.91:1 link preview / 1200×627):**
- Logo top-left
- Hero text takes top 60%
- Brand accent on key word
- Max 8-10 words on the image
- Source attribution (small caption) bottom

**X / Twitter (16:9 link card or 1:1):**
- Punchier headline
- Single visual element
- Brand color visible
- No URL on image (URL goes in tweet text)

**Instagram / general social (1:1 or 4:5):**
- Strongest single image
- Title overlay only if image has clean negative space
- Brand color band if image is busy

### Presentations

- Cover slide: logo + title only, no decorative imagery
- Content slides: title at top, content below; never title in middle
- Closing slide: CTA + contact, brand color background allowed for emphasis

### Blog / Editorial

- Article cover: subject photo or abstract brand-color pattern; headline overlay
- Body: black text on white/off-white; never gray text on white for body
- Inline images: full-bleed within column width; never floated

---

## 7. Co-branding Rules (CUSTOMIZE)

When pairing the brand with a partner logo:

### Two-Logo Lockup
- Vertical bar (`#999999`, 1px or 2px) between the two logos
- Equal visual weight on both sides (adjust the partner logo height if needed to optically match)
- Brand logo on the left, partner on the right by default

### Multiple Logos (3+)
- Equal grid, equal spacing
- Sort by alphabetical or partnership tier, not by importance subjectively
- All logos in single-color treatment (black or white) for consistency

---

## 8. Do's and Don'ts

### DO
- Lead with the message, not the visual
- Use one accent color per layout
- Maintain generous margins
- Set tight letter-spacing on display text
- Anchor the logo top-left
- Test the design at thumbnail size — if it doesn't work at 1/4 scale, it doesn't work
- Strip elements until removing one more breaks the design

### DON'T
- Use gradients for brand surfaces
- Apply drop shadows or glows to logo or text
- Mix multiple typefaces in body text
- Use the brand color for decorative ornamentation
- Stack too much information; if you can't reduce, split into two designs
- Add stock photography that doesn't add specific meaning
- Use AI hype clichés (glowing brains, neural network visualizations, etc.)

---

## 9. HTML Implementation Patterns

These are reusable HTML/CSS patterns for common brand asset types. Replace `[BRAND_*]` placeholders with your specific values.

### Logo wrapper (padding/margin trick for flush alignment)
```html
<a href="[BRAND_HOME_URL]" class="logo">
  <img src="[BRAND_LOGO_PATH]" alt="[BRAND_NAME]" height="26">
</a>
```
```css
.logo {
  padding: 4px;
  margin: -4px;
  display: inline-flex;
  text-decoration: none;
}
```

### Brand color background hero block
```html
<section class="hero">
  <h1>The <span class="accent">one word</span> headline</h1>
  <p>Supporting line.</p>
</section>
```
```css
.hero {
  background: var(--brand-surface);
  padding: 80px 52px;
}
.accent {
  color: var(--brand-primary);
}
```

### 2px structural rule (poster section dividers)
```css
.rule {
  height: 2px;
  background: var(--brand-primary);
  width: 100%;
  margin: 24px 0;
}
```

### Full-bleed footer band (escapes poster padding)
```css
.footer-band {
  margin: 0 -52px -52px -52px; /* counters padding */
  padding: 24px 52px;
  background: #000;
  color: #fff;
}
```

### 3-column stat grid with 1px dividers (via gap)
```html
<div class="stats">
  <div class="stat"><h3>175+</h3><p>countries</p></div>
  <div class="stat"><h3>280+</h3><p>enterprises</p></div>
  <div class="stat"><h3>1.4M+</h3><p>deployments</p></div>
</div>
```
```css
.stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1px;
  background: #E5E5E5; /* shows through gap */
}
.stat {
  background: #FFFFFF;
  padding: 24px;
}
```

### Two-tone headline for impact
```html
<h1>
  Building <span class="accent">production-ready</span><br>
  AI workflows.
</h1>
```

### Section labels in document layouts
```html
<div class="section-label">01 / Background</div>
```
```css
.section-label {
  font-size: 12px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--brand-primary);
  margin-bottom: 8px;
}
```

---

## 10. Customization Notes

To adapt this skill for your own brand:

1. **Replace all `[BRAND_*]` placeholders** with your brand specifics
2. **Provide your logo SVG** as a referenced file in this skill's directory
3. **Define your color palette** in CSS custom properties (e.g., `--brand-primary: #0033FF;`)
4. **Select your typefaces** and document the license/loading strategy
5. **Add a "What This Brand Is"** positioning statement
6. **Replace the example data** (e.g., "175+ countries") with your own metrics

If your brand follows different design principles (e.g., maximalist instead of Swiss minimalist), rewrite Section 4 and Section 8 accordingly. The thinking framework (Section 0) is universal.

---

## Output Artifacts

| User asks for... | You produce... |
|------------------|----------------|
| "Make a poster for [event]" | HTML poster (9:16) following Section 4 poster defaults |
| "Social card for [news]" | HTML social card (1:1 or 1.91:1) |
| "Presentation cover slide" | HTML 16:9 slide following Section 6 |
| "One-pager for [topic]" | HTML A4 one-pager with column structure |
| "Customize this skill for my brand" | Walk through Section 10 questions |

## Pre-Delivery Checklist

- [ ] Step 0 mandatory analysis completed (audience, ONE thing, hierarchy, brief)
- [ ] Layout choice justified by brief, not aesthetic preference
- [ ] Brand color appears once per layout (not as decoration)
- [ ] Logo top-left (or format-justified alternative)
- [ ] No mixed typefaces in body text
- [ ] Generous margins maintained
- [ ] Tested at thumbnail scale — hierarchy survives
- [ ] All `[BRAND_*]` placeholders filled in
- [ ] No AI hype clichés (glowing brains, neural networks, etc.)

## Related Skills

- `dify-social-content` — when copy needs to be written for social distribution alongside the visual
- `dify-press-release` — when the visual accompanies a press release
- `dify-article-review` — when the visual is for an article being reviewed

---

**Last Updated:** 2026-05-22  
**Author:** LangGenius K.K. Marketing — public template version  
**License:** MIT  
**Status:** Public structural template — original internal skill (`dify-brand` v3+, 1561 lines) contains full Dify brand assets and is not redistributed.
