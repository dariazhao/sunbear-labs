# Sunbear Labs — Design System

Extracted from the homepage (`index.html`) and extended with patterns from
Groundcover's product pages. This is the single source of truth for all pages.

---

## 1. Tokens (CSS Custom Properties)

```css
:root {
  /* ── Brand yellows ── */
  --yellow:        #FFCA00;
  --yellow-light:  #FFF4D9;
  --yellow-deep:   #CC9900;

  /* ── Backgrounds ── */
  --bg-page:       #FFFFFF;
  --bg-warm:       #FFFCF6;          /* Groundcover's signature cream */
  --bg-beige:      #F5F2EC;
  --bg-card:       #FFFFFF;
  --bg-active:     #F8F6F0;          /* hover/active state bg (from GC accordions) */

  /* ── Text ── */
  --text-1:        #101828;          /* headings, primary */
  --text-2:        #344054;          /* body copy */
  --text-3:        #667085;          /* captions, muted */

  /* ── Borders ── */
  --border:        #EAECF0;
  --border-mid:    #D0D5DD;

  /* ── Accent palette ── */
  --teal:          #D0ECE5;
  --teal-dark:     #2A6B58;
  --teal-mid:      #4BAF94;
  --blue:          #DCEBFF;
  --blue-brand:    #80AFFF;
  --purple:        #CD90E3;
  --purple-light:  #F3E6FA;
  --lavender:      #EDE8F8;
  --amber:         #FFE8CC;
  --amber-accent:  #FF8C00;

  /* ── Radii ── */
  --radius-pill:   999px;
  --radius-card:   16px;
  --radius-lg:     20px;            /* large cards, CTA strips */
  --radius-md:     8px;

  /* ── Shadows ── */
  --shadow-sm:     0 1px 3px rgba(16,24,40,.06);
  --shadow-md:     0 4px 12px rgba(16,24,40,.08);
  --shadow-lg:     0 12px 32px rgba(16,24,40,.11);

  /* ── Spacing scale (8px base) ── */
  --sp-1:  8px;
  --sp-2:  16px;
  --sp-3:  24px;
  --sp-4:  32px;
  --sp-5:  40px;
  --sp-6:  48px;
  --sp-8:  64px;
  --sp-10: 80px;

  /* ── Layout ── */
  --container:     1100px;
  --nav-height:    64px;
}
```

---

## 2. Typography

| Role | Font | Weight | Size | Notes |
|------|------|--------|------|-------|
| **H1** (page hero) | Nunito | 700 | `clamp(38px, 5.2vw, 58px)` | `letter-spacing: -0.02em; line-height: 1.08` |
| **H2** (section) | Nunito | 700 | `clamp(26px, 3.5vw, 40px)` | `letter-spacing: -0.015em; line-height: 1.12` |
| **H3** (card/subsection) | Inter | 700 | 17px | Normal tracking |
| **H4** (small heading) | Inter | 700 | 15px | Normal tracking |
| **Body** | Inter | 400–500 | 15–17px | `line-height: 1.65; color: var(--text-2)` |
| **Caption / Meta** | Inter | 500–600 | 12–13px | `color: var(--text-3)` |
| **Section label** | Inter | 700 | 11px | `letter-spacing: 0.10em; text-transform: uppercase; color: var(--text-3)` |
| **Eyebrow badge** | Inter | 700 | 11px | Same as label but inside a pill with yellow bg + border |
| **Wordmark** | Nunito | 800 | 17px | `letter-spacing: -0.01em` — always lowercase "sunbear labs" |

### Rules
- Nunito for display/headings only (H1, H2, step headings in flows)
- Inter for everything else (H3, H4, body, UI, buttons, nav)
- Two-color heading spans: `.em-teal` (var(--teal-dark)), `.em-gold` (var(--yellow-deep))
- Max heading width: ~720px for H1, ~600px for H2

---

## 3. Buttons

