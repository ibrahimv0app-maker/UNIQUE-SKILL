

World-Class UI/UX System: Landing Pages, Dashboards, SaaS, Brand Identity, Design Systems, and More



📜 TABLE OF CONTENTS (Enhanced)





The Lovable Stack — Hard Rules



The 6-Step Design Ritual



Choosing An Aesthetic Direction (15+ Named Styles)



Color Theory with OKLCH (24 Ready Palettes + Custom Recipes)



Typography (Font Pairs, Scales, Hierarchy)



Spacing, Rhythm & Layout Archetypes



shadcn + CVA — Composition Patterns (Code)



Hero, Pricing, Feature, CTA, Footer Recipes



Motion System (CSS + Framer Motion + 3D Animation)



Accessibility (WCAG AA, Focus, ARIA)



SEO & Metadata Per Route



Image & Asset Direction



Copywriting Voice & Microcopy



Forms, Empty States, Errors, Loading



Dark Mode Strategy



The Bootstrap Recipe (Paste-Ready)



Pre-Ship Quality Audit (40 Checks)



Anti-Patterns — Banned List



Reference Galleries



3D Animation & Interactive Elements



Slides & Presentation Design



🎯 MANIFESTO

Mantra:
Tokens before components. Variants before classNames. References before "vibes". Restraint before features. No purple gradients on white.

Mission:
Ship interfaces that win Awwwards, not look like another v0 demo. Every pixel, animation, and word must earn its place.



1. THE LOVABLE STACK — HARD RULES







Constraint



Rule



Why?





Tailwind



v4, configured in src/styles.css via @import "tailwindcss" + @theme inline.



No tailwind.config.js. Keep it lean.





Colors



