# Ovis Landing Page — Project Context (Current State)

Use this document to continue working on the Ovis landing page in a new chat.

---

## File Locations

| File | Path |
|------|------|
| Main landing page | `/Users/israelatkins/Desktop/omni world /omni interface/ovis-landing.html` |
| Browser link | `file:///Users/israelatkins/Desktop/omni%20world%20/omni%20interface/ovis-landing.html` |
| Live (Vercel) | `https://ovis-six.vercel.app/` |
| GitHub repo | `https://github.com/israelatkins30/ovis` |
| Ovis char image | `/Users/israelatkins/Desktop/omni world /omni interface/ovis-char.png` |

Single self-contained HTML/CSS/JS file. No frameworks, no build step.

---

## Product

**Ovis** — AI-powered Instagram growth agent. "Jarvis for Instagram."
**Brand:** Omni World
**Domain (not yet live):** omniworld.app
**Email capture:** Formspree `https://formspree.io/f/mpqyergz`

---

## Color System (CSS Variables)

```css
:root {
  --bg:        #F5F6FA;   /* light silver page background */
  --bg2:       #ECEDF3;
  --surface:   #FFFFFF;
  --surface2:  #F0F1F7;
  --carbon:    #090B10;
  --border:    rgba(0,0,0,0.07);
  --border2:   rgba(0,0,0,0.12);
  --text:      #0C0D14;
  --muted:     rgba(12,13,20,0.52);
  --muted2:    rgba(12,13,20,0.30);
  --blue:      #0098C8;
  --blue-dark: #007AA0;
  --blue-dim:  rgba(0,152,200,0.10);
  --pad:       max(28px, 5.5vw);
}
```

---

## Page Sections (Top to Bottom)

### 1. NAV (fixed)
- Right-aligned "Get Access" button only (no logo)
- `nav`, `nav-cta`

### 2. HERO
- Giant floating "OVIS" text — dark gradient with drop-shadow stack, levitate animation
- Tagline: "Your Jarvis for Instagram"
- Sub: short description + "Zero logins · Zero dashboards · Zero thinking" proof row
- Two CTAs: "Get Early Access" (primary) + "See How It Works" (ghost)
- No nav logo, no toast cards, no testimonial cards, no badge, no arc reactor rings
- Key classes: `hero`, `hero-ovis`, `hero-tag`, `hero-sub`, `hero-btns`, `hero-zeros`
- OVIS gradient: `linear-gradient(175deg, #F0F4FF 0%, #C8D0E8 6%, #6E7898 16%, #22253A 30%, #4A5070 44%, #141620 56%, #3A3E52 68%, #0A0B12 82%, #060710 100%)`
- OVIS animation: `ovisAssemble` 1.1s + `ovisLevitate` 9s infinite float

### 3. SHOWCASE — "The pulse of your Instagram"
- Apple/Jobs-style reveal copy
- **Pulse card** — glass card showing live activity feed (follows, DMs, unlikes) with redacted handles
- Bridge line: "And to control all of it —"
- **Command bar** — glass pill with "Standing by." text + rotating example commands
- Caption: "Switch your target. Rewrite your bio. Adjust your message. One sentence. Ovis handles the rest."
- Key classes: `showcase`, `sc-intro`, `sc-card`, `sc-bridge`, `sc-bar`, `sc-bar-caption`

### 4. TELL IT ONCE
- Headline: "Tell it once. It runs forever."
- Three proof points: Zero daily input · 150+ actions per day · Safe by design
- Key classes: `tell-once`, `tell-eyebrow`, `tell-headline`, `tell-proof-row`

### 5. HOW IT WORKS *(added this session)*
- Eyebrow: "THREE STEPS"
- Headline: "Up and running in minutes."
- Sub: "No dashboards to babysit. No settings to revisit."
- 3-column grid with connector line between steps:
  1. **Connect** — Link your Instagram. No passwords stored. 30 seconds.
  2. **Set your target** — Tell Ovis your niche, city, audience. Two minutes.
  3. **Ovis runs** — Follows, likes, DMs, cleans up. Every day, automatically.
- Scroll-reveal stagger via IntersectionObserver (`.hiw-step.in-view`)
- Key classes: `how-it-works`, `hiw-inner`, `hiw-steps`, `hiw-step`, `hiw-step-icon`, `hiw-step-num`, `hiw-step-title`, `hiw-step-desc`

### 6. FEATURES V10 — "Your Instagram. Fully automated."
- **Huly.io-style dark bento grid** — near-black cards (`#0D0F15`) on light background
- 3-column asymmetric grid: wide (span 2) + narrow (span 1)
- Row 1: Smart Follow (wide) + Auto-Likes (narrow)
- Row 2: Voice-Matched DMs (narrow) + Auto-Unfollow (wide)
- Each card has: step number, icon, tag, title, description, iPhone mockup, stat badge
- Cursor-following radial glow via JS mouse tracking (`--mx`, `--my` CSS vars)
- Shimmer accent bar animation on top edge of each card
- Colored drop-shadow bloom behind each phone (per accent color)
- Scroll-reveal stagger (80ms between cards)
- **Card color variants:**
  - Smart Follow: `v10-ca-blue` (`#2AA8D8`)
  - Auto-Likes: `v10-ca-red` (`#F0546A`)
  - Voice-Matched DMs: `v10-ca-purple` (`#9B7EFF`)
  - Auto-Unfollow: `v10-ca-green` (`#1FD195`)
