# Ovis Landing Page — Full Project Context

Use this document to continue working on the Ovis landing page in a new chat. Everything built so far is described here in full detail.

---

## Project Overview

**Product:** Ovis — an AI-powered Instagram growth agent ("Jarvis for Instagram")
**Brand:** Omni World
**File:** `/Users/israelatkins/Desktop/omni interface/ovis-landing.html`
**Type:** Single-file HTML/CSS/JS landing page — no frameworks, no dependencies
**Goal:** A landing page that feels like an onboarding flow. By the time someone reaches the CTA, they feel like they've already built their own Ovis bot and just need to flip a switch to go live.

---

## File Location

```
/Users/israelatkins/Desktop/omni interface/ovis-landing.html
```

This is a single self-contained file. All CSS, HTML, and JS live inside it. No build step required — open directly in a browser.

---

## Current Color System (CSS Variables)

```css
:root {
  /* ── Silver Chrome ── */
  --bg:         #A8ADB8;   /* silver chrome background */
  --surface:    #B4B9C4;   /* card/component surface */
  --surface2:   #9CA1AC;   /* deeper inset areas */
  --border:     rgba(0,0,0,0.11);
  --text:       #080810;   /* near-black for contrast */
  --muted:      rgba(8,8,16,0.50);

  /* ── Chrome steel blue accents ── */
  --blue:       #1A58A0;
  --blue-label: #144C8E;
  --blue-title: #185298;
  --blue2:      #104080;
  --blue3:      #0C3870;
  --green:      #148A38;
  --silver:     #6878A0;
  --steel:      #3A5070;
  --pad:        max(36px, 5vw);
}
```

**Design aesthetic:** Light silver chrome — like polished aluminum or a chrome car fixture. Components are slightly lighter than the background to lift off the surface. Text is near-black for maximum contrast.

**"OVIS" hero title color:** `#A8D8F0` (very light sky blue — hardcoded on `.hero h1`)

**Buttons:** Chrome metallic gradient style:
- Primary (btn-main, btn-cta, nav-cta): `linear-gradient(180deg, #2A78C8 0%, #1A5898 60%, #144880 100%)` with white text, dark border, inset highlight
- Ghost button: Frosted glass — `rgba(255,255,255,0.35)` background, dark border, backdrop blur

---

## Page Section Order (Top to Bottom)

1. **NAV** — Fixed top bar. "Ovis" logo left, "Try for Free" button right.
2. **HERO** — Giant "OVIS" in light sky blue (`#A8D8F0`). Subheading "Jarvis for Instagram." Tagline row. Try Now + See How It Works buttons. Below buttons: the hero product card (activity stream).
3. **FIRST ROBOT** — "Your first robot for Instagram." Ovis Unit-001 card with before/after stats and live counters.
4. **WHAT IT DOES (Clarity Strip)** — 3-card grid explaining: Follows the right people / DMs in your voice / Engages 24/7.
5. **OPTION A: LOGIC LOOP** — "Not a bot. A system." Animated card showing: Follow → Like → Like again → Wait → Did they follow back? → Yes: DM / No: Unfollow. Steps light up in sequence via JS.
6. **OPTION B: ACTIVITY STREAM** — "Ovis is already working." Live feed of 8 rows (follow, like, like again, follow-back, DM, unfollow, etc.) that play in sequence once and stop.
7. **STEP 1: YOUR VOICE** — "1 of 2 · Setup" badge. "Tell Ovis how you sound." Voice card with typewriter animation and tone chip selector.
8. **STEP 2: YOUR AUDIENCE** — "2 of 2 · Setup" badge. "Tell Ovis who to find." Preset tile shelf (Fitness, Entrepreneur, Music Artist, Coach, Lifestyle, Custom). Clicking a tile updates the anatomy card below.
9. **SEE IT RUN** — "You're set up." The full Ovis demo card showing the bot running with a live quote rotator, feed, session timer, and action counter.
10. **SOCIAL PROOF** — 3-stat bar: 1,247 Creators running Ovis / 84k+ Actions daily / Free · No waitlist.
11. **FINAL CTA** — "I'll take it from here." — Ovis. "Turn on Ovis for [Instagram]" button.
12. **FOOTER** — "Ovis by Omni World · © 2026"