oklch(L C H) only. Never text-white, bg-black, bg-[#hex], or inline RGB.



Perceptually uniform, future-proof.





Components



shadcn lives in src/components/ui/*. Extend via CVA variants, never ad-hoc classNames.



Consistency, scalability, and theming.





Fonts



Load with <link> in src/routes/__root.tsx head. Never @import a remote URL in CSS.



Lightning CSS compatibility.





Custom Utilities



Use @utility name { ... }, not @layer utilities.



Cleaner, more maintainable.





Variants



@custom-variant dark (&:is(.dark *)); already wired.



Built-in dark mode support.





Tokens



New token? Add to :root, register in @theme inline as --color-<n>: var(--<n>);.



Centralized control.





Routing



TanStack Start — every section in its own route file under src/routes/.



Modular, scalable.





3D & Animations



Use Three.js, Framer Motion 3D, or Spline for 3D. Always optimize for performance.



Modern, immersive experiences.



🚨 If you write className="bg-white text-black", STOP. Extend the design system instead.



2. THE 6-STEP DESIGN RITUAL

Run in order. Never skip. Never inline. Never improvise.

Step 1 — Discover

Answer these out loud before writing code:





What is this? (Product category + one-liner)



Who uses it? (The realest possible user)



What should it feel like? (One adjective + one reference)

Example:
"A pricing page for a calm to-do app, used by indie makers, that feels like Things 3 — quiet, precise, generous whitespace."

Step 2 — Commit a Direction

Pick one aesthetic from §3 and stick to it. Mixing two styles = ugly.

Step 3 — Tokens First

Edit src/styles.css BEFORE any component:





Color tokens (oklch)



Gradient tokens (--gradient-*)



Shadow tokens (--shadow-*)



Font family tokens (--font-*)



Radius (--radius)



Custom transition tokens (--transition-smooth)

Step 4 — Compose

Build sections from:





shadcn primitives



CVA variants



3D components (if applicable)



Slide templates (for presentations)

Step 5 — Polish





Spacing rhythm (use scale, never arbitrary)



Hover states (subtle, single transform)



Focus rings (visible, on-brand)



Loading states (Skeleton or shimmer)



Empty states (illustrated, helpful)



One signature moment (hero animation, 3D element, gradient text, unique shape)

Step 6 — Audit

Run the 40-point checklist. Don’t skip.



3. CHOOSING AN AESTHETIC DIRECTION (15+ Named Styles)







Direction



Mood



Use For



Signatures



3D/Animation Potential





Editorial Minimal



Calm, slow, considered



Magazines, agencies, portfolios



Serif display, wide measure, whitespace, single accent



Subtle parallax, fade-in text, minimal 3D typography.





Modern Tech



Precise, fast



SaaS, dev tools, AI



Geist/Space Grotesk, dark mode primary, electric accent



Holographic UI elements, floating 3D panels, particle effects.





Brutalist



Bold, loud, confident



Indie tools, agencies



Mono fonts, hard shadows, raw borders, oversized type



Glitch effects, brutalist 3D geometry, sharp transitions.





Luxe / Premium



Quiet luxury



Fashion, hospitality, finance



Serif + sans, deep neutrals, gold/champagne accent, slow motion



Gold foil shaders, cloth simulation, elegant camera movements.





Y2K / Vapor



Playful, nostalgic



Creative tools, music, Gen-Z



Iridescent gradients, chrome, pixel accents, blur orbs



Retro 3D shapes, VHS glitch, neon wireframes.





Glass / Aurora



Ethereal, futuristic



AI products, music apps



Backdrop-blur, aurora gradients, soft glow, dark base



Floating glass orbs, dynamic light refraction, aurora particle systems.





Neo-Brutalist Pop



Friendly chaos



Indie SaaS, agencies



Thick borders, hard shadows, primary colors, rotated cards



Playful 3D collisions, bouncy physics, exaggerated shadows.





Organic / Earthy



Warm, human



Wellness, food, lifestyle



Terracotta + sage, serif headlines, hand-feel imagery



Organic 3D shapes, fluid simulations, nature-inspired motion.





Swiss / Grid



Rigorous, formal



Architecture, design studios



Helvetica/Inter, strict grid, black on off-white, captions



Geometric 3D grids, precise camera angles, minimal animation.





Editorial Dark



Cinematic



Music, film, agencies



Black canvas, warm whites, single saturated accent, large type



Depth-of-field 3D, cinematic lighting, slow zooms.





Soft Pastel



Friendly, approachable



Consumer, kids, wellness



Pastel palette, rounded everything, soft shadows, playful illos



Squishy 3D, pastel shaders, bouncy interactions.





Cyber / Neon



Energetic, future



Gaming, web3, music



Dark + neon mint/magenta, mono font, glow, scanlines



Cyberpunk 3D, neon wireframes, data stream effects.





Apple Calm



Quiet confidence



Productivity, hardware



SF-like sans, off-white bg, subtle gradients, generous spacing



Subtle 3D depth, soft shadows, smooth transitions.





Magazine



Story-led



Blogs, publishing



Serif body, hero photography, drop caps, sidebars



Page-turn animations, 3D magazine spreads.





Bauhaus



Geometric, primary



Studios, schools



Primary colors, circles + squares, sans display



Abstract 3D geometry, primary color shaders.





3D Immersive



Futuristic, interactive



VR/AR, product showcases



Dynamic camera, interactive elements, depth layers



Full 3D environments, user-controlled navigation, physics-based interactions.





Slide Deck Modern



Professional, clean



Pitch decks, keynotes



Minimal text, bold visuals, consistent transitions



Animated slide transitions, 3D diagrams, interactive prototypes.



4. COLOR THEORY WITH OKLCH (24 Ready Palettes + Custom Recipes)

Why OKLCH?





Perceptually uniform: L (lightness) is real brightness.



Chroma (C): Saturation (clamp 0–0.37).



Hue (H): 0–360° color wheel.

Building a Palette (5-Minute Method)





Pick hero hue (e.g., brand color → measure its H).



Build neutral scale: Same H, low C (0.005–0.02), L from 0.99 → 0.08.



Pick accent hue ≈ 120° or 180° from hero (complementary).



Destructive color: oklch(0.55–0.62, 0.22, 25) (red).



Contrast check: Body text ≥ 4.5:1 vs. background.

🎨 24 Ready-to-Paste Palettes

(Format: --background / --foreground / --primary / --accent)

/* 1. Editorial Calm — beige + ink */
--background: oklch(0.98 0.01 80);
--foreground: oklch(0.18 0.02 80);
--primary:    oklch(0.22 0.04 80);
--accent:     oklch(0.62 0.15 30);

/* 2. Modern Dark Tech */
--background: oklch(0.14 0.02 250);
--foreground: oklch(0.96 0.005 250);
--primary:    oklch(0.72 0.18 250);
--accent:     oklch(0.78 0.20 160);

/* 3. Luxe Champagne */
--background: oklch(0.96 0.015 70);
--foreground: oklch(0.18 0.02 70);
--primary:    oklch(0.18 0.02 70);
--accent:     oklch(0.72 0.12 75);

/* 4. Brutalist High-Contrast */
--background: oklch(0.98 0 0);
--foreground: oklch(0.12 0 0);
--primary:    oklch(0.12 0 0);
--accent:     oklch(0.68 0.24 25);

/* 5. Y2K Vapor */
--background: oklch(0.97 0.02 320);
--foreground: oklch(0.22 0.04 290);
--primary:    oklch(0.72 0.18 320);
--accent:     oklch(0.80 0.16 200);

/* 6. Aurora Glass (dark) */
--background: oklch(0.16 0.03 280);
--foreground: oklch(0.96 0.01 280);
--primary:    oklch(0.74 0.18 290);
--accent:     oklch(0.78 0.18 180);

/* 7. Terracotta & Sage */
--background: oklch(0.97 0.015 60);
--foreground: oklch(0.22 0.03 40);
--primary:    oklch(0.58 0.13 40);
--accent:     oklch(0.65 0.08 145);

/* 8. Forest Premium */
--background: oklch(0.97 0.01 145);
--foreground: oklch(0.18 0.04 145);
--primary:    oklch(0.32 0.08 145);
--accent:     oklch(0.70 0.14 75);

/* 9. Navy Trust */
--background: oklch(0.98 0.005 250);
--foreground: oklch(0.18 0.04 250);
--primary:    oklch(0.28 0.10 250);
--accent:     oklch(0.65 0.16 220);

/* 10. Cyber Neon */
--background: oklch(0.12 0.02 260);
--foreground: oklch(0.96 0.01 160);
--primary:    oklch(0.82 0.20 160);
--accent:     oklch(0.72 0.24 320);

/* 11. Sunset Gradient */
--background: oklch(0.97 0.02 50);
--foreground: oklch(0.20 0.04 30);
--primary:    oklch(0.68 0.20 30);
--accent:     oklch(0.72 0.18 350);

/* 12. Ocean Deep */
--background: oklch(0.98 0.01 220);
--foreground: oklch(0.18 0.04 220);
--primary:    oklch(0.42 0.14 220);
--accent:     oklch(0.72 0.14 195);

/* 13. Apple Calm */
--background: oklch(0.99 0.003 250);
--foreground: oklch(0.18 0.01 250);
--primary:    oklch(0.55 0.18 255);
--accent:     oklch(0.65 0.12 200);

/* 14. Magazine Cream */
--background: oklch(0.96 0.02 80);
--foreground: oklch(0.15 0.02 30);
--primary:    oklch(0.20 0.03 30);
--accent:     oklch(0.55 0.22 25);

/* 15. Mono Studio (warm gray) */
--background: oklch(0.97 0.005 60);
--foreground: oklch(0.20 0.005 60);
--primary:    oklch(0.30 0.005 60);
--accent:     oklch(0.65 0.18 50);

/* 16. Pastel Soft */
--background: oklch(0.98 0.015 330);
--foreground: oklch(0.30 0.03 330);
--primary:    oklch(0.72 0.10 330);
--accent:     oklch(0.78 0.10 200);

/* 17. Emerald Prestige */
--background: oklch(0.97 0.01 150);
--foreground: oklch(0.18 0.04 150);
--primary:    oklch(0.40 0.12 150);
--accent:     oklch(0.72 0.12 90);

/* 18. Crimson Editorial */
--background: oklch(0.97 0.01 30);
--foreground: oklch(0.15 0.02 30);
--primary:    oklch(0.40 0.18 25);
--accent:     oklch(0.70 0.14 60);

/* 19. Slate Enterprise */
--background: oklch(0.98 0.005 240);
--foreground: oklch(0.22 0.02 240);
--primary:    oklch(0.35 0.04 240);
--accent:     oklch(0.62 0.16 220);

/* 20. Coral Energy */
--background: oklch(0.98 0.01 20);
--foreground: oklch(0.20 0.04 20);
--primary:    oklch(0.65 0.20 25);
--accent:     oklch(0.55 0.20 290);

/* 21. Midnight Indigo */
--background: oklch(0.13 0.04 280);
--foreground: oklch(0.96 0.01 280);
--primary:    oklch(0.62 0.20 280);
--accent:     oklch(0.78 0.16 200);

/* 22. Desert Clay */
--background: oklch(0.94 0.02 60);
--foreground: oklch(0.22 0.04 30);
--primary:    oklch(0.58 0.10 50);
--accent:     oklch(0.45 0.12 25);

/* 23. Glacier */
--background: oklch(0.97 0.01 220);
--foreground: oklch(0.20 0.03 240);
--primary:    oklch(0.50 0.08 220);
--accent:     oklch(0.75 0.10 200);

/* 24. Brutalist Yellow */
--background: oklch(0.95 0.18 100);
--foreground: oklch(0.12 0 0);
--primary:    oklch(0.12 0 0);
--accent:     oklch(0.55 0.24 25);

🌈 Gradient Recipes (OKLCH-Safe)

--gradient-hero:    linear-gradient(135deg, oklch(0.72 0.18 290), oklch(0.78 0.18 200));
--gradient-aurora:  linear-gradient(120deg, oklch(0.68 0.20 290) 0%, oklch(0.72 0.18 200) 50%, oklch(0.78 0.16 160) 100%);
--gradient-sunset:  linear-gradient(135deg, oklch(0.72 0.20 50), oklch(0.65 0.22 20), oklch(0.55 0.20 340));
--gradient-mesh:    radial-gradient(at 20% 20%, oklch(0.72 0.18 290 / 0.5), transparent 50%),
                    radial-gradient(at 80% 30%, oklch(0.78 0.18 200 / 0.5), transparent 50%),
                    radial-gradient(at 50% 90%, oklch(0.74 0.16 340 / 0.4), transparent 50%);
--gradient-subtle:  linear-gradient(180deg, var(--background), oklch(from var(--background) calc(l - 0.02) c h));
--gradient-3d-glow: linear-gradient(135deg, oklch(0.8 0.2 290 / 0.8), oklch(0.7 0.15 200 / 0.6));

🖤 Shadow Recipes

--shadow-sm:      0 1px 2px oklch(0 0 0 / 0.05);
--shadow-md:      0 4px 12px oklch(0 0 0 / 0.08);
--shadow-elegant: 0 20px 50px -20px oklch(from var(--primary) l c h / 0.3);
--shadow-glow:    0 0 60px oklch(from var(--accent) l c h / 0.4);
--shadow-brutal:  6px 6px 0 0 var(--foreground);
--shadow-inset:   inset 0 1px 0 0 oklch(1 0 0 / 0.06);
--shadow-3d:      0 10px 30px -10px oklch(from var(--primary) l c h / 0.2);



5. TYPOGRAPHY (Font Pairs, Scales, Hierarchy)

🔤 Font Pair Library







Direction



Display



Body



Mono



3D/Slide Use Case





Editorial Minimal



Fraunces, Instrument Serif



Inter, Geist



JetBrains Mono



Serif for 3D text, Inter for UI.





Modern Tech



Geist, Space Grotesk



Geist, Inter



Geist Mono



Geist for 3D UI panels, mono for code.





Luxe



Cormorant, Playfair



Karla, Inter



—



Playfair for elegant 3D titles.





Brutalist



Boldonse, Big Shoulders



IBM Plex Mono



IBM Plex Mono



Mono for brutalist 3D geometry.





Y2K / Vapor



Tektur, Pixelify Sans



DM Sans



Space Mono



Pixelify for retro 3D effects.





Aurora / Glass



Bricolage Grotesque



Inter



Geist Mono



Bricolage for futuristic 3D.





Magazine



DM Serif Display, Abril Fatface



Lora, IBM Plex Serif



—



DM Serif for 3D magazine layouts.





Soft Pastel



Outfit, Sora



DM Sans, Nunito



—



Outfit for playful 3D.





Apple Calm



Inter Tight



Inter



Geist Mono



Inter Tight for clean 3D.





Swiss Grid



Inter (tracking-tight)



Inter



JetBrains Mono



Inter for precise 3D grids.





3D Immersive



Rajdhani, Exo 2



Inter



Fira Code



Rajdhani for bold 3D headlines.





Slide Deck Modern



Manrope, Poppins



Inter



Fira Code



Manrope for slide titles.

📏 Modular Scale (rem)

Ratio 1.250 (UI) or 1.333 (Editorial):







Size



Value (rem)



Use Case



3D/Slide Scaling





xs



0.75



Captions, labels



Small 3D annotations.





sm



0.875



Buttons, badges



Secondary 3D text.





base



1



Body text



Default 3D text.





lg



1.125



Subheadings



Medium 3D labels.





xl



1.25



Headings (h4)



Large 3D annotations.





2xl



1.5



Headings (h3)



Bold 3D text.





3xl



1.875



Headings (h2)



Hero 3D text.





4xl



2.25



Headings (h1 mobile)



Large 3D titles.





5xl



3



Headings (h1 desktop)



Extra-large 3D headlines.





6xl



3.75



Hero text



Massive 3D text (e.g., landing pages).





7xl



4.5



Display text



Giant 3D text (e.g., slide titles).





8xl



6



Mega headings



Immersive 3D text (e.g., VR).





9xl



8



Ultra headings



Billboards, large-scale 3D.

📜 Typography Rules





One <h1> per page. No exceptions.



Hierarchy: Size + weight, never color alone.



Body line-height: 1.5–1.7.



Headlines line-height: 1.0–1.15.



Measure: ≤ 70ch for prose. Use max-w-prose.



Tracking:





tracking-tight on display ≥ 4xl



tracking-tighter on ≥ 7xl



Eyebrows: tracking-widest uppercase text-xs font-medium text-muted-foreground



Drop caps: first-letter:text-7xl first-letter:font-display first-letter:float-left first-letter:mr-3 first-letter:mt-1



Balance: text-balance on headlines, text-pretty on paragraphs.

🔗 Loading Fonts (Canonical Pattern)

In src/routes/__root.tsx, inside head().links:

{
  rel: "preconnect",
  href: "https://fonts.googleapis.com"
},
{
  rel: "preconnect",
  href: "https://fonts.gstatic.com",
  crossOrigin: "anonymous"
},
{
  rel: "stylesheet",
  href: "https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,300..900&family=Inter:wght@400;500;600;700&display=swap"
}

In src/styles.css @theme inline:

--font-display: "Fraunces", ui-serif, Georgia, serif;
--font-sans:    "Inter", ui-sans-serif, system-ui, sans-serif;
--font-mono:    "Geist Mono", ui-monospace, monospace;



6. SPACING, RHYTHM & LAYOUT ARCHETYPES

📏 Spacing Scale

(Use Tailwind defaults, no arbitrary values)







Value



Use Case





0



Reset





0.5



Tight gaps





1



Small padding





1.5



Compact elements





2



Default padding





3



Medium padding





4



Large padding





5



Extra-large padding





6



Card padding (mobile)





8



Card padding (desktop)





10



Section gaps





12



Wide gaps





16



Large sections





20



Section vertical rhythm





24



Hero sections





32



Alternating section rhythm





40



Tall sections





48



Extra-tall sections





64



Massive spacing

🏗️ Common Spacing Patterns







Element



Spacing





Button (sm)



px-4 py-2





Button (md)



px-6 py-3





Button (lg)



px-8 py-4





Card padding (mobile)



p-6





Card padding (desktop)



p-8





Section rhythm



py-20 or py-32





Container



mx-auto max-w-7xl px-4 sm:px-6 lg:px-8





Stack inside card



space-y-3





Grid gap



gap-6 or gap-8

🎨 Layout Archetypes

A. Bento Grid (Feature Showcase)

<div className="grid grid-cols-1 md:grid-cols-6 gap-4 md:gap-6">
  <Card className="md:col-span-4 md:row-span-2 p-10" />  {/* Hero feature */}
  <Card className="md:col-span-2 p-6" />
  <Card className="md:col-span-2 p-6" />
  <Card className="md:col-span-3 p-6" />
  <Card className="md:col-span-3 p-6" />
</div>

3D Twist: Replace one card with a 3D model (e.g., a floating product mockup).

B. Editorial Split (60/40 with Offset)

<div className="grid md:grid-cols-12 gap-12 items-center">
  <div className="md:col-span-7 md:col-start-1">{/* Text */}</div>
  <div className="md:col-span-4 md:col-start-9">{/* Image or 3D Model */}</div>
</div>

3D Twist: Use a 3D scene in the image column (e.g., a rotating product).

C. Magazine Layout





Wide hero photo



3-column sidebar text



Drop caps

3D Twist: Use a 3D magazine spread as the hero image.

D. Zigzag Layout

<div className="md:[&:nth-child(even)]:flex-row-reverse">
  {/* Alternating image/text rows */}
</div>

3D Twist: Alternate between 2D images and 3D models for dynamic depth.

E. Card Grid (Equal)





Only for truly equal items (logos, team, gallery).

3D Twist: Use 3D cards with hover tilt effects.

F. Sidebar Dashboard





Left nav: 240–280px



Main: min-w-0

3D Twist: Add a floating 3D navigation panel.

G. Full-Bleed Cinema





Sections at min-h-screen



Single statement per screen

3D Twist: Use parallax 3D backgrounds for depth.

H. Asymmetric Off-Grid





Translate cards by 4–12px



Rotate -1° to 1°



Overlap with negative margins

3D Twist: Use 3D transforms for true depth.

📱 Container Queries (Responsive Components)

.card-grid { container-type: inline-size; }
@container (min-width: 600px) {
  .card { grid-template-columns: 1fr 1fr; }
}

3D Twist: Adjust 3D camera angles based on container size.



7. SHADCN + CVA — COMPOSITION PATTERNS (Code)

🔧 Extending Button with Custom Variants

// src/components/ui/button.tsx
import { cva } from "class-variance-authority";

const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium transition-all duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50",
  {
    variants: {
      variant: {
        default:  "bg-primary text-primary-foreground hover:bg-primary/90 shadow-sm",
        hero:     "bg-[image:var(--gradient-hero)] text-primary-foreground shadow-[var(--shadow-elegant)] hover:scale-[1.02] hover:shadow-[var(--shadow-glow)]",
        glass:    "backdrop-blur-md bg-white/10 border border-white/20 text-foreground hover:bg-white/20",
        brutal:   "bg-primary text-primary-foreground border-2 border-foreground shadow-[var(--shadow-brutal)] hover:translate-x-1 hover:translate-y-1 hover:shadow-none",
        outline:  "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        ghost:    "hover:bg-accent hover:text-accent-foreground",
        link:     "text-primary underline-offset-4 hover:underline",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        "3d":     "bg-[image:var(--gradient-3d-glow)] text-foreground shadow-[var(--shadow-3d)] hover:scale-105 transform-gpu",
      },
      size: {
        sm: "h-9 px-3",
        md: "h-10 px-4",
        lg: "h-12 px-8 text-base",
        xl: "h-14 px-10 text-lg",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: { variant: "default", size: "md" },
  }
);

🪟 Card Variants

const cardVariants = cva("rounded-xl bg-card text-card-foreground transition-all", {
  variants: {
    variant: {
      default:  "border shadow-sm",
      elevated: "border shadow-[var(--shadow-elegant)] hover:-translate-y-1 hover:shadow-[var(--shadow-glow)]",
      glass:    "backdrop-blur-xl bg-white/5 border border-white/10",
      brutal:   "border-2 border-foreground shadow-[var(--shadow-brutal)]",
      ghost:    "border-transparent shadow-none",
      "3d":     "transform-gpu [transform-style:preserve-3d] hover:rotate-y-5 hover:rotate-x-5",
    },
  },
  defaultVariants: { variant: "default" },
});

🏷️ Badge Variants

const badgeVariants = cva("inline-flex items-center rounded-full px-3 py-1 text-xs font-medium", {
  variants: {
    variant: {
      default:  "bg-primary text-primary-foreground",
      soft:     "bg-accent/10 text-accent border border-accent/20",
      outline:  "border border-border text-foreground",
      gradient: "bg-[image:var(--gradient-hero)] text-primary-foreground",
      "3d":     "bg-[image:var(--gradient-3d-glow)] text-foreground shadow-[var(--shadow-3d)]",
    },
  },
});



8. SECTION RECIPES (Paste-and-Edit)

🌌 HERO — Editorial Calm

<section className="container mx-auto px-4 py-24 md:py-40">
  <div className="max-w-4xl">
    <p className="mb-6 text-xs uppercase tracking-widest text-muted-foreground">
      New · v2.0
    </p>
    <h1 className="font-display text-5xl md:text-7xl lg:text-8xl leading-[1.05] tracking-tight text-balance">
      A quieter way to <em className="italic text-accent">ship</em> software.
    </h1>
    <p className="mt-8 max-w-xl text-lg md:text-xl text-muted-foreground text-pretty">
      One sentence that promises a concrete outcome — not what the product is, but what changes for the user.
    </p>
    <div className="mt-10 flex flex-wrap gap-3">
      <Button variant="hero" size="lg">Start free</Button>
      <Button variant="ghost" size="lg">See how it works →</Button>
    </div>
  </div>
</section>

3D Twist: Replace the <em> text with a 3D-floating accent word.

⚡ HERO — Bold Tech with Glow + 3D

<section className="relative overflow-hidden bg-background py-32">
  <div className="absolute inset-0 bg-[image:var(--gradient-mesh)] opacity-50" />
  {/* 3D Background Element */}
  <div className="absolute inset-0 z-0">
    <Model3D src="/models/hero-floating-shapes.glb" />
  </div>
  <div className="container relative mx-auto px-4 text-center z-10">
    <Badge variant="soft" className="mb-6">⚡ Now in public beta</Badge>
    <h1 className="mx-auto max-w-4xl font-display text-6xl md:text-8xl font-bold tracking-tighter text-balance">
      Build at the speed of thought.
    </h1>
    <p className="mx-auto mt-6 max-w-2xl text-lg text-muted-foreground">
      A short sub-headline that earns the click.
    </p>
    <div className="mt-10 flex justify-center gap-3">
      <Button variant="hero" size="xl">Get started free</Button>
      <Button variant="outline" size="xl">
        <PlayIcon className="mr-2" /> Live demo
      </Button>
    </div>
  </div>
</section>

🧩 FEATURE BENTO (with 3D Elements)

<section className="container mx-auto px-4 py-24">
  <div className="mb-16 max-w-2xl">
    <p className="text-xs uppercase tracking-widest text-muted-foreground mb-4">Features</p>
    <h2 className="font-display text-4xl md:text-5xl tracking-tight">
      Everything you need. Nothing you don't.
    </h2>
  </div>
  <div className="grid md:grid-cols-6 gap-4">
    <Card variant="elevated" className="md:col-span-4 md:row-span-2 p-10">
      <div className="relative">
        <Model3D src="/models/feature-hero.glb" className="w-full h-64" />
      </div>
      <h3 className="text-2xl font-semibold mt-4">Big idea here</h3>
      <p className="mt-3 text-muted-foreground">
        Lead with the headline feature. Pair with a **3D illustration**.
      </p>
    </Card>
    <Card variant="3d" className="md:col-span-2 p-6">
      <Model3D src="/models/feature-1.glb" />
      <h4 className="mt-4">Feature 1</h4>
    </Card>
    <Card variant="3d" className="md:col-span-2 p-6">
      <Model3D src="/models/feature-2.glb" />
      <h4 className="mt-4">Feature 2</h4>
    </Card>
    <Card variant="elevated" className="md:col-span-3 p-6">
      <h4>Feature 3</h4>
    </Card>
    <Card variant="elevated" className="md:col-span-3 p-6">
      <h4>Feature 4</h4>
    </Card>
  </div>
</section>

💰 PRICING — 3 Tiers, Middle Highlighted (3D Accent)

<section className="container mx-auto px-4 py-24">
  <div className="grid md:grid-cols-3 gap-6 md:gap-4 max-w-5xl mx-auto items-stretch">
    {tiers.map((t, i) => (
      <Card
        key={t.name}
        variant={i === 1 ? "elevated" : "default"}
        className={cn(
          "p-8 flex flex-col",
          i === 1 && "md:scale-105 border-primary shadow-[var(--shadow-3d)]"
        )}
      >
        {i === 1 && (
          <div className="relative -top-4 -mx-4">
            <Model3D src="/models/pricing-highlight.glb" className="w-full h-8" />
          </div>
        )}
        {i === 1 && (
          <Badge variant="gradient" className="self-start mb-4">
            Most popular
          </Badge>
        )}
        <h3 className="text-xl font-semibold">{t.name}</h3>
        <div className="my-6">
          <span className="text-5xl font-display tracking-tight">${t.price}</span>
          <span className="text-muted-foreground">/mo</span>
        </div>
        <ul className="space-y-3 text-sm flex-1">
          {t.features.map((f) => (
            <li key={f} className="flex gap-2">
              <Check className="w-4 h-4 text-accent shrink-0 mt-0.5" />
              {f}
            </li>
          ))}
        </ul>
        <Button
          variant={i === 1 ? "hero" : "outline"}
          size="lg"
          className="mt-8 w-full"
        >
          Choose {t.name}
        </Button>
      </Card>
    ))}
  </div>
</section>

🎯 CTA Band (with 3D Glow Effect)

<section className="relative overflow-hidden">
  <div className="absolute inset-0 bg-[image:var(--gradient-hero)]" />
  <div className="absolute inset-0">
    <Model3D src="/models/cta-particles.glb" className="opacity-30" />
  </div>
  <div className="container relative mx-auto px-4 py-24 text-center text-primary-foreground">
    <h2 className="font-display text-4xl md:text-6xl tracking-tight max-w-3xl mx-auto text-balance">
      Stop reading. Start shipping.
    </h2>
    <Button variant="glass" size="xl" className="mt-10">
      <RocketIcon className="mr-2" /> Create your account
    </Button>
  </div>
</section>

👣 Footer (with 3D Logo)

<footer className="border-t bg-card">
  <div className="container mx-auto px-4 py-16 grid gap-12 md:grid-cols-5">
    <div className="md:col-span-2">
      <div className="w-12 h-12 mb-4">
        <Model3D src="/models/logo-3d.glb" />
      </div>
      <p className="mt-4 text-sm text-muted-foreground max-w-xs">
        One-line product description.
      </p>
    </div>
    {footerCols.map((col) => (
      <div key={col.title}>
        <h4 className="text-xs uppercase tracking-widest text-muted-foreground mb-4">
          {col.title}
        </h4>
        <ul className="space-y-3 text-sm">
          {col.links.map((l) => (
            <li key={l.href}>
              <Link
                to={l.href}
                className="hover:text-accent transition-colors"
              >
                {l.label}
              </Link>
            </li>
          ))}
        </ul>
      </div>
    ))}
  </div>
  <div className="border-t">
    <div className="container mx-auto px-4 py-6 flex justify-between text-xs text-muted-foreground">
      <span>© 2026 Brand</span>
      <span>Made with care.</span>
    </div>
  </div>
</footer>



9. MOTION SYSTEM (CSS + Framer Motion + 3D Animation)

🎬 CSS Keyframes

(Add to styles.css)

@keyframes fade-in       { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }
@keyframes fade-in-slow  { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: none; } }
@keyframes scale-in      { from { opacity: 0; transform: scale(0.96); } to { opacity: 1; transform: scale(1); } }
@keyframes shimmer       { 0% { background-position: -200% 0; } 100% { background-position: 200% 0; } }
@keyframes float         { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
@keyframes glow-pulse    { 0%, 100% { box-shadow: 0 0 30px oklch(from var(--accent) l c h / 0.3); } 50% { box-shadow: 0 0 60px oklch(from var(--accent) l c h / 0.6); } }
@keyframes rotate-3d     { from { transform: rotateY(0deg) rotateX(0deg); } to { transform: rotateY(360deg) rotateX(360deg); } }
@keyframes pulse-3d      { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.05); } }

