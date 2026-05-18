# DESIGN.md — noivan.dev Portfolio

> Version 1.0 | 2026-05-18
> Inspired by: Linear.app, Stripe, brittanychiang.com, rauno.me, antfu.me

---

## Brand Identity

**Name**: noivan
**Tagline (KO)**: 문제를 자동화로 해결합니다
**Tagline (EN)**: I automate what slows you down
**Tone**: Confident, minimal, sharp — not humble, not loud
**Archetype**: The Precision Engineer who ships

---

## Color System

### Core Palette
```
--color-bg:           #080810   /* near-black, slight blue tint — Linear ref */
--color-bg-2:         #0f0f1a   /* card backgrounds */
--color-bg-3:         #161625   /* elevated surfaces */
--color-border:       rgba(255,255,255,0.07)
--color-border-hover: rgba(255,255,255,0.14)

--color-text:         #f0f0f8   /* primary text */
--color-muted:        #6b6b8a   /* secondary text */
--color-subtle:       #3a3a5c   /* disabled / placeholders */

--color-accent:       #5e6ad2   /* Linear purple — primary CTA */
--color-accent-light: #828fff   /* hover state */
--color-accent-glow:  rgba(94,106,210,0.15)

--color-green:        #2dd4aa   /* active / success */
--color-amber:        #f59e0b   /* warning / building */
```

### Gradient System
```
--gradient-hero:    linear-gradient(135deg, #5e6ad2 0%, #828fff 50%, #2dd4aa 100%)
--gradient-text:    linear-gradient(90deg, #f0f0f8 0%, #828fff 60%, #2dd4aa 100%)
--gradient-card:    linear-gradient(135deg, rgba(94,106,210,0.08) 0%, rgba(45,212,170,0.04) 100%)
--gradient-noise:   url("noise.svg") — 3% opacity overlay
```

### Background Orbs (ambient light)
```
Orb 1: position top-left  | color #5e6ad2 | blur 140px | opacity 0.12
Orb 2: position top-right | color #2dd4aa | blur 160px | opacity 0.08
```

---

## Typography

### Fonts
```
Primary:  "Inter Variable" — body, UI, numbers
          weights: 300, 400, 500, 600, 700
          src: Google Fonts / bunny.net

Mono:     "JetBrains Mono" — labels, tags, code
          weights: 400, 500

Display:  Inter Variable, weight 700-800, tight tracking
```

### Scale
```
--text-xs:    12px / line-height 1.4 / tracking +0.5px  — labels, tags
--text-sm:    14px / line-height 1.5                    — secondary body
--text-base:  16px / line-height 1.7                    — body
--text-lg:    18px / line-height 1.6                    — lead text
--text-xl:    22px / line-height 1.4
--text-2xl:   28px / line-height 1.25 / tracking -0.5px
--text-3xl:   36px / line-height 1.15 / tracking -1px
--text-4xl:   clamp(42px, 5.5vw, 72px) / tracking -2px  — hero
```

### Weight Conventions
```
300 — long body paragraphs
400 — standard body
500 — labels, nav links, pills
600 — card headings, subheadings
700 — section titles
800 — hero headline
```

---

## Spacing System (8px base)

```
--space-1:   4px
--space-2:   8px
--space-3:   12px
--space-4:   16px
--space-5:   24px
--space-6:   32px
--space-7:   48px
--space-8:   64px
--space-9:   96px
--space-10: 128px

Section padding: 120px top/bottom (desktop), 80px (mobile)
Container max-width: 1100px | padding: 0 32px
```

---

## Component System

### Navigation
```
Position: fixed, top
Height: 64px
Background: rgba(8,8,16,0.75) + backdrop-blur(20px)
Border-bottom: 1px solid var(--color-border)
Logo: JetBrains Mono, 14px, color accent-light
Links: 14px, weight 400, color muted → text on hover
Right side: Language toggle (KO / EN) + CTA button
```

### Section Label (Eyebrow)
```
Font: JetBrains Mono
Size: 11px
Weight: 500
Color: accent
Letter-spacing: 3px
Text-transform: uppercase
Margin-bottom: 12px
Pattern: "01 — About" format
```

### Cards
```
Background: bg-2
Border: 1px solid border
Border-radius: 14px
Padding: 28px
Hover: border-color → border-hover + translateY(-2px)
Transition: 200ms ease
Top accent line: 2px gradient on hover (accent → green)
```

### Buttons
```
Primary:
  bg: accent (#5e6ad2)
  color: white
  padding: 12px 28px
  border-radius: 10px
  hover: bg accent-light + shadow 0 8px 24px accent-glow
  font: 15px / weight 500

Ghost:
  bg: transparent
  border: 1px solid border
  color: muted
  hover: border-hover + color text
```

### Pills / Tags
```
Font: JetBrains Mono, 11px, weight 500
Padding: 3px 10px
Border-radius: 100px
Variants:
  purple: bg rgba(94,106,210,0.12), color #828fff
  green:  bg rgba(45,212,170,0.10), color #2dd4aa
  amber:  bg rgba(245,158,11,0.10), color #f59e0b
```

---

## Layout Structure (Marketing)

```
[NAV] — fixed, KO/EN toggle right
[HERO] — Headline → Problem Framing → Key Outcomes → Dual CTA (Investors | Clients)
[SOCIAL PROOF] — 4 numbers strip: quantified results
[PROBLEM] — 3-column "What slows teams down"
[SOLUTION/PROJECTS] — KRAYT + Allsweep + NOVA with outcome framing
[HOW IT WORKS] — 3-step process (for clients)
[RESULTS] — Testimonial / metric proof
[CTA SPLIT] — Investor track vs Client track
[CONTACT]
[FOOTER]
```

---

## Animation Principles

```
1. Entrance: fadeIn + translateY(16px) → 0 | duration 400ms | stagger 60ms
2. Hover transitions: 200ms ease
3. No auto-playing animations in hero
4. Scroll-triggered only (IntersectionObserver threshold 0.15)
5. Respect prefers-reduced-motion
```

---

## Language Toggle System

```
Default: Korean (KO)
Toggle: KO ↔ EN button, top-right nav
Implementation: data-ko / data-en attributes on all text nodes
JS: toggle class 'lang-en' on <html>
  [data-ko] { display: block }
  [data-en] { display: none }
  .lang-en [data-ko] { display: none }
  .lang-en [data-en] { display: block }
```

---

## References Analyzed

| Site | Key Takeaway |
|------|-------------|
| linear.app | CSS var system, #141516 bg, #5e6ad2 accent, Inter Variable |
| stripe.com | Problem → Solution copy structure, gradient accents #533afd |
| brittanychiang.com | slate-900 bg, teal accent, two-column fixed nav |
| rauno.me | Ultra-minimal, single-column, strong typography |
| antfu.me | Personal + open source dual framing |
| paco.me | "Crafting interfaces" — craft-first positioning |