> **Note:** Option A and Option B are both currently visible on the page, stacked one above the other. The user has not yet chosen which one to keep. Once they decide, delete the other.

---

## Hero Card (Under "Try Now" Button)

The hero product card is styled like a macOS app window with:
- **Window chrome header** — dots (red/yellow/green), "Ovis × Instagram" logo centered
- **Status bar** — `@yourhandle · Ovis` / `Fitness Creator Mode · Active` / green live dot
- **Greeting** — "Your interface. Zero buttons — Ovis handles it."
- **Activity stream feed** (`id="liveFeed"`) — rows feed in via JS using `st-row` format
- **Footer** — `Actions today: [counter]` + Ovis status text

**JS behavior:** Loops through 15 feed entries forever. First 3 rows seed immediately, then each new row appears every 5–11 seconds. Counter ticks up with each row. Feed trims to max 5 visible rows at a time (oldest fades out).

---

## Key CSS Classes

### Layout
- `.ed-section` — full-width section with `padding: 140px var(--pad)`
- `.ed-inner` — centered content container, `max-width: 580px`
- `.ed-label` — small eyebrow label above titles
- `.ed-title` — large section heading
- `.ed-sub` — body paragraph below heading

### Step Badges (Setup Flow)
- `.step-badge` — inline label "1 of 2 · Setup"
- `.step-badge-num` — circular numbered badge

### Clarity Strip (What It Does)
- `.clarity-strip` — section wrapper
- `.clarity-grid` — 3-col grid (collapses to 1 col on mobile)
- `.clarity-card` — individual feature card with shimmer top border
- `.clarity-icon`, `.clarity-action`, `.clarity-desc`

### Activity Stream (Option B + Hero Feed)
- `.stream-section`, `.stream-inner`, `.stream-card`
- `.stream-header`, `.stream-hd-left`, `.stream-av`, `.stream-handle`, `.stream-mode-label`, `.stream-live-pill`, `.stream-live-dot`
- `.stream-feed`, `.st-row`, `.st-av`, `.st-info`, `.st-name`, `.st-meta`
- `.st-tag` with variants: `.st-follow` (blue), `.st-like` (red-pink), `.st-dm` (green), `.st-unfollow` (orange), `.st-back` (bright green)
- `.stream-footer`, `.stream-count-label`, `.stream-niche-label`

### Hero Card Specific
- `.hero-live-card` — the card itself (gradient bg, border-radius 26px, scan line animation)
- `.hlc-head` — macOS window chrome header
- `.hlc-body` — card body (padding 24px 22px)
- `.hlc-sbar` — status bar row at top of body
- `.hlc-sbar-av`, `.hlc-sbar-handle`, `.hlc-sbar-mode`, `.hlc-sbar-live`
- `.hlc-greeting` — "Your interface. Zero buttons..." text
- `.hlc-hero-feed` — stream feed container (margin: 12px -22px 0 to bleed edge-to-edge)
- `.hlc-sfoot`, `.hlc-sfoot-count`, `.hlc-sfoot-status`

### Logic Loop (Option A)
- `.loop-section`, `.loop-inner`, `.loop-card`
- `.loop-steps`, `.loop-node`, `.loop-node-icon`, `.loop-node-label`, `.loop-node-sub`
- `.loop-arrow` — SVG arrow between steps
- `.loop-decision`, `.loop-decision-q`, `.loop-branches`
- `.loop-branch.yes`, `.loop-branch.no`
- Active states: `.ln-active`, `.la-active`, `.lb-active`

