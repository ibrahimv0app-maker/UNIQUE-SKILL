# **UI/UX PRO MAX — The Lovable Design Bible**

## **Part 1: Core Design System & Foundations**

*World-Class UI/UX System for Modern Web, SaaS, and Branding*

---

## **📜 TABLE OF CONTENTS (Part 1)**

1. **[The Lovable Stack — Hard Rules](#1-the-lovable-stack--hard-rules)**
2. **[The 6-Step Design Ritual](#2-the-6-step-design-ritual)**
3. **[Choosing An Aesthetic Direction (15+ Named Styles)](#3-choosing-an-aesthetic-direction-15-named-styles)**
4. **[Color Theory with OKLCH (24 Ready Palettes + Custom Recipes)](#4-color-theory-with-oklch-24-ready-palettes--custom-recipes)**
5. **[Typography (Font Pairs, Scales, Hierarchy)](#5-typography-font-pairs-scales-hierarchy)**
6. **[Spacing, Rhythm & Layout Archetypes](#6-spacing-rhythm--layout-archetypes)**
7. **[shadcn + CVA — Composition Patterns (Code)](#7-shadcn--cva--composition-patterns-code)**
8. **[Section Recipes (Hero, Pricing, Feature, CTA, Footer)](#8-section-recipes-hero-pricing-feature-cta-footer)**

---

## **🎯 MANIFESTO**

**Mantra:**  
*Tokens before components. Variants before classNames. References before "vibes". Restraint before features. No purple gradients on white.*

**Mission:**  
Ship interfaces that win **Awwwards**, not look like another v0 demo. Every pixel, animation, and word must earn its place.

---

## **1. THE LOVABLE STACK — HARD RULES**

### **⚡ Non-Negotiable Constraints**


| **Constraint**       | **Rule**                                                                                       | **Why?**                                                |
| -------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Tailwind**         | v4, configured in `src/styles.css` via `@import "tailwindcss"` + `@theme inline`.              | No `tailwind.config.js`. Keep it lean and future-proof. |
| **Colors**           | `oklch(L C H)` only. Never `text-white`, `bg-black`, `bg-[#hex]`, or inline RGB.               | Perceptually uniform, accessible, and consistent.       |
| **Components**       | `shadcn` lives in `src/components/ui/*`. Extend via **CVA variants**, never ad-hoc classNames. | Scalable, maintainable, and themed.                     |
| **Fonts**            | Load with `<link>` in `src/routes/__root.tsx` head. Never `@import` a remote URL in CSS.       | Lightning CSS compatibility. Avoid FOUC.                |
| **Custom Utilities** | Use `@utility name { ... }`, not `@layer utilities`.                                           | Cleaner, more maintainable, and scoped.                 |
| **Variants**         | `@custom-variant dark (&:is(.dark *));` already wired.                                         | Built-in dark mode support.                             |
| **Tokens**           | New token? Add to `:root`, register in `@theme inline` as `--color-<n>: var(--<n>);`.          | Centralized control. One source of truth.               |
| **Routing**          | TanStack Start — every section in its own route file under `src/routes/`.                      | Modular, scalable, and easy to maintain.                |


> **🚨 Golden Rule:** If you write `className="bg-white text-black"`, **STOP**. Extend the design system instead.

---

## **2. THE 6-STEP DESIGN RITUAL**

**Run in order. Never skip. Never inline. Never improvise.**

### **🔍 Step 1 — Discover**

Answer these **out loud** before writing a single line of code:

1. **What is this?** (Product category + one-liner)
  - *Example: "A pricing page for a calm to-do app."*
2. **Who uses it?** (The realest possible user)
  - *Example: "Indie makers who juggle multiple projects."*
3. **What should it feel like?** (One adjective + one reference)
  - *Example: "Like Things 3 — quiet, precise, generous whitespace."*

**Full Example:**  
*"A pricing page for a calm to-do app, used by indie makers, that feels like Things 3 — quiet, precise, generous whitespace."*

### **🎯 Step 2 — Commit a Direction**

- Pick **one** aesthetic from **[§3](#3-choosing-an-aesthetic-direction-15-named-styles)**.
- **Mixing two styles = ugly.** Stick to one.
- **Pro Tip:** Name your reference (e.g., "This is Stripe meets Things 3").

### **🎨 Step 3 — Tokens First**

Edit `src/styles.css` **BEFORE** any component:

```css
/* Example: Editorial Calm Palette */
:root {
  --background: oklch(0.98 0.01 80);
  --foreground: oklch(0.18 0.02 80);
  --primary:    oklch(0.22 0.04 80);
  --accent:     oklch(0.62 0.15 30);
  
  /* Gradients */
  --gradient-hero: linear-gradient(135deg, var(--primary), var(--accent));
  
  /* Shadows */
  --shadow-sm: 0 1px 2px oklch(0 0 0 / 0.05);
  --shadow-elegant: 0 20px 50px -20px oklch(from var(--primary) l c h / 0.3);
  
  /* Fonts */
  --font-display: "Fraunces", ui-serif, Georgia, serif;
  --font-sans: "Inter", ui-sans-serif, system-ui, sans-serif;
  
  /* Spacing */
  --radius: 0.75rem;
}
```

### **🧩 Step 4 — Compose**

- Build sections **one at a time** using:
  - `shadcn` primitives (Button, Card, Input, etc.)
  - **CVA variants** (for reusable styles)
  - **Layout archetypes** from §6

### **✨ Step 5 — Polish**

- **Spacing rhythm:** Use the scale (never arbitrary values).
- **Hover states:** Subtle, single transform (e.g., `hover:scale-105`).
- **Focus rings:** Visible, on-brand (e.g., `focus-visible:ring-2`).
- **Loading states:** Skeleton or shimmer.
- **Empty states:** Illustrated + helpful CTA.
- **Signature moment:** One per page (e.g., hero animation, unique shape).

### **🔍 Step 6 — Audit**

- Run the **[40-point checklist](#)** (see Part 3).
- **Fix all issues before shipping.**

---

## **3. CHOOSING AN AESTHETIC DIRECTION (15+ Named Styles)**

### **🎨 How to Choose**

1. **Match your brand personality** (e.g., Luxe for high-end, Brutalist for bold).
2. **Consider your audience** (e.g., Modern Tech for devs, Soft Pastel for wellness).
3. **Pick one and commit.** Mixing styles = visual chaos.

### **📋 Aesthetic Directory**


| **Direction**         | **Mood**               | **Use For**                     | **Signatures**                                                  | **Font Pair**                 | **Color Palette Example**                          |
| --------------------- | ---------------------- | ------------------------------- | --------------------------------------------------------------- | ----------------------------- | -------------------------------------------------- |
| **Editorial Minimal** | Calm, slow, considered | Magazines, agencies, portfolios | Serif display, wide measure, whitespace, single accent          | Fraunces + Inter              | Beige + Ink (`oklch(0.98 0.01 80)`)                |
| **Modern Tech**       | Precise, fast          | SaaS, dev tools, AI             | Geist/Space Grotesk, dark mode primary, electric accent         | Geist + Inter                 | Dark blue + Electric blue (`oklch(0.14 0.02 250)`) |
| **Brutalist**         | Bold, loud, confident  | Indie tools, agencies           | Mono fonts, hard shadows, raw borders, oversized type           | Boldonse + IBM Plex Mono      | High-contrast black/white (`oklch(0.98 0 0)`)      |
| **Luxe / Premium**    | Quiet luxury           | Fashion, hospitality, finance   | Serif + sans, deep neutrals, gold/champagne accent, slow motion | Cormorant + Karla             | Champagne + Gold (`oklch(0.96 0.015 70)`)          |
| **Y2K / Vapor**       | Playful, nostalgic     | Creative tools, music, Gen-Z    | Iridescent gradients, chrome, pixel accents, blur orbs          | Tektur + DM Sans              | Pastel pink + Purple (`oklch(0.97 0.02 320)`)      |
| **Glass / Aurora**    | Ethereal, futuristic   | AI products, music apps         | Backdrop-blur, aurora gradients, soft glow, dark base           | Bricolage + Inter             | Dark purple + Aurora (`oklch(0.16 0.03 280)`)      |
| **Neo-Brutalist Pop** | Friendly chaos         | Indie SaaS, agencies            | Thick borders, hard shadows, primary colors, rotated cards      | Big Shoulders + IBM Plex Mono | Primary colors (`oklch(0.95 0.18 100)`)            |
| **Organic / Earthy**  | Warm, human            | Wellness, food, lifestyle       | Terracotta + sage, serif headlines, hand-feel imagery           | DM Serif + Lora               | Terracotta + Sage (`oklch(0.97 0.015 60)`)         |
| **Swiss / Grid**      | Rigorous, formal       | Architecture, design studios    | Helvetica/Inter, strict grid, black on off-white, captions      | Inter + JetBrains Mono        | Black + Off-white (`oklch(0.98 0 0)`)              |
| **Editorial Dark**    | Cinematic              | Music, film, agencies           | Black canvas, warm whites, single saturated accent, large type  | Abril Fatface + Lora          | Black + Warm white (`oklch(0.12 0.02 260)`)        |
| **Soft Pastel**       | Friendly, approachable | Consumer, kids, wellness        | Pastel palette, rounded everything, soft shadows, playful illos | Outfit + Nunito               | Pastel purple (`oklch(0.98 0.015 330)`)            |
| **Cyber / Neon**      | Energetic, future      | Gaming, web3, music             | Dark + neon mint/magenta, mono font, glow, scanlines            | Space Mono + DM Sans          | Dark + Neon (`oklch(0.12 0.02 260)`)               |
| **Apple Calm**        | Quiet confidence       | Productivity, hardware          | SF-like sans, off-white bg, subtle gradients, generous spacing  | Inter Tight + Inter           | Off-white (`oklch(0.99 0.003 250)`)                |
| **Magazine**          | Story-led              | Blogs, publishing               | Serif body, hero photography, drop caps, sidebars               | DM Serif + IBM Plex Serif     | Cream (`oklch(0.96 0.02 80)`)                      |
| **Bauhaus**           | Geometric, primary     | Studios, schools                | Primary colors, circles + squares, sans display                 | Inter + JetBrains Mono        | Primary colors (`oklch(0.98 0 0)`)                 |


---

## **4. COLOR THEORY WITH OKLCH (24 Ready Palettes + Custom Recipes)**

### **🎯 Why OKLCH?**

- **Perceptually uniform:** `L` (lightness) is *real* brightness (unlike RGB/HSL).
- **Chroma (C):** Saturation (clamp **0–0.37** for UI).
- **Hue (H):** 0–360° color wheel (consistent across lightness levels).
- **Accessibility:** Easier to hit **WCAG AA contrast ratios** (4.5:1 for text).

### **🔧 Building a Custom Palette (5-Minute Method)**

1. **Pick a hero hue** (e.g., your brand color’s `H` value).
  - *Example:* Brand color is `oklch(0.5 0.2 150)` → Hero hue = **150**.
2. **Build a neutral scale:**
  - Same `H` as hero, **low `C` (0.005–0.02)**, `L` from **0.99 → 0.08**.
  - *Example:* `oklch(0.99 0.01 150)` (lightest) to `oklch(0.08 0.01 150)` (darkest).
3. **Pick an accent hue:**
  - **120° or 180°** from hero hue (complementary).
  - *Example:* Hero hue = 150 → Accent hue = **150 + 120 = 270**.
4. **Destructive color:**
  - Use `oklch(0.55–0.62, 0.22, 25)` (red) for errors/warnings.
5. **Validate contrast:**
  - Body text **≥ 4.5:1** vs. background.
  - Use [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

### **🎨 24 Ready-to-Paste Palettes**

*(Copy-paste into `:root` in `styles.css`)*

#### **🌿 Earthy & Organic**

```css
/* 1. Terracotta & Sage */
--background: oklch(0.97 0.015 60);
--foreground: oklch(0.22 0.03 40);
--primary:    oklch(0.58 0.13 40);
--accent:     oklch(0.65 0.08 145);

/* 2. Forest Premium */
--background: oklch(0.97 0.01 145);
--foreground: oklch(0.18 0.04 145);
--primary:    oklch(0.32 0.08 145);
--accent:     oklch(0.70 0.14 75);

/* 3. Desert Clay */
--background: oklch(0.94 0.02 60);
--foreground: oklch(0.22 0.04 30);
--primary:    oklch(0.58 0.10 50);
--accent:     oklch(0.45 0.12 25);
```

#### **💎 Luxury & Premium**

```css
/* 4. Luxe Champagne */
--background: oklch(0.96 0.015 70);
--foreground: oklch(0.18 0.02 70);
--primary:    oklch(0.18 0.02 70);
--accent:     oklch(0.72 0.12 75);

/* 5. Emerald Prestige */
--background: oklch(0.97 0.01 150);
--foreground: oklch(0.18 0.04 150);
--primary:    oklch(0.40 0.12 150);
--accent:     oklch(0.72 0.12 90);

/* 6. Navy Trust */
--background: oklch(0.98 0.005 250);
--foreground: oklch(0.18 0.04 250);
--primary:    oklch(0.28 0.10 250);
--accent:     oklch(0.65 0.16 220);
```

#### **🌌 Modern & Tech**

```css
/* 7. Modern Dark Tech */
--background: oklch(0.14 0.02 250);
--foreground: oklch(0.96 0.005 250);
--primary:    oklch(0.72 0.18 250);
--accent:     oklch(0.78 0.20 160);

/* 8. Cyber Neon */
--background: oklch(0.12 0.02 260);
--foreground: oklch(0.96 0.01 160);
--primary:    oklch(0.82 0.20 160);
--accent:     oklch(0.72 0.24 320);

/* 9. Slate Enterprise */
--background: oklch(0.98 0.005 240);
--foreground: oklch(0.22 0.02 240);
--primary:    oklch(0.35 0.04 240);
--accent:     oklch(0.62 0.16 220);
```

#### **🎨 Creative & Playful**

```css
/* 10. Y2K Vapor */
--background: oklch(0.97 0.02 320);
--foreground: oklch(0.22 0.04 290);
--primary:    oklch(0.72 0.18 320);
--accent:     oklch(0.80 0.16 200);

/* 11. Aurora Glass (dark) */
--background: oklch(0.16 0.03 280);
--foreground: oklch(0.96 0.01 280);
--primary:    oklch(0.74 0.18 290);
--accent:     oklch(0.78 0.18 180);

/* 12. Soft Pastel */
--background: oklch(0.98 0.015 330);
--foreground: oklch(0.30 0.03 330);
--primary:    oklch(0.72 0.10 330);
--accent:     oklch(0.78 0.10 200);
```

#### **📰 Editorial & Classic**

```css
/* 13. Editorial Calm */
--background: oklch(0.98 0.01 80);
--foreground: oklch(0.18 0.02 80);
--primary:    oklch(0.22 0.04 80);
--accent:     oklch(0.62 0.15 30);

/* 14. Magazine Cream */
--background: oklch(0.96 0.02 80);
--foreground: oklch(0.15 0.02 30);
--primary:    oklch(0.20 0.03 30);
--accent:     oklch(0.55 0.22 25);

/* 15. Apple Calm */
--background: oklch(0.99 0.003 250);
--foreground: oklch(0.18 0.01 250);
--primary:    oklch(0.55 0.18 255);
--accent:     oklch(0.65 0.12 200);
```

#### **⚡ Bold & High-Contrast**

```css
/* 16. Brutalist High-Contrast */
--background: oklch(0.98 0 0);
--foreground: oklch(0.12 0 0);
--primary:    oklch(0.12 0 0);
--accent:     oklch(0.68 0.24 25);

/* 17. Crimson Editorial */
--background: oklch(0.97 0.01 30);
--foreground: oklch(0.15 0.02 30);
--primary:    oklch(0.40 0.18 25);
--accent:     oklch(0.70 0.14 60);

/* 18. Coral Energy */
--background: oklch(0.98 0.01 20);
--foreground: oklch(0.20 0.04 20);
--primary:    oklch(0.65 0.20 25);
--accent:     oklch(0.55 0.20 290);

/* 19. Midnight Indigo */
--background: oklch(0.13 0.04 280);
--foreground: oklch(0.96 0.01 280);
--primary:    oklch(0.62 0.20 280);
--accent:     oklch(0.78 0.16 200);

/* 20. Brutalist Yellow */
--background: oklch(0.95 0.18 100);
--foreground: oklch(0.12 0 0);
--primary:    oklch(0.12 0 0);
--accent:     oklch(0.55 0.24 25);
```

#### **🌅 Gradient & Sunset**

```css
/* 21. Sunset Gradient */
--background: oklch(0.97 0.02 50);
--foreground: oklch(0.20 0.04 30);
--primary:    oklch(0.68 0.20 30);
--accent:     oklch(0.72 0.18 350);

/* 22. Ocean Deep */
--background: oklch(0.98 0.01 220);
--foreground: oklch(0.18 0.04 220);
--primary:    oklch(0.42 0.14 220);
--accent:     oklch(0.72 0.14 195);

/* 23. Glacier */
--background: oklch(0.97 0.01 220);
--foreground: oklch(0.20 0.03 240);
--primary:    oklch(0.50 0.08 220);
--accent:     oklch(0.75 0.10 200);

/* 24. Mono Studio (warm gray) */
--background: oklch(0.97 0.005 60);
--foreground: oklch(0.20 0.005 60);
--primary:    oklch(0.30 0.005 60);
--accent:     oklch(0.65 0.18 50);
```

### **🌈 Gradient Recipes (OKLCH-Safe)**

```css
/* Hero Gradient */
--gradient-hero: linear-gradient(135deg, oklch(0.72 0.18 290), oklch(0.78 0.18 200));

/* Aurora Gradient */
--gradient-aurora: linear-gradient(
  120deg,
  oklch(0.68 0.20 290) 0%,
  oklch(0.72 0.18 200) 50%,
  oklch(0.78 0.16 160) 100%
);

/* Sunset Gradient */
--gradient-sunset: linear-gradient(
  135deg,
  oklch(0.72 0.20 50),
  oklch(0.65 0.22 20),
  oklch(0.55 0.20 340)
);

/* Mesh Gradient (for 3D backgrounds) */
--gradient-mesh: 
  radial-gradient(at 20% 20%, oklch(0.72 0.18 290 / 0.5), transparent 50%),
  radial-gradient(at 80% 30%, oklch(0.78 0.18 200 / 0.5), transparent 50%),
  radial-gradient(at 50% 90%, oklch(0.74 0.16 340 / 0.4), transparent 50%);

/* Subtle Gradient (for cards) */
--gradient-subtle: linear-gradient(
  180deg,
  var(--background),
  oklch(from var(--background) calc(l - 0.02) c h)
);
```

### **🖤 Shadow Recipes**

```css
--shadow-sm:      0 1px 2px oklch(0 0 0 / 0.05);
--shadow-md:      0 4px 12px oklch(0 0 0 / 0.08);
--shadow-lg:      0 10px 25px -5px oklch(0 0 0 / 0.1);
--shadow-elegant: 0 20px 50px -20px oklch(from var(--primary) l c h / 0.3);
--shadow-glow:    0 0 60px oklch(from var(--accent) l c h / 0.4);
--shadow-brutal:  6px 6px 0 0 var(--foreground);
--shadow-inset:   inset 0 1px 0 0 oklch(1 0 0 / 0.06);
```

---

## **5. TYPOGRAPHY (Font Pairs, Scales, Hierarchy)**

### **🔤 Font Pair Library**

*(Pair display + body fonts for each aesthetic)*


| **Aesthetic**         | **Display**                | **Body**             | **Mono**       | **Use Case**                    |
| --------------------- | -------------------------- | -------------------- | -------------- | ------------------------------- |
| **Editorial Minimal** | Fraunces, Instrument Serif | Inter, Geist         | JetBrains Mono | Magazines, portfolios, agencies |
| **Modern Tech**       | Geist, Space Grotesk       | Geist, Inter         | Geist Mono     | SaaS, dev tools, AI             |
| **Luxe**              | Cormorant, Playfair        | Karla, Inter         | —              | Fashion, hospitality, finance   |
| **Brutalist**         | Boldonse, Big Shoulders    | IBM Plex Mono        | IBM Plex Mono  | Indie tools, bold statements    |
| **Y2K / Vapor**       | Tektur, Pixelify Sans      | DM Sans              | Space Mono     | Creative tools, Gen-Z           |
| **Glass / Aurora**    | Bricolage Grotesque        | Inter                | Geist Mono     | AI products, futuristic apps    |
| **Magazine**          | DM Serif Display           | Lora, IBM Plex Serif | —              | Blogs, publishing               |
| **Soft Pastel**       | Outfit, Sora               | DM Sans, Nunito      | —              | Consumer, kids, wellness        |
| **Apple Calm**        | Inter Tight                | Inter                | Geist Mono     | Productivity, hardware          |
| **Swiss Grid**        | Inter (tracking-tight)     | Inter                | JetBrains Mono | Architecture, design studios    |


### **📏 Modular Scale (rem)**

*(Use for consistent typography sizing)*


| **Size** | **Value (rem)** | **Use Case**            | **Example**                         |
| -------- | --------------- | ----------------------- | ----------------------------------- |
| `xs`     | 0.75            | Captions, labels        | `<p class="text-xs">`               |
| `sm`     | 0.875           | Buttons, badges         | `<Button size="sm">`                |
| `base`   | 1               | Body text               | `<p class="text-base">`             |
| `lg`     | 1.125           | Subheadings (h4)        | `<h4 class="text-lg">`              |
| `xl`     | 1.25            | Headings (h3)           | `<h3 class="text-xl">`              |
| `2xl`    | 1.5             | Headings (h2)           | `<h2 class="text-2xl">`             |
| `3xl`    | 1.875           | Hero subheadings        | `<h1 class="text-3xl md:text-4xl">` |
| `4xl`    | 2.25            | Hero headings (mobile)  | `<h1 class="text-4xl">`             |
| `5xl`    | 3               | Hero headings (desktop) | `<h1 class="text-5xl">`             |
| `6xl`    | 3.75            | Mega headings           | `<h1 class="text-6xl">`             |
| `7xl`    | 4.5             | Display text            | `<h1 class="text-7xl">`             |


### **📜 Typography Rules**

1. **One `<h1>` per page.** No exceptions.
2. **Hierarchy:** Use **size + weight**, never color alone.
3. **Body line-height:** **1.5–1.7** (e.g., `leading-6` or `leading-7`).
4. **Headline line-height:** **1.0–1.15** (e.g., `leading-none` or `leading-tight`).
5. **Measure (max width):**
  - **Prose:** ≤ **70ch** (use `max-w-prose`).
  - **Headlines:** ≤ **12ch** per line.
6. **Tracking:**
  - `tracking-tight` for **display text ≥ 4xl**.
  - `tracking-tighter` for **≥ 7xl**.
7. **Eyebrows (metadata):**
  ```html
   <p class="text-xs uppercase tracking-widest text-muted-foreground">New · v2.0</p>
  ```
8. **Drop Caps (Editorial):**
  ```html
   <p class="first-letter:text-7xl first-letter:font-display first-letter:float-left first-letter:mr-3 first-letter:mt-1">...</p>
  ```
9. **Text Balance:**
  - `text-balance` for **headlines** (auto-wrap long words).
  - `text-pretty` for **paragraphs** (better line breaks).

### **🔗 Loading Fonts (Canonical Pattern)**

In `src/routes/__root.tsx` (or equivalent):

```tsx
<head>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossOrigin="anonymous" />
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300..900&family=Inter:wght@400;500;600;700&display=swap"
  />
</head>
```

In `src/styles.css`:

```css
@theme inline {
  --font-display: "Fraunces", ui-serif, Georgia, serif;
  --font-sans: "Inter", ui-sans-serif, system-ui, sans-serif;
  --font-mono: "JetBrains Mono", ui-monospace, monospace;
}
```

---

## **6. SPACING, RHYTHM & LAYOUT ARCHETYPES**

### **📏 Spacing Scale**

*(Tailwind’s default scale — **no arbitrary values**!)*


| **Value** | **Use Case**               | **Example**         |
| --------- | -------------------------- | ------------------- |
| 0         | Reset                      | `m-0`, `p-0`        |
| 0.5       | Tight gaps                 | `gap-0.5`, `px-0.5` |
| 1         | Small padding              | `p-1`, `m-1`        |
| 1.5       | Compact elements           | `gap-1.5`, `py-1.5` |
| 2         | Default padding            | `p-2`, `m-2`        |
| 3         | Medium padding             | `p-3`, `gap-3`      |
| 4         | Large padding              | `p-4`, `m-4`        |
| 5         | Extra-large padding        | `p-5`               |
| 6         | Card padding (mobile)      | `p-6`               |
| 8         | Card padding (desktop)     | `p-8`               |
| 10        | Section gaps               | `py-10`             |
| 12        | Wide gaps                  | `gap-12`, `my-12`   |
| 16        | Large sections             | `py-16`             |
| 20        | Section vertical rhythm    | `py-20`             |
| 24        | Hero sections              | `py-24`             |
| 32        | Alternating section rhythm | `py-32`             |
| 40        | Tall sections              | `py-40`             |
| 48        | Extra-tall sections        | `py-48`             |
| 64        | Massive spacing            | `py-64`             |


### **🏗️ Common Spacing Patterns**


| **Element**            | **Spacing**                              | **Example**                |
| ---------------------- | ---------------------------------------- | -------------------------- |
| Button (sm)            | `px-4 py-2`                              | `<Button size="sm">`       |
| Button (md)            | `px-6 py-3`                              | `<Button size="md">`       |
| Button (lg)            | `px-8 py-4`                              | `<Button size="lg">`       |
| Card padding (mobile)  | `p-6`                                    | `<Card class="p-6">`       |
| Card padding (desktop) | `p-8`                                    | `<Card class="p-8">`       |
| Section rhythm         | `py-20` or `py-32`                       | `<section class="py-20">`  |
| Container              | `mx-auto max-w-7xl px-4 sm:px-6 lg:px-8` | `<div class="container">`  |
| Stack inside card      | `space-y-3`                              | `<div class="space-y-3">`  |
| Grid gap               | `gap-6` or `gap-8`                       | `<div class="grid gap-6">` |


### **🎨 Layout Archetypes**

*(Copy-paste these patterns for consistent layouts)*

#### **A. Bento Grid (Feature Showcase)**

```tsx
<div className="grid grid-cols-1 md:grid-cols-6 gap-4 md:gap-6">
  <Card className="md:col-span-4 md:row-span-2 p-8">
    {/* Hero feature */}
  </Card>
  <Card className="md:col-span-2 p-6">
    {/* Side feature */}
  </Card>
  <Card className="md:col-span-2 p-6">
    {/* Side feature */}
  </Card>
  <Card className="md:col-span-3 p-6">
    {/* Wide feature */}
  </Card>
  <Card className="md:col-span-3 p-6">
    {/* Wide feature */}
  </Card>
</div>
```

**When to use:** Feature pages, dashboards, asymmetric designs.

#### **B. Editorial Split (60/40 with Offset)**

```tsx
<div className="grid md:grid-cols-12 gap-12 items-center">
  <div className="md:col-span-7 md:col-start-1">
    {/* Text content */}
  </div>
  <div className="md:col-span-4 md:col-start-9">
    {/* Image or visual */}
  </div>
</div>
```

**When to use:** Hero sections, feature highlights, storytelling.

#### **C. Magazine Layout**

- **Wide hero photo** (16:9 or 21:9 aspect ratio).
- **3-column sidebar text** (for metadata, related links).
- **Drop caps** for the first paragraph.

**Example:**

```tsx
<div className="container mx-auto px-4 py-24">
  <img src="/hero.jpg" className="w-full h-auto mb-8" alt="Hero" />
  <div className="grid md:grid-cols-4 gap-8">
    <div className="md:col-span-3">
      <h1 className="text-4xl md:text-5xl">Article Title</h1>
      <p className="first-letter:text-7xl first-letter:font-display first-letter:float-left first-letter:mr-3 first-letter:mt-1">
        Lorem ipsum dolor sit amet...
      </p>
    </div>
    <aside className="md:col-span-1">
      <p class="text-xs uppercase tracking-widest text-muted-foreground">Category</p>
      <p class="text-sm">Author: Jane Doe</p>
      <p class="text-sm">Date: June 2026</p>
    </aside>
  </div>
</div>
```

#### **D. Zigzag Layout**

```tsx
<div className="space-y-24">
  <div className="grid md:grid-cols-2 gap-12 items-center">
    <div>{/* Text */}</div>
    <div>{/* Image */}</div>
  </div>
  <div className="grid md:grid-cols-2 gap-12 items-center md:flex-row-reverse">
    <div>{/* Text */}</div>
    <div>{/* Image */}</div>
  </div>
  <div className="grid md:grid-cols-2 gap-12 items-center">
    <div>{/* Text */}</div>
    <div>{/* Image */}</div>
  </div>
</div>
```

**When to use:** Storytelling, product tours, alternating content.

#### **E. Card Grid (Equal)**

```tsx
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
  <Card className="p-6"> {/* Item 1 */} </Card>
  <Card className="p-6"> {/* Item 2 */} </Card>
  <Card className="p-6"> {/* Item 3 */} </Card>
</div>
```

**When to use:** Logos, team members, galleries, equal-height items.

#### **F. Sidebar Dashboard**

```tsx
<div className="grid grid-cols-1 lg:grid-cols-[240px_1fr] min-h-screen">
  <aside className="border-r p-6">
    {/* Left navigation */}
  </aside>
  <main className="p-6">
    {/* Main content */}
  </main>
</div>
```

**When to use:** Admin panels, SaaS dashboards, multi-page apps.

#### **G. Full-Bleed Cinema**

```tsx
<section className="min-h-screen flex items-center justify-center">
  <h1 className="text-6xl md:text-8xl font-bold text-center">
    One Statement Per Screen
  </h1>
</section>
```

**When to use:** Landing pages, hero sections, storytelling.

#### **H. Asymmetric Off-Grid**

```tsx
<div className="space-y-6">
  <Card className="p-6 transform rotate-1 translate-x-2">
    {/* Card 1 */}
  </Card>
  <Card className="p-6 transform -rotate-1 -translate-x-2">
    {/* Card 2 */}
  </Card>
  <Card className="p-6 transform translate-y-4">
    {/* Card 3 */}
  </Card>
</div>
```

**When to use:** Modern, playful, or artistic designs.

### **📱 Container Queries (Responsive Components)**

*(For components that adapt to their container width, not the viewport)*

```css
.card-grid {
  container-type: inline-size;
}

@container (min-width: 600px) {
  .card {
    grid-template-columns: 1fr 1fr;
  }
}
```

**Example in React:**

```tsx
<div className="card-grid">
  <Card className="card">
    {/* Content */}
  </Card>
</div>
```

---

## **7. SHADCN + CVA — COMPOSITION PATTERNS (Code)**

### **🔧 Why shadcn + CVA?**

- **shadcn**: Radix-based, accessible, unstyled components.
- **CVA (Class Variance Authority)**: Type-safe variants for Tailwind.
- **Result**: Reusable, themeable, and maintainable components.

### **📁 File Structure**

```
src/
└── components/
    └── ui/
        ├── button.tsx
        ├── card.tsx
        ├── badge.tsx
        └── ...
```

### **✨ Button Component (Extended with Variants)**

```tsx
// src/components/ui/button.tsx
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";

const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium transition-all duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90 shadow-sm",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline: "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        secondary: "bg-secondary text-secondary-foreground hover:bg-secondary/80",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",
        // Custom variants
        hero: "bg-[image:var(--gradient-hero)] text-primary-foreground shadow-[var(--shadow-elegant)] hover:scale-105 hover:shadow-[var(--shadow-glow)]",
        glass: "backdrop-blur-md bg-white/10 border border-white/20 text-foreground hover:bg-white/20",
        brutal: "bg-primary text-primary-foreground border-2 border-foreground shadow-[var(--shadow-brutal)] hover:translate-x-1 hover:translate-y-1 hover:shadow-none",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 px-3",
        lg: "h-12 px-8 text-base",
        xl: "h-14 px-10 text-lg",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
);

export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean;
}

const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    const Comp = asChild ? Slot : "button";
    return (
      <Comp
        className={cn(buttonVariants({ variant, size, className }))}
        ref={ref}
        {...props}
      />
    );
  }
);
Button.displayName = "Button";

export { Button, buttonVariants };
```

### **🪟 Card Component (Extended with Variants)**

```tsx
// src/components/ui/card.tsx
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";

const cardVariants = cva(
  "rounded-xl bg-card text-card-foreground transition-all duration-200",
  {
    variants: {
      variant: {
        default: "border shadow-sm",
        elevated: "border shadow-[var(--shadow-elegant)] hover:-translate-y-1 hover:shadow-[var(--shadow-glow)]",
        glass: "backdrop-blur-xl bg-white/5 border border-white/10",
        brutal: "border-2 border-foreground shadow-[var(--shadow-brutal)]",
        ghost: "border-transparent shadow-none",
      },
    },
    defaultVariants: {
      variant: "default",
    },
  }
);

export interface CardProps
  extends React.HTMLAttributes<HTMLDivElement>,
    VariantProps<typeof cardVariants> {}

function Card({ className, variant, ...props }: CardProps) {
  return (
    <div className={cn(cardVariants({ variant, className }))} {...props} />
  );
}

export { Card, cardVariants };
```

### **🏷️ Badge Component (Extended with Variants)**

```tsx
// src/components/ui/badge.tsx
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";

const badgeVariants = cva(
  "inline-flex items-center rounded-full px-3 py-1 text-xs font-medium",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground",
        secondary: "bg-secondary text-secondary-foreground",
        destructive: "bg-destructive text-destructive-foreground",
        outline: "border border-border text-foreground",
        soft: "bg-accent/10 text-accent border border-accent/20",
        gradient: "bg-[image:var(--gradient-hero)] text-primary-foreground",
      },
    },
    defaultVariants: {
      variant: "default",
    },
  }
);

export interface BadgeProps
  extends React.HTMLAttributes<HTMLDivElement>,
    VariantProps<typeof badgeVariants> {}

function Badge({ className, variant, ...props }: BadgeProps) {
  return (
    <div className={cn(badgeVariants({ variant, className }))} {...props} />
  );
}

export { Badge, badgeVariants };
```

### **📦 Input Component (Extended with Variants)**

```tsx
// src/components/ui/input.tsx
import { cva, type VariantProps } from "class-variance-authority";
import { cn } from "@/lib/utils";

const inputVariants = cva(
  "flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50",
  {
    variants: {
      variant: {
        default: "",
        ghost: "border-0 focus-visible:ring-0",
        glass: "backdrop-blur-md bg-white/10 border border-white/20",
      },
    },
    defaultVariants: {
      variant: "default",
    },
  }
);

export interface InputProps
  extends React.InputHTMLAttributes<HTMLInputElement>,
    VariantProps<typeof inputVariants> {}

const Input = React.forwardRef<HTMLInputElement, InputProps>(
  ({ className, variant, type, ...props }, ref) => {
    return (
      <input
        type={type}
        className={cn(inputVariants({ variant, className }))}
        ref={ref}
        {...props}
      />
    );
  }
);
Input.displayName = "Input";

export { Input, inputVariants };
```

---

## **8. SECTION RECIPES (Paste-and-Edit)**

### **🌌 Hero — Editorial Calm**

*(Minimalist, serif typography, generous whitespace)*

```tsx
<section className="container mx-auto px-4 py-24 md:py-40">
  <div className="max-w-4xl">
    {/* Eyebrow */}
    <p className="mb-6 text-xs uppercase tracking-widest text-muted-foreground">
      New · v2.0
    </p>
    
    {/* Headline */}
    <h1 className="font-display text-5xl md:text-7xl lg:text-8xl leading-[1.05] tracking-tight text-balance">
      A quieter way to <em className="italic text-accent">ship</em> software.
    </h1>
    
    {/* Subheadline */}
    <p className="mt-8 max-w-xl text-lg md:text-xl text-muted-foreground text-pretty">
      One sentence that promises a concrete outcome — not what the product is, but what changes for the user.
    </p>
    
    {/* CTA */}
    <div className="mt-10 flex flex-wrap gap-3">
      <Button variant="hero" size="lg">Start free</Button>
      <Button variant="ghost" size="lg">
        See how it works →
      </Button>
    </div>
  </div>
</section>
```

### **⚡ Hero — Bold Tech with Glow**

*(Modern, dark mode, electric accents, mesh gradient background)*

```tsx
<section className="relative overflow-hidden bg-background py-32">
  {/* Background Gradient */}
  <div className="absolute inset-0 bg-[image:var(--gradient-mesh)] opacity-50" />
  
  <div className="container relative mx-auto px-4 text-center">
    {/* Badge */}
    <Badge variant="soft" className="mb-6">
      ⚡ Now in public beta
    </Badge>
    
    {/* Headline */}
    <h1 className="mx-auto max-w-4xl font-display text-6xl md:text-8xl font-bold tracking-tighter text-balance">
      Build at the speed of thought.
    </h1>
    
    {/* Subheadline */}
    <p className="mx-auto mt-6 max-w-2xl text-lg text-muted-foreground">
      A short sub-headline that earns the click.
    </p>
    
    {/* CTA */}
    <div className="mt-10 flex justify-center gap-3">
      <Button variant="hero" size="xl">Get started free</Button>
      <Button variant="outline" size="xl">
        <PlayIcon className="mr-2 h-4 w-4" />
        Live demo
      </Button>
    </div>
  </div>
</section>
```

### **🧩 Feature Bento**

*(Asymmetric grid for feature showcase)*

```tsx
<section className="container mx-auto px-4 py-24">
  {/* Section Header */}
  <div className="mb-16 max-w-2xl">
    <p className="text-xs uppercase tracking-widest text-muted-foreground mb-4">
      Features
    </p>
    <h2 className="font-display text-4xl md:text-5xl tracking-tight">
      Everything you need. Nothing you don't.
    </h2>
  </div>
  
  {/* Bento Grid */}
  <div className="grid md:grid-cols-6 gap-4">
    <Card variant="elevated" className="md:col-span-4 md:row-span-2 p-10">
      <h3 className="text-2xl font-semibold">Big idea here</h3>
      <p className="mt-3 text-muted-foreground">
        Lead with the headline feature. Pair with a generated illustration.
      </p>
    </Card>
    <Card variant="elevated" className="md:col-span-2 p-6">
      <h4 className="text-lg font-semibold">Feature 1</h4>
      <p className="mt-2 text-sm text-muted-foreground">
        Short description.
      </p>
    </Card>
    <Card variant="elevated" className="md:col-span-2 p-6">
      <h4 className="text-lg font-semibold">Feature 2</h4>
      <p className="mt-2 text-sm text-muted-foreground">
        Short description.
      </p>
    </Card>
    <Card variant="elevated" className="md:col-span-3 p-6">
      <h4 className="text-lg font-semibold">Feature 3</h4>
      <p className="mt-2 text-sm text-muted-foreground">
        Short description.
      </p>
    </Card>
    <Card variant="elevated" className="md:col-span-3 p-6">
      <h4 className="text-lg font-semibold">Feature 4</h4>
      <p className="mt-2 text-sm text-muted-foreground">
        Short description.
      </p>
    </Card>
  </div>
</section>
```

### **💰 Pricing — 3 Tiers, Middle Highlighted**

*(Modern SaaS pricing table)*

```tsx
<section className="container mx-auto px-4 py-24">
  <div className="grid md:grid-cols-3 gap-6 md:gap-4 max-w-5xl mx-auto items-stretch">
    {[
      {
        name: "Starter",
        price: "9",
        features: ["Feature 1", "Feature 2", "Feature 3"],
        popular: false,
      },
      {
        name: "Pro",
        price: "29",
        features: ["Everything in Starter", "Feature 4", "Feature 5", "Feature 6"],
        popular: true,
      },
      {
        name: "Enterprise",
        price: "99",
        features: ["Everything in Pro", "Dedicated Support", "Custom Integrations"],
        popular: false,
      },
    ].map((tier, i) => (
      <Card
        key={tier.name}
        variant={tier.popular ? "elevated" : "default"}
        className={cn(
          "p-8 flex flex-col",
          tier.popular && "md:scale-105 border-primary"
        )}
      >
        {tier.popular && (
          <Badge variant="gradient" className="self-start mb-4">
            Most popular
          </Badge>
        )}
        <h3 className="text-xl font-semibold">{tier.name}</h3>
        <div className="my-6">
          <span className="text-5xl font-display tracking-tight">${tier.price}</span>
          <span className="text-muted-foreground">/mo</span>
        </div>
        <ul className="space-y-3 text-sm flex-1">
          {tier.features.map((feature) => (
            <li key={feature} className="flex gap-2">
              <Check className="w-4 h-4 text-accent shrink-0 mt-0.5" />
              {feature}
            </li>
          ))}
        </ul>
        <Button
          variant={tier.popular ? "hero" : "outline"}
          size="lg"
          className="mt-8 w-full"
        >
          Choose {tier.name}
        </Button>
      </Card>
    ))}
  </div>
</section>
```

### **🎯 CTA Band**

*(Full-width call-to-action with gradient background)*

```tsx
<section className="relative overflow-hidden">
  <div className="absolute inset-0 bg-[image:var(--gradient-hero)]" />
  <div className="container relative mx-auto px-4 py-24 text-center text-primary-foreground">
    <h2 className="font-display text-4xl md:text-6xl tracking-tight max-w-3xl mx-auto text-balance">
      Stop reading. Start shipping.
    </h2>
    <Button variant="glass" size="xl" className="mt-10">
      Create your account
    </Button>
  </div>
</section>
```

### **👣 Footer**

*(Multi-column footer with logo, links, and copyright)*

```tsx
<footer className="border-t bg-card">
  <div className="container mx-auto px-4 py-16 grid gap-12 md:grid-cols-5">
    {/* Logo + Description */}
    <div className="md:col-span-2">
      <Logo className="h-8 w-8 mb-4" />
      <p className="mt-4 text-sm text-muted-foreground max-w-xs">
        One-line product description.
      </p>
    </div>
    
    {/* Footer Columns */}
    {[
      {
        title: "Product",
        links: [
          { label: "Features", href: "/features" },
          { label: "Pricing", href: "/pricing" },
          { label: "Docs", href: "/docs" },
        ],
      },
      {
        title: "Company",
        links: [
          { label: "About", href: "/about" },
          { label: "Blog", href: "/blog" },
          { label: "Careers", href: "/careers" },
        ],
      },
      {
        title: "Legal",
        links: [
          { label: "Privacy", href: "/privacy" },
          { label: "Terms", href: "/terms" },
          { label: "Cookie Policy", href: "/cookies" },
        ],
      },
    ].map((col) => (
      <div key={col.title}>
        <h4 className="text-xs uppercase tracking-widest text-muted-foreground mb-4">
          {col.title}
        </h4>
        <ul className="space-y-3 text-sm">
          {col.links.map((link) => (
            <li key={link.href}>
              <Link
                to={link.href}
                className="hover:text-accent transition-colors"
              >
                {link.label}
              </Link>
            </li>
          ))}
        </ul>
      </div>
    ))}
  </div>
  
  {/* Copyright */}
  <div className="border-t">
    <div className="container mx-auto px-4 py-6 flex justify-between text-xs text-muted-foreground">
      <span>© 2026 Brand</span>
      <span>Made with care.</span>
    </div>
  </div>
</footer>
```