| Type | Class | Look |
|------|-------|------|
| **Primary** | `.btn-primary` | Yellow gradient (135deg: #FFE566 → #FFCA00 → #E8AA00), dark text, pill radius, diagonal glint `::before` overlay |
| **Outline** | `.btn-outline` | Transparent bg, 1.5px `--border-mid` border, pill radius |
| **Dark** | `.btn-dark` | Dark gradient (#1D2A3F → #101828), white text, pill radius, subtle glint |
| **Outline Dark** | `.btn-outline-dark` | Transparent bg, 2px dark border, pill radius |
| **Download** | `.btn-download` | Teal bg + teal-dark border, small (4px 10px), 6px radius |

### Shared behavior
- Hover: `opacity .85–.9`, `translateY(-1px)`
- All pill-shaped (`border-radius: var(--radius-pill)`)
- Font: Inter 600, 14–15px
- Arrow links: `.feat-link` — 13px Inter 600, colored per-section, arrow gap widens on hover + bounces up 3px

---

## 4. Navigation (shared across all pages)

```
┌─────────────────────────────────────────────────────┐
│ [logo SVG] sunbear labs   About Programs Vision ... │
│                                        [Get Started]│
└─────────────────────────────────────────────────────┘
```

- Sticky, `z-index: 100`
- Frosted glass: `rgba(255,255,255,.94)` + `backdrop-filter: blur(14px)`
- Height: 64px
- Bottom border: 1px `--border`
- Nav links: 14px Inter 500, `--text-2`, 8px 14px padding, 8px radius
- Active: `--text-1`, `--yellow-light` bg, font-weight 600
- CTA button: `btn-primary` in nav

---

## 5. Footer (shared across all pages)

- Background: `--bg-beige` with top border
- 5-column grid: brand (2fr) + 4 link columns (1fr each)
- Brand column: logo SVG + wordmark + tagline
- Column titles: 13px Inter 700
- Column links: 13px Inter 400, `--text-2`, hover → `--text-1`
- Bottom bar: copyright left, social links right, top border

---

## 6. Section Patterns

### 6a. Standard Section
```
padding: 80px 0 (var(--sp-10))
.container max-width: 1100px, 32px horizontal padding
centered section-label → h2 → section-sub → content
```

### 6b. Beige Band
```
background: var(--bg-beige) or linear-gradient(135deg, #F5F2EC → #EAF2EE → #F5F2EC)
border-top + border-bottom: 1px var(--border)
padding: 64px 0
```
Used for: audience strip, stats, any section needing visual separation.

### 6c. Warm Background Section
```
background: var(--bg-warm) (#FFFCF6)
border-top: 1px var(--border)
```
Used for: FAQ, secondary content areas.

### 6d. CTA Strip
```
background: linear-gradient(135deg, #FFD740 → #FFCA00 → #F5A800)
border-radius: 20px
padding: 64px 56px
```
Full-width yellow banner with dark buttons. Optional botanical illustration floating from corner.

### 6e. Full-Width Illustration Divider
An image (like `floralbottom.png`) spanning full width between sections, `line-height: 0`, no padding.

---

## 7. Card Patterns

### 7a. Feature Card (from homepage)
```
bg: white, 1px border, 16px radius
padding: 30px
border-top: 3px solid [accent color] (yellow/teal/blue/amber)
hover: shadow-lg + translateY(-3px)
```
Contains: icon badge (46px, 11px radius, pastel bg) → title (17px 700) → desc (14px) → arrow link.

### 7b. Resource Card (from homepage)
```
bg: white, 1px border, 16px radius, overflow hidden
thumbnail area: 132px height, centered illustration
body: 20px padding
```
Contains: type label (10px uppercase) → title (15px 700) → meta (12px) → download button.

### 7c. Audience Card (from homepage)
```
bg: transparent (sits on beige band)
no border, no shadow
```
Contains: icon badge (40px, 10px radius, pastel bg) → title → description → floating stat chip.

### 7d. Program Card (NEW — for Programs page)
```
bg: white, 1px border, 16px radius
padding: 0 (image area) + 28px (body)
hover: shadow-lg + translateY(-3px)
```
Contains: illustration thumbnail (full-width, 180px, pastel bg tint) → program name (Nunito 700 17px) → tagline → audience pills → arrow link.

### 7e. Team/Person Card (NEW — for About page)
```
bg: white, 1px border, 16px radius
padding: 24px, text-align: center
```
Contains: avatar/illustration (80px circle) → name (Inter 700 15px) → role (Inter 400 13px, --text-3) → optional one-liner.

### 7f. Research Citation Card (NEW — for Vision page)
```
bg: var(--bg-warm), 1px border, 12px radius
padding: 24px
border-left: 3px solid var(--teal-dark)
```
Contains: quote/finding (Inter 500 15px, italic) → source (Inter 600 13px) → institution (Inter 400 13px, --text-3).

### 7g. Download Resource Card (NEW — for Resources page)
```
bg: white, 1px border, 16px radius, overflow hidden
hover: shadow-lg + translateY(-3px)
```
Contains: preview thumbnail (160px, light bg) → category pill → title → format + page count meta → "Download Free" button.

### 7h. Dashboard Preview Card (NEW — for Resources page)
```
bg: white, 1px border, 20px radius
padding: 0
overflow: hidden
```
Contains: dark top bar (mock browser chrome) → screenshot/mockup image → caption below.

---

## 8. Layout Compositions (from Groundcover product pages)

### 8a. Alternating Image + Text Blocks
```
┌──────────────────────────────────┐
│  [IMAGE]         Title           │
│                  Description     │
│                  • Bullet        │
│                  • Bullet        │
│                  → Learn more    │
├──────────────────────────────────┤
│  Title           [IMAGE]         │
│  Description                     │
│  • Bullet                        │
│  • Bullet                        │
│  → Learn more                    │
└──────────────────────────────────┘
```
- 2-column grid: `1fr 1fr`, gap 48–64px, vertically centered
- Image side: `border-radius: 16px`, hover `scale(1.02)` subtle
- Text side: section-label → h3 → body → bullet list → arrow link
- Alternates: even rows use `order` or reversed grid

### 8b. Accordion + Side Image (from GC migration page)
```
┌──────────────────────────────────┐
│  [Accordion Item 1] ▼   [IMG]   │
│  [Accordion Item 2]             │
│  [Accordion Item 3]             │
└──────────────────────────────────┘
```
- Left: vertical accordion, each item expands to show description
- Right: image swaps based on active accordion item
- Active item: bg shifts to `--bg-active`, left border accent
- Image transitions: `opacity` + `translateY` on swap

### 8c. Three-Column Icon Grid
```
┌────────┐  ┌────────┐  ┌────────┐
│  icon  │  │  icon  │  │  icon  │
│ Title  │  │ Title  │  │ Title  │
│ Desc   │  │ Desc   │  │ Desc   │
└────────┘  └────────┘  └────────┘
```
- `grid-template-columns: repeat(3, 1fr)`, gap 20px
- Each: icon (46px badge) → h4 → short description
- No card border — lives on beige or white bg, content only

### 8d. Stats Row
```
┌─────────┬─────────┬─────────┬─────────┐
│  2400+  │   38    │   91%   │  Free   │
│educators│ states  │on-track │ always  │
└─────────┴─────────┴─────────┴─────────┘
```
- 4-column grid, divided by 1px borders
- Number: Nunito 800, 44px (accent color on key character)
- Label: Inter 500, 14px, --text-2
- Lives on beige gradient bg

### 8e. FAQ Accordion (2-column)
```
┌──────────────────────────────────┐
│  LABEL        ┌────────────────┐ │
│  Heading      │ Q: Question  ▼ │ │
│  Subtext      │ Q: Question    │ │
│               │ Q: Question    │ │
│               └────────────────┘ │
└──────────────────────────────────┘
```
- Left column sticky (`top: 100px`): label + heading + subtext
- Right column: accordion items with `+` icon that rotates 45° on open
- Answer wraps: `max-height` transition

---

## 9. Animations & Interactions

| Pattern | CSS | Used for |
|---------|-----|----------|
| **Card hover lift** | `translateY(-3px) + shadow-lg` | Feature cards, resource cards |
| **Arrow link nudge** | `gap: 5px → 9px` on hover + `translateY(-3px)` | "Learn more →" links |
| **Icon pop** | Custom keyframes per persona (spin/pulse/rotate) | Audience card icons on hover |
| **Stat chip float** | `translateY(0 → -5px)` 2.8s infinite | Floating stat badges |
| **Entrance reveal** | `opacity 0→1, translateY(20→0)` on scroll | Audience cards, any scroll-reveal |
| **Accordion expand** | `max-height: 0 → 400px`, 0.38s ease | FAQ, feature accordions |
| **Accordion icon** | `rotate(0 → 45deg)` | Plus icon in FAQ |
| **Image hover zoom** | `scale(1) → scale(1.02–1.05)` | Images in alternating blocks |
| **Button glint** | Diagonal white gradient overlay via `::before` | Primary + dark buttons |
| **Focus ring** | `outline: 2px solid var(--yellow-deep), offset 3px` | All focusable elements |

### Scroll-reveal (applied site-wide)
```css
.reveal { opacity: 0; transform: translateY(20px); transition: opacity 0.5s, transform 0.5s; }
.reveal.visible { opacity: 1; transform: translateY(0); }
```
Triggered via IntersectionObserver at ~20% threshold.

---

## 10. Responsive Breakpoints

| Breakpoint | Behavior |
|------------|----------|
| **> 1100px** | Full layout, all columns |
| **≤ 900px** | 2-col grids → 1-col, nav links collapse to hamburger, alternating blocks stack |
| **≤ 600px** | Stats 4-col → 2×2, footer 5-col → stacked, padding reduces |

### Mobile rules
- Nav links hidden, hamburger menu appears
- All grids collapse to single column
- CTA strip: stacks vertically, full-width buttons
- FAQ: single column (no sticky sidebar)
- Images: `max-width: 100%`, `border-radius` preserved

---

## 11. Illustration Placement Rules

| Context | Treatment |
|---------|-----------|
| **Hero** | Full-width below CTAs, may overlap upward with negative margin |
| **Alternating blocks** | `border-radius: 16px`, contained in column, subtle zoom on hover |
| **Card thumbnails** | Fixed height (132–180px), `object-fit: contain`, light pastel bg |
| **Vision/aspirational** | Full-width in rounded card (`border-radius: 20px`), generous padding |
| **Dividers** | Full-bleed, `line-height: 0`, no padding, separates major sections |
| **CTA strip accent** | `position: absolute`, floats from corner, `opacity: .88`, decorative only |

---

## 12. Page-Specific Palette Tints

Each page uses the full token set but emphasizes one accent for identity:

| Page | Accent emphasis | Used on |
|------|----------------|---------|
| **Homepage** | Yellow + Teal | CTAs, stats, audience icons |
| **About** | Teal | Pillar icons, team section, credibility signals |
| **Programs** | Full palette | Each program gets its own accent (yellow, teal, blue, purple, amber, lavender) |
| **Vision** | Teal-dark + Gold | Research citations, stats, aspirational quotes |
| **Resources** | Blue + Teal | Category pills, download buttons, dashboard previews |

---

## 13. Do / Don't

| ✓ Do | ✗ Don't |
|------|---------|
| Use beige/cream for section breaks | Use dark/black backgrounds anywhere |
| Keep all illustrations in warm, botanical style | Mix in photos or stock imagery |
| Use Nunito only for H1/H2 display text | Use Nunito for body copy or UI |
| Use pill radius for buttons and badges | Use pill radius on cards |
| Use 3px colored top-border on feature cards | Use full colored backgrounds on cards |
| Say "activity" not "assessment" | Say "assessment" or "test" |
| Write "pre-K" (lowercase p, capital K) | Write "Pre-K" or "pre-k" |
| Write "kindergarten" lowercase | Capitalize "Kindergarten" mid-sentence |
| Keep copy concise, warm, professional | Sound clinical, corporate, or cutesy |