### First Robot Card
- `.frc` — the main dark card (`background: #CDD2DC`)
- `.frc-scan` — animated scan line
- `.frc-grid` — background grid
- `.frc-glow` — ambient glow
- `.frc-top`, `.frc-meta`, `.frc-unit`, `.frc-badge`
- `.frc-headline`, `.frc-hl-sub`
- `.frc-split`, `.frc-col`, `.frc-before`, `.frc-now`
- `.frc-row`, `.frc-n` (big stat number), `.frc-l` (stat label)
- `.frc-strip` — bottom status bar with live counters

### Preset Shelf (Step 2)
- `.op-shelf` — horizontal scrollable shelf
- `.op-tile`, `.op-sel` (selected state), `.op-sel-dot`, `.op-icon`, `.op-name`, `.op-desc`

### Anatomy Card (Step 2)
- `.oa-card`, `.oa-head`, `.oa-head-icon`, `.oa-head-title`
- `.oa-grid`, `.oa-cell`, `.oa-cell-l`, `.oa-cell-v`

### Voice Card (Step 1)
- `.voice-card`, `.vc-label`, `.vc-question`, `.vc-input-wrap`
- `.vc-input-text` (`id="vcTyping"`) — typewriter target
- `.vc-cursor` — blinking cursor
- `.tone-chips`, `.chip`, `.chip.active`
- `.vc-confirm`

### Social Proof Strip
- `.proof-strip`, `.proof-bar` — 3-col grid card with green shimmer top border
- `.proof-item`, `.proof-n` (big number), `.proof-l` (label)

### CTA Section
- `.cta`, `.cta-speaker`, `.cta-av`, `.cta-speaker-name`, `.cta-speaker-status`
- `.btn-cta`, `.btn-cta-ig` — main CTA button with Instagram SVG logo
- `.cta-fine` — "No credit card · Cancel anytime"

---

## JavaScript — All Live Animations

### 1. Hero Feed (`addFeedRow`)
- **Array:** `feedData` — 15 entries with `{initials, avColor, name, tagClass, tagText, meta}`
- **Behavior:** Loops forever. Seeds 3 rows at 0/1000/2000ms, then each row schedules the next at 5000–11000ms random delay. Max 5 visible rows — oldest fades out when limit hit.
- **Counter:** `id="actionCount"` — starts at 40, increments with each row, resets at 100
- **Status text:** `id="ovisStatusText"` — populated by separate Ovis status ticker IIFE

### 2. Option A Logic Loop
- **Nodes:** `id="ln0"` through `id="ln3"` — Follow, Like, Like again, Wait
- **Arrows:** `id="la0"` through `id="la2"`
- **Branches:** `id="lb-yes"`, `id="lb-no"`
- **Behavior:** Cycles through 6 states every 1800ms: steps 0→1→2→3 light up in sequence, then decision shows yes branch, then no branch, then loops

### 3. Option B Activity Stream
- **Array:** 8 entries in `rows[]` — follow, like, like again, follow-back, DM, unfollow, follow, like
- **Behavior:** Plays all 8 rows **once** and stops. First 3 stagger at 0/900/1800ms, rest chain. Max 5 visible. Counter `id="streamCountB"` goes to 8 and holds.
- **Feed container:** `id="streamFeedB"`

### 4. Typewriter (Step 1 Voice Card)
- **Target:** `id="vcTyping"`
- **Messages:** 3 DM-style messages cycle with typewriter effect
- **Behavior:** Types each message char by char, pauses, fades out, types next

### 5. Preset Switcher (Step 2)
- **Presets:** 6 objects (Fitness Creator, Entrepreneur, Music Artist, Coach, Lifestyle, Custom)
- **Tiles:** `.op-tile[data-preset="0-5"]` — clicking updates anatomy card with fade transition
- **Anatomy targets:** `id="oaIcon"`, `id="oaGrid"` — update with preset's target/voice/actions/schedule

### 6. Ovis Demo Card (See It Run section)
- Quote rotator — 5 quotes cycle every ~5–7 seconds
- Live feed — 12 entries, new row every 6–11 seconds
- Session timer — starts 3h 12m, ticks every 60s
- Action counter — starts at 71, increments with each feed row

