---
title: "UI/UX PRO MAX — The Lovable Design Bible"
description: "Core Design System & Foundations"
---

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


| **Direction**         | **Mood**               | **Use For**                     | **Signatures**                                                  | **Font Pair**                 | **Color Pale[...]`