- Key classes: `features-v10`, `v10-list`, `v10-card`, `v10-card-wide`, `v10-card-narrow`, `v10-left`, `v10-phone`, `v10-stat-badge`

### 7. CAPSULES — "Four agents. One for every ambition."
- 5 glowing jar capsules with Ovis characters inside (hue-rotate per jar)
- Creator (blue, 0deg) · Fitness (green, 270deg) · Music (purple, 60deg) · Sales (orange, 170deg) · + Custom
- Ovis character image: `ovis-char.png` (512×512, circular alpha mask)
- Key classes: `caps-section`, `caps-item`, `caps-jar`, `caps-char`, `caps-name`, `caps-hook`

### 8. SOCIAL PROOF
- Single testimonial card with quote, avatar, name, handle, Instagram badge
- Three stats: +400 followers / 24/7 autopilot / 0 manual hours
- Scroll-reveal via `arm-from-bot` class
- Key classes: `proof`, `proof-card`, `proof-quote`, `proof-stats`

### 9. WAITLIST CTA — "You're early. Let's keep it that way."
- Countdown timer (48-hour cycle with 18-hour grace)
- "Initialize Access" button → opens modal
- Key classes: `waitlist`, `countdown-row`

### 10. FOOTER
- Brand + copyright only

### 11. MODAL (overlay)
- Email capture: name, email, niche fields
- Submits to Formspree `https://formspree.io/f/mpqyergz`
- Success screen with referral link + tweet button
- Key classes: `modal-overlay`, `modal-card`, `modal-form`, `modal-success`

---

## JavaScript Behaviors

| Block | What it does | Key targets |
|-------|-------------|-------------|
| Countdown timer | 48hr cycle, ticks every 1s | `#cdHours`, `#cdMins`, `#cdSecs` |
| Waitlist counter | Bumps 1247+ every 8–15s | `#waitlistCount` |
| Bar text rotation | 3 example commands cycle every 3.2s | `#barText` |
| Modal open/close | Opens email form overlay | `#modalOverlay`, `#earlyAccessForm` |
| Form submit | POST to Formspree, shows success screen | `#modalForm`, `#modalSuccess` |
| Niche FOMO | Shows niche-specific availability | `#nicheFomo`, `#nicheInput` |
| Jarvis typewriter | Types init message on scroll-in | `#jarvisBrief`, `.jb-cursor` |
| Built cards stagger | Assembly entrance animation | `.built-card`, `#builtGrid` |
| Bento cursor glow | Mouse position → CSS vars on each card | `.v10-card` (`--mx`, `--my`) |
| Bento stat count-up | Counts up numbers when scrolled into view | `.v10-stat-val[data-count]` |
| Bento scroll reveal | Stagger `.in-view` on cards | `.v10-card` |
| HIW scroll reveal | Stagger `.in-view` on steps | `.hiw-step` |
| Referral system | Unique ref code + copy/tweet | `#msRefLink`, `#msCopyBtn` |

---

## Design Principles

- **Bento cards are dark** (`#0D0F15`) on a light silver page (`#F5F6FA`) — creates Huly.io contrast
- **OVIS hero text** floats out of the screen with multi-layer drop-shadow + levitate animation
- **Showcase section** is Jobs-style: headline → card → bridge → bar → caption
- **No clutter:** Each scroll = one clear idea
- **Copy voice:** Confident, minimal, premium. Never hype-y. "Ovis is an agent, not a tool."

---

## Key Copy Lines

- "Your Jarvis for Instagram"
- "Tell it once. It runs forever."
- "The pulse of your Instagram."
- "And to control all of it —" / "Standing by."
- "Up and running in minutes."
- "Four agents. One for every ambition."
- "You're early. Let's keep it that way."

---

## What's Been Built This Session

- Dark Huly-style bento grid (4 feature cards, asymmetric layout, cursor glow, shimmer bars, phone glow)
- "How It Works" 3-step section with connector line + stagger reveal
- OVIS hero polish (dark gradient, 3D drop-shadows, levitate float)
- Showcase section (Apple-reveal copy, pulse card, command bar)
- Capsule characters (ovis-char.png with hue-rotate)
- Hero cleanup (removed nav logo, toast cards, testimonials, badge, rings)
- Vercel deployment config fixed (`outputDirectory: "omni interface"`)

---

## Potential Next Additions

- **FAQ accordion** — "Will Instagram ban me?", "How fast will I see results?" etc. (highest conversion impact)
- **Results metrics strip** — Bold numbers: avg followers/month, actions/day, manual hours
- **Comparison table** — Ovis vs. manual vs. growth agency