### 7. First Robot Card Counters
- `id="frcDms"` — starts 73, ticks every 90s
- `id="frcActionCount"` — starts 71, ticks every 18s
- `id="frcSessionTime"` — starts "3h 12m", ticks every 60s

### 8. Ovis Status Ticker
- `id="ovisStatusText"` — cycles through ~8 status messages (scanning, found a match, sending DM, etc.)
- Checks `ovisMatchInterrupt` flag from feed to insert "Found a perfect match" at the right moment

---

## Pending Decisions / Next Steps

1. **Choose between Option A and Option B** — Both are currently stacked on the page. User needs to pick one and delete the other.
   - Option A = Logic Loop (animated step sequence showing the follow→like→wait→DM/unfollow intelligence)
   - Option B = Activity Stream (live feed of actions, runs once and stops)

2. **Algorithm knowledge section** — User discussed adding a section that communicates Ovis knows the Instagram algorithm for your niche. 5 concepts were proposed:
   - The Signal Map (network visualization)
   - The Niche Algorithm Profile (classified data readout)
   - The Account Scanner (profile being "read" with data points surfacing)
   - The Certainty Contrast (guessing vs. Ovis side by side)
   - The Niche Fingerprint (unique growth pattern per niche)
   User has not yet chosen or built this section.

3. **Sticky build progress bar** — Discussed but not built. Would show `Voice → Audience → Live` progress as user scrolls through the setup steps.

4. **Scroll-triggered step completion states** — Discussed but not built. Each setup step would show "✓ locked in" as user scrolls past.

5. **Color refinement** — User has been iterating on the chrome color. Current bg is `#A8ADB8`. User may want to continue adjusting.

6. **Console error** — User reported an error but Claude in Chrome extension was not connected so it could not be diagnosed. Should be investigated.

---

## Design Principles Established

- **Onboarding feel:** The page should feel like you're building your Ovis as you scroll, not watching a demo. By the CTA, the visitor feels emotionally invested.
- **Step framing:** "1 of 2 · Setup" and "2 of 2 · Setup" badges make the voice and audience sections feel like real configuration steps.
- **"See It Run" payoff:** The demo card appears AFTER both setup steps, so seeing it "live" makes sense — you just configured it.
- **No clutter:** Every section is minimal. No information overload. Each scroll is one clear idea.
- **Seamless, minimal:** All copy and design choices should feel professional and never corny.

---

## Brand / Copy Voice

- Ovis is not a tool. It's a bot. An agent. A robot. The **world's first autonomous Instagram agent**.
- Positioning: Like Jarvis (Iron Man's AI) but for Instagram growth.
- Key messages:
  - "Your interface. Zero buttons — Ovis handles it."
  - "Not a tool. Not a scheduler. An autonomous agent."
  - "There is nothing else on Earth like it."
  - "I'll take it from here." — Ovis
- Tone: Confident, minimal, premium. Never hype-y. Never corny.
- The algorithm angle: Ovis knows the Instagram algorithm for your specific niche. Everyone else is guessing. Ovis already knows.
- Growth loop Ovis runs: Follow → Like → Like again → Wait 3 days → Did they follow back? → Yes: DM in your voice → No: Unfollow (keeps ratio clean)

---

## Technical Notes

- Font: `-apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Inter'` — system font stack
- No external JS libraries
- CSS animations used: `blink`, `rowIn`, `stPulse`, `frcBorderPulse`, `frcScanMove`, `btnPulse`
- All IDs used by JS: `heroTitle`, `liveFeed`, `actionCount`, `ovisStatusText`, `vcTyping`, `opShelf`, `oaIcon`, `oaGrid`, `streamFeedB`, `streamCountB`, `ln0-ln3`, `la0-la2`, `lb-yes`, `lb-no`, `frcDms`, `frcActionCount`, `frcSessionTime`
- No duplicate IDs — verified clean
- Mobile: `@media (max-width: 560px)` breakpoints exist for clarity grid and other components
