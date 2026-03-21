# Ovis — Claude Instructions

## Key Rules

- **Always provide the file path AND the browser link** when referencing or modifying any file.
  - File path format: `/Users/israelatkins/Desktop/omni world /omni interface/ovis-landing.html`
  - Browser link format: `file:///Users/israelatkins/Desktop/omni%20world%20/omni%20interface/ovis-landing.html`
- Never mention a file without giving the user a way to open it immediately.

## Project Structure

| File | Purpose | Path |
|------|---------|------|
| `ovis-landing.html` | Main landing page (ACTIVE) | `/Users/israelatkins/Desktop/omni world /omni interface/ovis-landing.html` |
| `omni-landing.html` | Older dark theme version (archive) | `/Users/israelatkins/Desktop/omni world /omni interface/omni-landing.html` |
| `ovis-context.md` | Full project documentation | `/Users/israelatkins/Desktop/omni world /omni interface/ovis-context.md` |
| `omni-launch-thread.md` | Twitter/X launch strategy | `/Users/israelatkins/Desktop/omni world /omni interface/omni-launch-thread.md` |

## Browser Link (always send this after edits)

```
file:///Users/israelatkins/Desktop/omni%20world%20/omni%20interface/ovis-landing.html
```

## Project Overview

- **Product:** Ovis — AI-powered Instagram growth agent ("Jarvis for Instagram")
- **Brand:** Omni World
- **Stack:** Pure HTML/CSS/JS, no frameworks, no build step
- **Theme:** Silver chrome (`#A8ADB8` background, `#080810` text, `#1A58A0` blue)
- **Email capture:** Formspree endpoint `https://formspree.io/f/mpqyergz`
- **Domain:** omniworld.app (not yet deployed)

## Phase Tracking

- [x] Phase 1: Finish Ovis landing page
- [ ] Phase 2: Content machine (user will provide video transcript)