@utility animate-fade-in       { animation: fade-in 0.5s ease-out both; }
@utility animate-fade-in-slow  { animation: fade-in-slow 0.8s ease-out both; }
@utility animate-scale-in      { animation: scale-in 0.4s ease-out both; }
@utility animate-float         { animation: float 4s ease-in-out infinite; }
@utility animate-glow-pulse    { animation: glow-pulse 3s ease-in-out infinite; }
@utility animate-rotate-3d      { animation: rotate-3d 20s linear infinite; }
@utility animate-pulse-3d       { animation: pulse-3d 2s ease-in-out infinite; }

🎭 Framer Motion Patterns

Page Enter Animation

import { motion } from "framer-motion";

const pageVariants = {
  initial: { opacity: 0, y: 12 },
  animate: { opacity: 1, y: 0 },
  exit: { opacity: 0, y: -12 },
};

function Page() {
  return (
    <motion.div
      initial="initial"
      animate="animate"
      exit="exit"
      variants={pageVariants}
      transition={{ duration: 0.4, ease: "easeOut" }}
    >
      {/* Page content */}
    </motion.div>
  );
}

Hover Lift (3D-Ready)

<motion.div
  whileHover={{ y: -4, scale: 1.02 }}
  transition={{ type: "spring", stiffness: 300, damping: 24 }}
  className="transform-gpu"
>
  {/* 3D or 2D element */}
</motion.div>

3D Model Animation

import { useRef } from "react";
import { useFrame } from "@react-three/fiber";

function FloatingModel({ model }) {
  const ref = useRef();
  useFrame((state) => {
    ref.current.rotation.y = Math.sin(state.clock.elapsedTime) * 0.2;
    ref.current.position.y = Math.sin(state.clock.elapsedTime * 0.5) * 0.1;
  });
  return <primitive object={model} ref={ref} />;
}

Scroll-Triggered 3D Parallax

import { useScroll } from "framer-motion";

function Parallax3D() {
  const { scrollYProgress } = useScroll();
  return (
    <motion.div
      style={{ y: scrollYProgress * -100 }}
      className="fixed inset-0 z-0"
    >
      <Model3D src="/models/parallax-bg.glb" />
    </motion.div>
  );
}

🎯 Motion Rules





One transform per interaction (translate OR scale OR rotate, not all three).



Durations:





150ms (hover)



300ms (transitions)



500–800ms (entrances)



Easing:





ease-out for entrances



ease-in-out for loops



ease-in for exits



Never animate width/height. Use transform + opacity.



Wrap heavy motion in motion-safe:

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

🚀 3D Animation Guidelines

Tools & Libraries







Tool



Use Case



Pros



Cons





Three.js



Custom 3D scenes



Full control, performant



Steeper learning curve





React Three Fiber



3D in React



Declarative, React-friendly



Requires WebGL





Framer Motion 3D



Simple 3D animations



Easy to use, good for basics



Limited to basic 3D





Spline



No-code 3D models



Drag-and-drop, great for designers



Less control, paid for advanced





Babylon.js



Complex 3D (games, simulations)



Powerful, feature-rich



Heavy, overkill for UI

Best Practices





Performance:



Limit **polygon count** (aim for <50k triangles).

Use **GLTF/GLB** format (compressed, single file).

**Lazy-load** 3D models (`loading="lazy"`).

**Dispose** of unused resources (e.g., textures, geometries).



Accessibility:



Provide **fallback content** for non-WebGL browsers.

Use `aria-label` for interactive 3D elements.

Respect `prefers-reduced-motion`.



Design:



**Camera:** Start with a **static camera**, then add subtle movement.

**Lighting:** Use **HDRI environments** for realistic reflections.

**Materials:** Prefer **PBR materials** (metalness, roughness).

**Shadows:** Use **soft shadows** for a natural look.



Interactivity:



**Hover:** Rotate or scale on hover.

**Click:** Trigger animations or open modals.

**Scroll:** Parallax or reveal effects.

**Drag:** Allow users to rotate 3D models (e.g., product showcases).

Example: 3D Product Showcase

import { Canvas } from "@react-three/fiber";
import { OrbitControls, Environment } from "@react-three/drei";

function ProductShowcase({ model }) {
  return (
    <Canvas camera={{ fov: 50, position: [0, 0, 5] }}>
      <ambientLight intensity={0.5} />
      <spotLight position={[10, 10, 10]} angle={0.15} penumbra={1} intensity={1} />
      <primitive object={model} scale={0.5} />
      <Environment preset="city" />
      <OrbitControls enableZoom={false} enablePan={false} />
    </Canvas>
  );
}

Example: Animated 3D Button

import { motion } from "framer-motion";
import { useRef } from "react";
import { useFrame } from "@react-three/fiber";

function Animated3DButton() {
  const meshRef = useRef();
  useFrame((state) => {
    meshRef.current.rotation.y = Math.sin(state.clock.elapsedTime) * 0.1;
  });

  return (
    <motion.button
      whileHover={{ scale: 1.05 }}
      whileTap={{ scale: 0.95 }}
      className="relative w-32 h-32"
    >
      <Canvas>
        <ambientLight intensity={0.5} />
        <pointLight position={[10, 10, 10]} />
        <mesh ref={meshRef}>
          <boxGeometry args={[1, 1, 1]} />
          <meshStandardMaterial color="var(--primary)" />
        </mesh>
      </Canvas>
      <span className="absolute inset-0 flex items-center justify-center">
        Click Me
      </span>
    </motion.button>
  );
}



10. ACCESSIBILITY (WCAG AA, Focus, ARIA)

✅ Semantic HTML





Use landmarks: <header>, <nav>, <main>, <section>, <article>, <aside>, <footer>.



One <h1> per page. No exceptions.



Heading levels never skip (e.g., h2 → h4 is ❌).

⌨️ Keyboard Navigation





Visible focus on every interactive element:

focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2



Logical tab order.



No keyboard traps.



Escape closes overlays (modals, dropdowns).

🎨 Color & Contrast





Body text: ≥ 4.5:1 contrast vs. background.



Large text: ≥ 3:1 contrast.



UI components: ≥ 3:1 contrast.



Color is never the only signal (add icon, label, or pattern).

🔖 ARIA & Screen Readers





Form fields: Use <Label htmlFor> + aria-describedby for errors.



Icons:





Meaningful: aria-label or sibling text.



Decorative: aria-hidden="true".



Live regions: Use aria-live for dynamic content (e.g., toasts).

🖥️ Testing Checklist





Keyboard-only navigation works.



Screen reader announces all interactive elements.



Color contrast meets WCAG AA.



Focus indicators are visible.



Reduced motion is respected.



Touch targets are ≥ 48x48px.



11. SEO & METADATA PER ROUTE

📌 Required Metadata (TanStack Router)

// src/routes/index.tsx
import { createFileRoute } from "@tanstack/react-router";

export const Route = createFileRoute("/")({
  component: Home,
  head: () => (
    <>
      <title>Lovable | Ship Awwwards-Worthy Designs</title>
      <meta
        name="description"
        content="The ultimate UI/UX design system for modern web apps. Win Awwwards, not look like another demo."
      />
      <meta property="og:title" content="Lovable | Ship Awwwards-Worthy Designs" />
      <meta
        property="og:description"
        content="The ultimate UI/UX design system for modern web apps."
      />
      <meta property="og:image" content="https://yourdomain.com/og-home.jpg" />
      <meta name="twitter:card" content="summary_large_image" />
      <link rel="canonical" href="https://yourdomain.com" />
      <script type="application/ld+json">
        {`{
          "@context": "https://schema.org",
          "@type": "WebSite",
          "name": "Lovable",
          "description": "The ultimate UI/UX design system for modern web apps.",
          "url": "https://yourdomain.com"
        }`}
      </script>
    </>
  ),
});

📝 SEO Rules





Title: < 60 chars, primary keyword first.



Description: < 160 chars, value-led.



OG Image: Only on leaf routes with a real hero image.



Twitter Card: summary_large_image if OG image exists, else summary.



Canonical URL: Always set.



JSON-LD: Use for articles, products, FAQs.



Single <h1>: Matches <title> intent.



Alt Text: On all meaningful images.



12. IMAGE & ASSET DIRECTION

🖼️ Image Rules





Always generate, never use placeholders.



Tools:





Midjourney (for photos, illustrations)



DALL·E 3 (for precise prompts)



Stable Diffusion (for custom models)



Spline (for 3D models)



Formats:





Photos: .jpg (compressed)



Transparency: .png



3D Models: .glb (preferred) or .gltf



Sizes:





Desktop hero: 1920x1080 (16:9)



Mobile hero: 1080x1080 (1:1)



Thumbnails: 800x600



Optimization:





Use **next-optimized-images** or **sharp** for compression.



Lazy load by default (loading="lazy").



Hero images: loading="eager".

🎨 Prompt Recipes







Type



Prompt





Editorial Photo



"35mm editorial photograph, soft daylight, muted desaturated palette, shallow depth of field, magazine cover quality"





3D Isometric



"3D isometric illustration, pastel gradients, soft shadows, rounded geometry, clay material"





Abstract Gradient



"abstract organic gradient mesh, oklch hues of {hero} and {accent}, soft blur, no text"





Product Mockup



"floating glass UI panels, soft glow, dark background, premium SaaS aesthetic"





Logo



"minimal geometric mark, single weight stroke, monoline, transparent background"





3D Product



"realistic 3D model, {product}, studio lighting, 8K, PBR materials"





Slide Background



"minimalist gradient background, subtle texture, corporate, {brand colors}"

📁 Asset Organization

public/
├── images/
│   ├── hero/
│   │   ├── desktop.jpg
│   │   └── mobile.jpg
│   ├── icons/
│   ├── illustrations/
│   └── thumbnails/
└── models/
    ├── hero.glb
    ├── feature-1.glb
    └── logo-3d.glb

src/
└── assets/
    ├── images/ (ES6 imports)
    └── models/ (ES6 imports)



13. COPYWRITING VOICE & MICROCOPY

🎯 Headline Formulas That Work







Formula



Example



Best For





Outcome-led



"Ship software people love."



SaaS, tools





Promise + Time



"Your invoices, paid in days not weeks."



FinTech, productivity





Opposition



"All your tools. None of the chaos."



All-in-one products





Question



"What if onboarding only took five minutes?"



Onboarding flows





Quietly Confident



"A better way to think."



Premium, luxury

✍️ Microcopy Rules







Context



Rule



Example





Buttons



Verb-first.



"Start free" (not "Get started for free")





Empty States



Explain + offer next step.



"No projects yet. Create your first →"





Errors



Human, blameless.



"That email doesn't match our records. Try again?"





Loading



Specific when possible.



"Generating preview…" (not "Loading…")





404s



Useful + on-brand.



"Page not found. Let's get you back on track."

🗣️ Voice Presets







Voice



Tone



Sentence Structure



Word Choice





Calm/Editorial



Slow, deliberate



Short sentences.



Plain words.





Tech-Confident



Declarative, precise



Direct.



Concrete numbers.





Playful



Light, witty



Wordplay (sparingly).



Earned humor.





Premium



Restrained, elegant



Longer pauses.



Less is more.



14. FORMS, EMPTY STATES, ERRORS, LOADING

📝 Forms





Library: Use shadcn <Form> + react-hook-form + zod.



Labels: Always above inputs (never placeholder-as-label).



Errors: Inline, below field, with aria-describedby.



Submit Button: Show loading state (spinner + "Saving…").



Grouping: Use <fieldset> + <legend> for related fields.

Example:

<Form {...form}>
  <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-4">
    <FormField
      control={form.control}
      name="email"
      render={({ field }) => (
        <FormItem>
          <FormLabel>Email</FormLabel>
          <FormControl>
            <Input placeholder="you@example.com" {...field} />
          </FormControl>
          <FormMessage />
        </FormItem>
      )}
    />
    <Button type="submit" disabled={isSubmitting}>
      {isSubmitting ? (
        <>
          <Loader2 className="mr-2 h-4 w-4 animate-spin" />
          Saving…
        </>
      ) : (
        "Submit"
      )}
    </Button>
  </form>
</Form>

🪟 Empty States





Icon/Illustration: Small, not giant.



Explanation: One line.



CTA: One action.



Tone: Encouraging, not apologetic.

Example:

<div className="flex flex-col items-center justify-center py-12">
  <div className="w-24 h-24 mb-4">
    <EmptyStateIcon />
  </div>
  <p className="text-muted-foreground mb-4">No projects yet.</p>
  <Button>Create your first project</Button>
</div>

❌ Errors





Toast: For ephemeral errors.



Inline: For field-level errors.



Full-page: Only for catastrophic errors.



Always actionable: "Try again", "Contact support", "Go back".

Example (Toast):

const { toast } = useToast();

toast({
  variant: "destructive",
  title: "Uh oh! Something went wrong.",
  description: "That email doesn't match our records. Try again?",
  action: (
    <ToastAction altText="Try again" onClick={() => window.location.reload()}>
      Try again
    </ToastAction>
  ),
});

⏳ Loading





Skeleton screens > spinners for content.



Match skeleton shape to final content.



Spinner: Only for actions < 2s. Otherwise, use a progress indicator.



Optimistic UI: When safe (e.g., "Liking" a post).

Example (Skeleton):

<div className="space-y-4">
  <Skeleton className="h-4 w-[250px]" />
  <Skeleton className="h-4 w-[200px]" />
  <Skeleton className="h-10 w-full" />
</div>



15. DARK MODE STRATEGY

🌙 Implementation Rules





Only implement if asked.



Define the complete .dark block — every token must have a dark counterpart.



Test every surface. Don’t ship with hardcoded light values that break.

🔧 Toggle Pattern (Next.js)

"use client";

import { useTheme } from "next-themes";

function ThemeToggle() {
  const { setTheme, theme } = useTheme();
  return (
    <DropdownMenu>
      <DropdownMenuTrigger asChild>
        <Button variant="ghost" size="icon">
          <Sun className="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0" />
          <Moon className="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100" />
          <span className="sr-only">Toggle theme</span>
        </Button>
      </DropdownMenuTrigger>
      <DropdownMenuContent align="end">
        <DropdownMenuItem onClick={() => setTheme("light")}>
          Light
        </DropdownMenuItem>
        <DropdownMenuItem onClick={() => setTheme("dark")}>
          Dark
        </DropdownMenuItem>
        <DropdownMenuItem onClick={() => setTheme("system")}>
          System
        </DropdownMenuItem>
      </DropdownMenuContent>
    </DropdownMenu>
  );
}

🎨 Dark Mode Tokens

:root {
  --background: oklch(0.98 0.01 80);
  --foreground: oklch(0.18 0.02 80);
  /* ... */
}

.dark {
  --background: oklch(0.14 0.02 250);
  --foreground: oklch(0.96 0.005 250);
  --primary: oklch(0.72 0.18 250);
  --accent: oklch(0.78 0.20 160);
  /* ... */
}

💾 Storage & Preference





Store preference in **localStorage**.



Respect **prefers-color-scheme** on first visit.



16. THE BOOTSTRAP RECIPE (Paste-Ready)

📄 src/styles.css (Complete Setup)

@import "tailwindcss" source(none);
@source "../src";
@import "tw-animate-css";

@custom-variant dark (&:is(.dark *));

@theme inline {
  /* colors */
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-destructive-foreground: var(--destructive-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);

  /* fonts */
  --font-display: "Fraunces", ui-serif, Georgia, serif;
  --font-sans:    "Inter", ui-sans-serif, system-ui, sans-serif;
  --font-mono:    "Geist Mono", ui-monospace, monospace;

  /* radius */
  --radius-sm: calc(var(--radius) - 4px);
  --radius-md: calc(var(--radius) - 2px);
  --radius-lg: var(--radius);
  --radius-xl: calc(var(--radius) + 4px);
}

:root {
  --radius: 0.75rem;

  /* Pick a palette from §4 and paste here */
  --background: oklch(0.98 0.01 80);
  --foreground: oklch(0.18 0.02 80);
  --card: var(--background);
  --card-foreground: var(--foreground);
  --primary: oklch(0.22 0.04 80);
  --primary-foreground: oklch(0.98 0.01 80);
  --secondary: oklch(0.94 0.01 80);
  --secondary-foreground: var(--foreground);
  --muted: oklch(0.94 0.01 80);
  --muted-foreground: oklch(0.50 0.02 80);
  --accent: oklch(0.62 0.15 30);
  --accent-foreground: oklch(0.98 0.01 80);
  --destructive: oklch(0.58 0.22 25);
  --destructive-foreground: oklch(0.98 0.01 80);
  --border: oklch(0.90 0.01 80);
  --input: var(--border);
  --ring: var(--accent);

  /* Tokens — gradients */
  --gradient-hero: linear-gradient(135deg, var(--primary), var(--accent));
  --gradient-mesh:
    radial-gradient(at 20% 20%, oklch(from var(--accent) l c h / 0.25), transparent 50%),
    radial-gradient(at 80% 30%, oklch(from var(--primary) l c h / 0.20), transparent 50%);
  --gradient-3d: linear-gradient(135deg, oklch(0.8 0.2 290 / 0.8), oklch(0.7 0.15 200 / 0.6));

  /* Tokens — shadows */
  --shadow-sm:      0 1px 2px oklch(0 0 0 / 0.05);
  --shadow-md:      0 4px 12px oklch(0 0 0 / 0.08);
  --shadow-elegant: 0 20px 50px -20px oklch(from var(--primary) l c h / 0.30);
  --shadow-glow:    0 0 60px oklch(from var(--accent) l c h / 0.40);
  --shadow-brutal:  6px 6px 0 0 var(--foreground);
  --shadow-3d:      0 10px 30px -10px oklch(from var(--primary) l c h / 0.2);

  /* Transitions */
  --transition-smooth: 200ms cubic-bezier(0.4, 0, 0.2, 1);
}

.dark {
  /* Paste dark counterpart of the palette */
  --background: oklch(0.14 0.02 250);
  --foreground: oklch(0.96 0.005 250);
  --primary: oklch(0.72 0.18 250);
  --primary-foreground: oklch(0.14 0.02 250);
  --secondary: oklch(0.20 0.02 250);
  --secondary-foreground: var(--foreground);
  --muted: oklch(0.20 0.02 250);
  --muted-foreground: oklch(0.70 0.02 250);
  --accent: oklch(0.78 0.20 160);
  --accent-foreground: oklch(0.14 0.02 250);
  --destructive: oklch(0.65 0.20 25);
  --destructive-foreground: oklch(0.96 0.005 250);
  --border: oklch(0.30 0.02 250);
  --input: var(--border);
  --ring: var(--accent);
}

@layer base {
  * { border-color: var(--color-border); }
  body {
    background-color: var(--color-background);
    color: var(--color-foreground);
    font-family: var(--font-sans);
    font-feature-settings: "ss01", "cv11";
  }
  h1, h2, h3, h4 { 
    font-family: var(--font-display); 
    letter-spacing: -0.02em; 
  }
  ::selection { background: oklch(from var(--accent) l c h / 0.25); }
}

/* keyframes */
@keyframes fade-in { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }
@keyframes float   { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
@keyframes rotate-3d { from { transform: rotateY(0deg) rotateX(0deg); } to { transform: rotateY(360deg) rotateX(360deg); } }

@utility animate-fade-in { animation: fade-in 0.5s ease-out both; }
@utility animate-float   { animation: float 4s ease-in-out infinite; }
@utility animate-rotate-3d { animation: rotate-3d 20s linear infinite; }



17. PRE-SHIP QUALITY AUDIT (40 CHECKS)

🎨 Design (10)





Color palette is consistent and accessible.



Typography uses the correct font pairs and hierarchy.



Spacing follows the defined scale (no arbitrary values).



Layout uses archetypes from §6.



Signature moment exists (e.g., hero animation, 3D element).



Images are high-quality, optimized, and have alt text.



3D models are optimized (polygon count, textures).



Dark mode (if implemented) works flawlessly.



Responsive design works on all breakpoints.



Visual hierarchy is clear and intentional.

🧩 Components (5)





All components use shadcn + CVA variants (no ad-hoc classNames).



Buttons have consistent styles and hover/focus states.



Cards use the correct variants (default, elevated, glass, brutal, 3D).



Forms follow accessibility and UX best practices.



3D components are performant and accessible.

🎬 Motion (5)





Animations are smooth and intentional.



No transition-all on body or heavy elements.



Durations follow the guidelines (150ms, 300ms, 500–800ms).



Easing is appropriate (ease-out, ease-in-out, ease-in).



Reduced motion is respected (prefers-reduced-motion).

✍️ Content (5)





Headlines are outcome-led and benefit-focused.



Microcopy is clear, actionable, and on-brand.



Empty states are helpful and encouraging.



Error messages are human and blameless.



Loading states are specific and user-friendly.

♿ Accessibility (5)





Semantic HTML is used (landmarks, headings).



Keyboard navigation works flawlessly.



Focus indicators are visible on all interactive elements.



Color contrast meets WCAG AA.



ARIA attributes are used where needed.

🔍 SEO (5)





Metadata is unique and optimized for each route.



Title is <60 chars, keyword-first.



Description is <160 chars, value-led.



OG images are set for leaf routes.



Canonical URLs are set.

🖼️ Images & Assets (3)





All images are generated (no placeholders).



3D models are optimized and lazy-loaded.



Asset organization follows the structure in §12.

✨ Polish (2)





No console errors or warnings.



Cross-browser testing (Chrome, Firefox, Safari).



18. ANTI-PATTERNS — BANNED LIST







Banned



Why



Replace With





from-purple-500 to-indigo-500 gradient on white



Generic AI slop



Domain-appropriate palette from §4





Inter for everything



Lazy



Display font for headlines





<button className="...">



Bypasses system



<Button variant="...">





bg-white / text-black



Bypasses theming



bg-background / text-foreground





bg-[#hexcode]



One-off color



Add token in styles.css





3 equal feature columns



Boring



Bento or asymmetric layout





Stock photos of multi-ethnic team



Cliché



Generated bespoke imagery





Gradient text on every heading



Visual noise



One signature use per page





Glassmorphism on every card



Dated



Use intentionally, 1–2 surfaces





Center-aligned everything



Wedding invite



Mix with left-aligned editorial





transition-all on body or *



Performance



Scoped transitions





Animating width/height



Reflow



transform + opacity only





<h1> repeated for visual size



A11y break



Use <h2> with display class





Dark mode toggle nobody asked for



Scope creep



Skip until requested





Sparkles icon as logo



Generic AI



Generated brand mark





Animating on page load to "wow"



Cheap



Earn motion with intent





Sticky CTAs on mobile that block content



UX hostile



Inline or thumb-reachable



19. REFERENCE GALLERIES

🏆 Awwwards-Worthy Inspiration







Reference



Why Look



Key Takeaways





Linear



Precision, density, dark-first SaaS



Dark mode, geometric shapes, micro-interactions





Vercel



Minimal-dark, geometric, premium



Monochrome palette, bold typography





Stripe



Editorial-tech, illustration, gradients



Gradients, illustration, whitespace





Apple



Restraint, typography, whitespace



Minimalism, large text, high-quality images





Arc Browser



Playful-modern, color, motion



Vibrant colors, smooth animations





Things 3



Calm-utility, native feel



Generous whitespace, serif fonts





Notion



Warm-neutral, friendly density



Soft colors, dense but clean UI





PostHog



Brutalist-fun, personality



Bold colors, playful microcopy





Pitch



Color-confident, gradient mastery



Gradients, bold typography





Framer



Motion-forward, scroll storytelling



Scroll-triggered animations, 3D elements





Are.na



Editorial, archival, slow



Asymmetric layouts, serif fonts





Cron / Notion Calendar



Information density done right



Compact, data-rich interfaces





Mercury



Premium fintech, restraint



Luxe palette, subtle animations





Raycast



Dense + delightful, dark + accent



Dark mode, accent colors, keyboard shortcuts



💡 Pro Tip: When starting a build, name your reference and commit to it.
Example: "This is Stripe meets Things 3, with a brutalist accent on the pricing."



20. 3D ANIMATION & INTERACTIVE ELEMENTS

🚀 Why 3D?





Engagement: 3D elements increase time-on-page by 40%.



Memorability: Users remember 3D experiences 2x better than 2D.



Differentiation: Stand out from flat, generic designs.



Storytelling: 3D can explain complex concepts visually.

🛠️ Tools & Workflow

3D Modeling Tools







Tool



Best For



Skill Level



Export Format



Pricing





Blender



Custom 3D models, animations



Advanced



GLTF/GLB



Free





Spline



No-code 3D designs, animations



Beginner



GLB



Free (Pro: $10/mo)





Cinema 4D



High-end 3D modeling



Advanced



GLTF/GLB



Paid





Figma + Spline



UI + 3D integration



Intermediate



GLB



Free (Pro: $10/mo)





Three.js Editor



Code-based 3D scenes



Intermediate



HTML/JS



Free

3D in React







Library



Use Case



Pros



Cons





React Three Fiber



3D in React apps



Declarative, React-friendly



Requires WebGL





Three.js



Custom 3D (vanilla JS)



Full control, performant



Steeper learning curve





Framer Motion 3D



Simple 3D animations



Easy to use



Limited to basic 3D





Babylon.js



Complex 3D (games, simulations)



Powerful, feature-rich



Heavy, overkill for UI





Model Viewer



Quick 3D model embedding



Native HTML, no JS required



Limited interactivity

🎯 3D Use Cases for UI/UX







Use Case



Example



Implementation



Performance Tips





Hero Background



Floating particles, abstract shapes



<Canvas> + <Particles>



Limit particle count (<1000).





Product Showcase



3D product model



<Canvas> + <OrbitControls>



Use GLTF + draco compression.





Interactive Card



3D card flip/tilt



<motion.div> + transform-style: preserve-3d



Use will-change: transform.





Loading Animation



3D spinner



<Canvas> + <mesh>



Keep geometry simple.





Scroll Parallax



3D layers on scroll



useScroll + motion



Use transform: translateZ for depth.





Micro-Interactions



Button hover (3D lift)



<motion.div whileHover={{ y: -4, scale: 1.02 }}>



Use transform-gpu.





Data Visualization



3D charts/graphs



three.js + d3.js



Simplify geometry for performance.





Virtual Tour



360° product view



<Canvas> + <Environment>



Use HDRI for lighting.





Animated Icons



3D icons



<Canvas> + <primitive>



Preload models.





Slide Transitions



3D slide effects



framer-motion + perspective



Use backface-visibility: hidden.

📦 3D Asset Optimization

File Formats







Format



Use Case



Pros



Cons





GLB



3D models (preferred)



Single file, binary, compressed



Not human-readable





GLTF



3D models (text-based)



Human-readable, modular



Larger file size





USDZ



Apple AR Quick Look



Native iOS support



Apple-only





FBX



Legacy 3D models



Widely supported



Not web-optimized





OBJ



Simple 3D models



Simple format



No animations, large file size

Compression Tools





glTF Pipeline (CLI tool for GLTF/GLB optimization)



Draco Compression (Reduces file size by 50–90%)



Meshoptimizer (Optimizes geometry)



Spline (Built-in optimization)

Optimization Checklist





Polygon count < 50k triangles.



Texture size < 2048x2048 (prefer 1024x1024).



Draco compression enabled.



GLB format (not GLTF).



Lazy loading (loading="lazy").



CDN hosting for large models.



Fallback for non-WebGL browsers.

🎨 3D Design Principles

1. Camera Setup





FOV (Field of View): 45–75° (50° is a safe default).



Position: Start with [0, 0, 5] (x, y, z).



Near/Far Clipping: near={0.1} (default), far={1000}.



Perspective vs. Orthographic: Use perspective for depth, orthographic for 2D-like views.

Example (React Three Fiber):

<Canvas camera={{ fov: 50, position: [0, 0, 5], near: 0.1, far: 1000 }}>
  {/* Your 3D scene */}
</Canvas>

2. Lighting





Ambient Light: Base illumination (intensity: 0.3–0.5).



Directional Light: Sunlight (intensity: 1–2).



Point Light: Local light source (e.g., lamps).



Spot Light: Focused light (e.g., flashlight).



Hemisphere Light: Sky/ground lighting.



Environment Map: HDRI for realistic reflections.

Example:

<Canvas>
  <ambientLight intensity={0.5} />
  <directionalLight position={[10, 10, 5]} intensity={1} />
  <pointLight position={[-10, -10, -10]} />
  <Environment preset="city" />
</Canvas>

3. Materials





MeshStandardMaterial: PBR (Physically Based Rendering) for realism.





color: Base color.



metalness: 0 (dielectric) to 1 (metal).



roughness: 0 (smooth) to 1 (rough).



envMap: Environment map for reflections.



MeshBasicMaterial: Flat color (no lighting).



MeshPhongMaterial: Legacy (deprecated).



ShaderMaterial: Custom shaders (advanced).

Example (PBR Material):

<meshStandardMaterial
  color="var(--primary)"
  metalness={0.8}
  roughness={0.2}
  envMap={environmentMap}
/>

4. Shadows





Cast Shadow: Object casts a shadow.



Receive Shadow: Object receives shadows.



Shadow Map Size: Higher = better quality (but slower).

Example:

<Canvas shadows>
  <directionalLight
    castShadow
    position={[10, 10, 5]}
    shadow-mapSize-width={2048}
    shadow-mapSize-height={2048}
  />
  <mesh castShadow receiveShadow>
    <boxGeometry />
    <meshStandardMaterial />
  </mesh>
  <planeGeometry args={[100, 100]} />
  <meshStandardMaterial />
</Canvas>

5. Performance Tips





Limit Polygons: Aim for <50k triangles per scene.



Use Instanced Mesh: For repeated objects (e.g., particles).



Level of Detail (LOD): Show simpler models at a distance.



Frustum Culling: Only render objects in view.



Occlusion Culling: Don’t render objects behind others.



Texture Atlases: Combine multiple textures into one.



Compress Textures: Use JPEG or WebP for textures.



Avoid Math in Render Loop: Pre-calculate values.

Example (Instanced Mesh):

import { InstancedMesh } from "three";

function ParticleSystem({ count = 1000 }) {
  const meshRef = useRef();
  useEffect(() => {
    const geometry = new THREE.SphereGeometry(0.1, 16, 16);
    const material = new THREE.MeshBasicMaterial({ color: "var(--accent)" });
    meshRef.current = new InstancedMesh(geometry, material, count);
    // Position particles...
  }, []);
  return <primitive object={meshRef.current} />;
}

🚀 3D Animation Techniques

1. Basic Animations





Rotation: mesh.rotation.x/y/z = value



Position: mesh.position.x/y/z = value



Scale: mesh.scale.x/y/z = value

Example (React Three Fiber):

import { useRef } from "react";
import { useFrame } from "@react-three/fiber";

function RotatingBox() {
  const meshRef = useRef();
  useFrame((state) => {
    meshRef.current.rotation.y = state.clock.elapsedTime;
  });
  return (
    <mesh ref={meshRef}>
      <boxGeometry />
      <meshStandardMaterial color="var(--primary)" />
    </mesh>
  );
}

2. Spring Physics

Use Framer Motion for spring-based animations:

import { motion } from "framer-motion";

<motion.div
  whileHover={{ scale: 1.05, rotateY: 10 }}
  transition={{ type: "spring", stiffness: 300, damping: 20 }}
>
  <Model3D src="/models/button.glb" />
</motion.div>

3. Scroll-Triggered Animations

Use **Framer Motion’s useScroll** or **React Three Fiber’s useScroll**:

import { useScroll } from "framer-motion";

function ScrollAnimatedModel() {
  const { scrollYProgress } = useScroll();
  return (
    <motion.div style={{ y: scrollYProgress * -100 }}>
      <Model3D src="/models/scroll-animated.glb" />
    </motion.div>
  );
}

4. Path Animations

Use **@react-three/drei’s Curve** or **Spline** for path animations:

import { Curve } from "@react-three/drei";

function PathAnimation() {
  const curve = new THREE.CatmullRomCurve3([
    new THREE.Vector3(0, 0, 0),
    new THREE.Vector3(5, 5, 0),
    new THREE.Vector3(10, 0, 0),
  ]);
  return (
    <Curve path={curve}>
      <mesh>
        <sphereGeometry args={[0.2]} />
        <meshBasicMaterial color="var(--accent)" />
      </mesh>
    </Curve>
  );
}

5. Morph Animations

Use **@react-three/drei’s Morph** or **useMorph**:

import { useMorph } from "@react-three/drei";

function MorphAnimation() {
  const { morph, nodes } = useMorph("/models/morph-targets.glb");
  return (
    <mesh onClick={() => morph("target1")}>
      <primitive object={nodes.target1} />
    </mesh>
  );
}

🎮 Interactive 3D Examples

1. 3D Product Configurator

import { Canvas } from "@react-three/fiber";
import { OrbitControls, Environment } from "@react-three/drei";

function ProductConfigurator({ model, colors }) {
  const [color, setColor] = useState(colors[0]);
  return (
    <div className="flex">
      <Canvas camera={{ fov: 50, position: [0, 0, 5] }}>
        <ambientLight intensity={0.5} />
        <spotLight position={[10, 10, 10]} angle={0.15} penumbra={1} />
        <primitive object={model} scale={0.5}>
          <meshStandardMaterial color={color} />
        </primitive>
        <Environment preset="city" />
        <OrbitControls enableZoom enablePan />
      </Canvas>
      <div className="flex flex-col gap-2 p-4">
        {colors.map((c) => (
          <button
            key={c}
            onClick={() => setColor(c)}
            className="w-8 h-8 rounded-full"
            style={{ backgroundColor: c }}
          />
        ))}
      </div>
    </div>
  );
}

2. 3D Card Flip

import { motion } from "framer-motion";

function CardFlip() {
  const [isFlipped, setIsFlipped] = useState(false);
  return (
    <motion.div
      className="relative w-64 h-80 perspective-1000"
      onClick={() => setIsFlipped(!isFlipped)}
    >
      <motion.div
        className="absolute inset-0 backface-hidden"
        initial={false}
        animate={{ rotateY: isFlipped ? 180 : 0 }}
        transition={{ duration: 0.6 }}
        style={{ transformStyle: "preserve-3d" }}
      >
        {/* Front */}
        <div className="absolute inset-0 bg-gradient-to-br from-primary to-accent rounded-xl p-6 flex items-center justify-center">
          <span className="text-white text-xl font-bold">Click to Flip</span>
        </div>
        {/* Back */}
        <div className="absolute inset-0 bg-background rounded-xl p-6 flex items-center justify-center rotate-y-180">
          <Model3D src="/models/flip-content.glb" />
        </div>
      </motion.div>
    </motion.div>
  );
}

3. 3D Scroll Parallax

import { useScroll } from "framer-motion";
import { Canvas } from "@react-three/fiber";

function ParallaxScene() {
  const { scrollYProgress } = useScroll();
  return (
    <div className="relative h-screen overflow-hidden">
      <Canvas>
        <ambientLight intensity={0.5} />
        <motion.group
          position-y={scrollYProgress * -10}
          position-z={scrollYProgress * -5}
        >
          <Model3D src="/models/parallax-layer-1.glb" />
        </motion.group>
        <motion.group position-y={scrollYProgress * -5}>
          <Model3D src="/models/parallax-layer-2.glb" />
        </motion.group>
      </Canvas>
      <div className="absolute inset-0 flex items-center justify-center">
        <h1 className="text-6xl font-bold text-white">Scroll Down</h1>
      </div>
    </div>
  );
}

4. 3D Particle System

import { Points, PointMaterial } from "@react-three/drei";
import { useMemo } from "react";

function ParticleSystem({ count = 1000 }) {
  const particlesPosition = useMemo(() => {
    const positions = new Float32Array(count * 3);
    for (let i = 0; i < count; i++) {
      positions[i * 3] = (Math.random() - 0.5) * 10;
      positions[i * 3 + 1] = (Math.random() - 0.5) * 10;
      positions[i * 3 + 2] = (Math.random() - 0.5) * 10;
    }
    return positions;
  }, [count]);

  return (
    <Points positions={particlesPosition} stride={3} frustumCulled={false}>
      <PointMaterial
        transparent
        color="var(--accent)"
        size={0.02}
        sizeAttenuation={true}
        depthWrite={false}
      />
    </Points>
  );
}

5. 3D Text

import { Text3D } from "@react-three/drei";

function Text3DComponent() {
  return (
    <Text3D
      font="/fonts/helvetiker_regular.typeface.json"
      size={0.5}
      height={0.2}
      curveSegments={12}
      bevelEnabled
      bevelThickness={0.02}
      bevelSize={0.02}
      bevelOffset={0}
      bevelSegments={5}
    >
      HELLO WORLD
      <meshStandardMaterial color="var(--primary)" />
    </Text3D>
  );
}

🌐 Hosting 3D Models

Option 1: Public Folder (Static Hosting)

public/
└── models/
    ├── hero.glb
    ├── feature-1.glb
    └── logo-3d.glb

Usage:

<Model3D src="/models/hero.glb" />

Option 2: ES6 Imports (Bundled)

src/
└── assets/
    └── models/
        ├── hero.glb
        └── feature-1.glb

Usage:

import heroModel from "@/assets/models/hero.glb";
<Model3D src={heroModel} />

Option 3: CDN Hosting (Recommended for Large Models)





Vercel Blob Storage



Cloudflare R2



AWS S3 + CloudFront



Spline Hosting

Usage:

<Model3D src="https://cdn.yourdomain.com/models/hero.glb" />

🔧 3D Model Viewer (Fallback)

For browsers without WebGL support, use the native <model-viewer>:

<model-viewer
  src="/models/hero.glb"
  alt="3D model of our product"
  ar
  ar-modes="scene-viewer quick-look"
  camera-controls
  environment-image="neutral"
  shadow-intensity="1"
  style="width: 100%; height: 400px;"
></model-viewer>

Note: Requires polyfill for some browsers.



21. SLIDES & PRESENTATION DESIGN

🎤 Why Slides Matter





Pitch Decks: Raise funding, attract partners.



Keynotes: Educate, inspire, or sell.



Internal Presentations: Align teams, share updates.



Portfolios: Showcase your work professionally.

📌 Slide Design Principles

1. The 10-20-30 Rule (Guy Kawasaki)





10 slides (max).



20 minutes (total).



30pt font (minimum).

2. The 6x6 Rule





≤ 6 bullet points per slide.



≤ 6 words per bullet.

3. The 5-Second Rule





If a slide takes >5 seconds to understand, simplify it.

4. The Picture Superiority Effect





Visuals > Text. People remember images 6x better than text.

🎨 Slide Aesthetics







Style



Use For



Key Features



3D Potential





Minimalist



Corporate, professional



Whitespace, clean typography



Subtle 3D accents





Modern Tech



Startups, SaaS



Dark mode, neon accents, gradients



3D UI mockups, holographic elements





Editorial



Storytelling, portfolios



Serif fonts, large images, drop caps



3D illustrations, depth layers





Brutalist



Bold statements, indie projects



Hard edges, primary colors, raw textures



3D geometric shapes, glitch effects





Luxe



High-end, premium



Gold accents, deep neutrals, slow motion



3D gold elements, cloth textures





Playful



Creative, fun projects



Bright colors, illustrations, animations



3D characters, bouncy animations





Data-Driven



Reports, analytics



Charts, graphs, minimal text



3D data visualizations

📝 Slide Content Structure

1. Title Slide





Headline: Project/product name.



Subheadline: One-sentence tagline.



Visual: Hero image or 3D model.



Footer: Your name, date, brand.

Example:

---
marp: true
theme: default
paginate: true
---

# **Lovable Design System**
## *Ship Awwwards-Worthy Interfaces*

![3D Logo](https://cdn.yourdomain.com/models/logo-3d.glb)

**Samia Aurangzeb**
June 2026

2. Problem Slide





Headline: "The Problem"



Bullet Points: 3–4 pain points.



Visual: Image or 3D illustration of the problem.

Example:

---

# The Problem

- **Generic designs** blend into the noise.
- **Poor UX** frustrates users.
- **Slow development** kills momentum.

![Problem Illustration](https://cdn.yourdomain.com/images/problem-3d.png)

3. Solution Slide





Headline: "The Solution"



Subheadline: One-sentence value prop.



Visual: Product screenshot or 3D mockup.

Example:

---

# The Solution
## *A design system for 100X better UI/UX*

![Solution 3D Mockup](https://cdn.yourdomain.com/models/solution.glb)

4. Features Slide





Headline: "Key Features"



Grid Layout: 2–4 features with icons or 3D models.

Example:

---

# Key Features

<div class="grid grid-cols-2 gap-8">
  <div>
    <div class="w-16 h-16 mb-4">
      ![Feature 1 Icon](https://cdn.yourdomain.com/models/feature-1.glb)
    </div>
    <h3>OKLCH Color Theory</h3>
    <p>Perceptually uniform colors for better UX.</p>
  </div>
  <div>
    <div class="w-16 h-16 mb-4">
      ![Feature 2 Icon](https://cdn.yourdomain.com/models/feature-2.glb)
    </div>
    <h3>3D Animations</h3>
    <p>Immersive, interactive elements.</p>
  </div>
</div>

5. Demo Slide





Headline: "See It in Action"



Embed: Video, GIF, or interactive 3D demo.

Example:

---

# See It in Action

<iframe
  src="https://yourdomain.com/demo"
  width="100%"
  height="400px"
  frameborder="0"
></iframe>

*or*

![3D Demo](https://cdn.yourdomain.com/models/demo.glb)

6. Traction Slide





Headline: "Traction"



Metrics: User growth, revenue, partnerships.



Visual: Chart or 3D data visualization.

Example:

---

# Traction

<div class="grid grid-cols-3 gap-8">
  <div>
    <h2>10K+</h2>
    <p>Active Users</p>
  </div>
  <div>
    <h2>$1M+</h2>
    <p>Revenue</p>
  </div>
  <div>
    <h2>50+</h2>
    <p>Partners</p>
  </div>
</div>

![Traction Chart](https://cdn.yourdomain.com/models/traction-3d.glb)

7. Team Slide





Headline: "The Team"



Grid Layout: Team member photos + names/roles.



Visual: 3D team illustration or group photo.

Example:

---

# The Team

<div class="grid grid-cols-3 gap-8">
  <div>
    <img src="https://cdn.yourdomain.com/images/team-1.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>Samia Aurangzeb</h3>
    <p>Founder & CEO</p>
  </div>
  <div>
    <img src="https://cdn.yourdomain.com/images/team-2.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>Jane Doe</h3>
    <p>Head of Design</p>
  </div>
  <div>
    <img src="https://cdn.yourdomain.com/images/team-3.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>John Smith</h3>
    <p>CTO</p>
  </div>
</div>

![Team 3D Illustration](https://cdn.yourdomain.com/models/team-3d.glb)

8. Roadmap Slide





Headline: "The Road Ahead"



Timeline: 3–5 milestones.



Visual: 3D roadmap or Gantt chart.

Example:

---

# The Road Ahead

<div class="space-y-4">
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-green-500 rounded-full"></div>
    <span>Q3 2026: Launch v2.0</span>
  </div>
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-blue-500 rounded-full"></div>
    <span>Q4 2026: Mobile App</span>
  </div>
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-purple-500 rounded-full"></div>
    <span>2027: AI Integration</span>
  </div>
</div>

![Roadmap 3D](https://cdn.yourdomain.com/models/roadmap-3d.glb)

9. Call-to-Action Slide





Headline: "Let’s Build the Future Together"



Subheadline: What you want the audience to do.



Visual: 3D CTA element or product screenshot.



Contact Info: Email, website, socials.

Example:

---

# Let’s Build the Future Together

## *Join us in revolutionizing UI/UX design.*

<div class="flex justify-center gap-4 mt-8">
  <a href="https://yourdomain.com/signup" class="bg-primary text-white px-6 py-3 rounded-lg">Get Started</a>
  <a href="https://yourdomain.com/contact" class="border border-primary text-primary px-6 py-3 rounded-lg">Contact Us</a>
</div>

<div class="flex justify-center gap-4 mt-8">
  <a href="mailto:hello@yourdomain.com">hello@yourdomain.com</a>
  <a href="https://twitter.com/yourdomain">@yourdomain</a>
  <a href="https://linkedin.com/company/yourdomain">LinkedIn</a>
</div>

![CTA 3D](https://cdn.yourdomain.com/models/cta-3d.glb)

10. Thank You Slide





Headline: "Thank You!"



Subheadline: Brief closing message.



Visual: 3D thank-you animation or brand logo.

Example:

---

# Thank You!

## *Questions?*

![Thank You 3D](https://cdn.yourdomain.com/models/thank-you-3d.glb)

**Samia Aurangzeb**
Founder & CEO, Lovable

hello@lovable.design | [lovable.design](https://lovable.design)



🎨 Slide Design Tools







Tool



Best For



Pros



Cons



3D Support





Marp



Markdown-based slides



Simple, version-controlled



Limited animations



❌ No





Slidev



Developer-friendly slides



Markdown + Vue, customizable



Requires Node.js



✅ Yes (via components)





Google Slides



Quick, collaborative



Easy to use, real-time collab



Generic templates



❌ No





Canva



Non-designers



Drag-and-drop, templates



Limited customization



❌ No





Pitch



Pitch decks



Beautiful templates, animations



Paid for advanced features



✅ Yes





Framer



Interactive presentations



Animations, 3D support



Steeper learning curve



✅ Yes





Figma



Custom slide designs



Full design control



Manual export to PDF/PPT



✅ Yes (via plugins)





Keynote



Mac users



Beautiful animations



Mac-only



✅ Yes





PowerPoint



Windows users



Widely compatible



Clunky animations



❌ No

🚀 Recommended Setup: Slidev + 3D

Slidev is the best choice for developers who want:





Markdown-based slides.



Custom themes (Tailwind, OKLCH colors).



3D support (via React/Vue components).



Interactive elements (e.g., live demos).

Installation:

npm init slidev@latest

Example slides.md:

---
theme: ./theme
---

# Slidev + 3D = 🚀

<div class="grid grid-cols-2 gap-8">
  <div>
    <h2>Why Slidev?</h2>
    <ul>
      <li>Markdown-based</li>
      <li>Custom themes</li>
      <li>3D support</li>
    </ul>
  </div>
  <div>
    <ClientOnly>
      <Model3D src="/models/slidev-3d.glb" class="w-full h-64" />
    </ClientOnly>
  </div>
</div>

Custom Theme (theme/index.css):

@import "tailwindcss";

@theme {
  --color-primary: oklch(0.62 0.15 30);
  --color-background: oklch(0.98 0.01 80);
  /* ... */
}

body {
  font-family: "Inter", sans-serif;
  background: var(--color-background);
  color: var(--color-foreground);
}



🎬 Slide Animations

1. Entrance Animations





Fade In:

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}



Slide In:

@keyframes slideIn {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}



Scale In:

@keyframes scaleIn {
  from { opacity: 0; transform: scale(0.9); }
  to { opacity: 1; transform: scale(1); }
}

2. Exit Animations





Fade Out:

@keyframes fadeOut {
  from { opacity: 1; }
  to { opacity: 0; }
}



Slide Out:

@keyframes slideOut {
  from { transform: translateX(0); }
  to { transform: translateX(100%); }
}

3. Emphasis Animations





Pulse:

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}



Shake:

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-5px); }
  75% { transform: translateX(5px); }
}

4. 3D Slide Transitions

Use Framer Motion for advanced transitions:

import { motion } from "framer-motion";

const slideVariants = {
  initial: { opacity: 0, x: 100 },
  animate: { opacity: 1, x: 0 },
  exit: { opacity: 0, x: -100 },
};

function Slide({ children }) {
  return (
    <motion.div
      variants={slideVariants}
      initial="initial"
      animate="animate"
      exit="exit"
      transition={{ duration: 0.5 }}
    >
      {children}
    </motion.div>
  );
}

5. Interactive Slides





Click Triggers:

<motion.div
  whileHover={{ scale: 1.05 }}
  whileTap={{ scale: 0.95 }}
  onClick={() => navigate("/next-slide")}
>
  Click Me
</motion.div>



Scroll Triggers:

const { scrollYProgress } = useScroll();
<motion.div style={{ opacity: scrollYProgress }}>
  Revealed on scroll
</motion.div>



3D Hover Effects:

<motion.div
  whileHover={{ rotateY: 10, rotateX: 10 }}
  transition={{ type: "spring" }}
>
  <Model3D src="/models/hover-3d.glb" />
</motion.div>



📦 Slide Templates (Copy-Paste)

Template 1: Minimalist Pitch Deck

---
marp: true
theme: default
paginate: true
---

# **Project Name**
## *Tagline Here*

![Hero Image](https://cdn.yourdomain.com/images/hero.jpg)

**Your Name**
[Your Email](mailto:you@yourdomain.com) | [Your Website](https://yourdomain.com)

---

# The Problem

- Pain point 1
- Pain point 2
- Pain point 3

![Problem Image](https://cdn.yourdomain.com/images/problem.jpg)

---

# The Solution

## *One-sentence value prop.*

![Solution Image](https://cdn.yourdomain.com/models/solution.glb)

---

# Key Features

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3>Feature 1</h3>
    <p>Description here.</p>
  </div>
  <div>
    <h3>Feature 2</h3>
    <p>Description here.</p>
  </div>
  <div>
    <h3>Feature 3</h3>
    <p>Description here.</p>
  </div>
  <div>
    <h3>Feature 4</h3>
    <p>Description here.</p>
  </div>
</div>

---

# Traction

| Metric       | Value   |
|--------------|---------|
| Users        | 10K+    |
| Revenue      | $1M+    |
| Partners     | 50+     |

![Traction Chart](https://cdn.yourdomain.com/models/traction.glb)

---

# Roadmap

- Q3 2026: Launch v2.0
- Q4 2026: Mobile App
- 2027: AI Integration

![Roadmap 3D](https://cdn.yourdomain.com/models/roadmap.glb)

---

# Let’s Connect

<div class="flex justify-center gap-4">
  <a href="https://yourdomain.com/signup">Get Started</a>
  <a href="https://yourdomain.com/contact">Contact Us</a>
</div>

**Your Name**
[Your Email](mailto:you@yourdomain.com) | [LinkedIn](https://linkedin.com/in/you)

---

# Thank You!

![Thank You 3D](https://cdn.yourdomain.com/models/thank-you.glb)

Template 2: Modern Tech Product Launch

---
marp: true
theme: ./theme-dark.css
paginate: true
---

# **Product Name**
## *Revolutionizing [Industry]*

<div class="flex justify-center">
  <Model3D src="/models/product-hero.glb" class="w-full h-96" />
</div>

**Your Name**
Founder & CEO

---

# The Problem

<div class="grid grid-cols-2 gap-8">
  <div>
    <h3>Old Way</h3>
    <ul>
      <li>Slow</li>
      <li>Expensive</li>
      <li>Complicated</li>
    </ul>
  </div>
  <div>
    <h3>New Way</h3>
    <ul>
      <li>⚡ Fast</li>
      <li>💰 Affordable</li>
      <li>🎯 Simple</li>
    </ul>
  </div>
</div>

---

# How It Works

<div class="flex gap-8">
  <div class="flex-1">
    <h3>Step 1</h3>
    <p>Description here.</p>
    <Model3D src="/models/step-1.glb" class="w-full h-48" />
  </div>
  <div class="flex-1">
    <h3>Step 2</h3>
    <p>Description here.</p>
    <Model3D src="/models/step-2.glb" class="w-full h-48" />
  </div>
  <div class="flex-1">
    <h3>Step 3</h3>
    <p>Description here.</p>
    <Model3D src="/models/step-3.glb" class="w-full h-48" />
  </div>
</div>

---

# Demo

<iframe
  src="https://yourdomain.com/demo"
  width="100%"
  height="500px"
  frameborder="0"
></iframe>

*or*

![Demo GIF](https://cdn.yourdomain.com/images/demo.gif)

---

# Pricing

<div class="grid grid-cols-3 gap-4">
  <div class="border rounded-lg p-6">
    <h3>Basic</h3>
    <p>$9/mo</p>
    <ul>
      <li>Feature 1</li>
      <li>Feature 2</li>
    </ul>
    <a href="https://yourdomain.com/signup?plan=basic">Get Started</a>
  </div>
  <div class="border rounded-lg p-6 bg-primary">
    <h3>Pro</h3>
    <p>$29/mo</p>
    <ul>
      <li>Everything in Basic</li>
      <li>Feature 3</li>
      <li>Feature 4</li>
    </ul>
    <a href="https://yourdomain.com/signup?plan=pro">Get Started</a>
  </div>
  <div class="border rounded-lg p-6">
    <h3>Enterprise</h3>
    <p>Custom</p>
    <ul>
      <li>Everything in Pro</li>
      <li>Dedicated Support</li>
    </ul>
    <a href="https://yourdomain.com/contact">Contact Sales</a>
  </div>
</div>

---

# Testimonials

<div class="grid grid-cols-2 gap-8">
  <div>
    <blockquote>
      "This product changed my life!"
    </blockquote>
    <cite>— Customer Name, Company</cite>
  </div>
  <div>
    <blockquote>
      "Best investment I’ve ever made."
    </blockquote>
    <cite>— Customer Name, Company</cite>
  </div>
</div>

---

# The Team

<div class="grid grid-cols-3 gap-8">
  <div>
    <img src="https://cdn.yourdomain.com/images/team-1.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>Name 1</h3>
    <p>Title</p>
  </div>
  <div>
    <img src="https://cdn.yourdomain.com/images/team-2.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>Name 2</h3>
    <p>Title</p>
  </div>
  <div>
    <img src="https://cdn.yourdomain.com/images/team-3.jpg" class="rounded-full w-24 h-24 mb-2" />
    <h3>Name 3</h3>
    <p>Title</p>
  </div>
</div>

---

# Roadmap

<div class="space-y-4">
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-green-500 rounded-full"></div>
    <span>Q3 2026: Launch v1.0</span>
  </div>
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-blue-500 rounded-full"></div>
    <span>Q4 2026: Mobile App</span>
  </div>
  <div class="flex items-center gap-4">
    <div class="w-4 h-4 bg-purple-500 rounded-full"></div>
    <span>2027: AI Integration</span>
  </div>
</div>

---

# Let’s Build the Future

<div class="flex justify-center gap-4">
  <a href="https://yourdomain.com/signup" class="bg-primary text-white px-6 py-3 rounded-lg">Get Started</a>
  <a href="https://yourdomain.com/contact" class="border border-primary text-primary px-6 py-3 rounded-lg">Contact Us</a>
</div>

**Your Name**
[Your Email](mailto:you@yourdomain.com) | [Twitter](https://twitter.com/you)

---

# Thank You!

![Thank You 3D](https://cdn.yourdomain.com/models/thank-you.glb)



🎯 CLOSING MANIFESTO

🚀 The 10 Commandments of Lovable Design





Tokens before components.



Variants before classNames.



References before vibes.



Restraint before features.



One signature moment per page.



Earn every animation.



Generate every image.



No purple on white.



3D with purpose, not just for show.



Slides that tell a story, not just show bullets.

💡 Final Thoughts





Design is a system, not a one-off.



Every pixel, animation, and word must earn its place.



3D and slides are tools — use them intentionally.



Ship something Awwwards-worthy.



📚 RESOURCES & TOOLS

🎨 Design Tools





Figma (UI/UX Design)



Spline (3D Design)



Blender (3D Modeling)



Penpot (Open-source Figma alternative)



Excalidraw (Hand-drawn diagrams)

💻 Development Tools





React Three Fiber (3D in React)



Three.js (3D Library)



Framer Motion (Animations)



Tailwind CSS (Styling)



shadcn/ui (UI Components)



TanStack Router (Routing)

📦 3D Asset Sources





Sketchfab (Free/paid 3D models)



TurboSquid (Premium 3D models)



CGTrader (3D models marketplace)



Poly Haven (Free PBR textures)



Mixamo (3D character animations)

📚 Learning Resources





React Three Fiber Docs



Three.js Fundamentals



Framer Motion Docs



OKLCH Color Picker



Awwwards (Design inspiration)

🤝 Communities





r/reactthreefiber (React 3D)



r/threejs (Three.js)



Framer Discord (Framer Motion)



Tailwind Discord (Tailwind CSS)



🚀 NEXT STEPS





Pick an aesthetic from §3.



Set up your tokens in styles.css.



Build a component library with shadcn + CVA.



Add 3D elements where they enhance the experience.



Design your slides with Slidev or Pitch.



Run the 40-point audit before shipping.



Ship something Awwwards-worthy.





"Design is not just what it looks like and feels like. Design is how it works." — Steve Jobs



"The details matter. It’s worth waiting to get it right." — Tim Cook



"3D is the future of the web. Start experimenting today." — You, after reading this.



Now go ship something legendary. 🚀
