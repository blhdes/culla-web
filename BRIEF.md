# Culla Web — Project Brief

Reference document for building the `culla-web` landing page. Contains all design decisions, copy, and context agreed upon before development started.

---

## Project context

**What this is**: A single-page website that serves two purposes simultaneously:
1. Product landing page for Culla (iOS app)
2. Hosted Privacy Policy (required by Apple for App Store submission)

**Final URL**: `culla.app`
**Privacy Policy URL for Apple**: `culla.app/#privacy`
**Hosting**: Netlify (free tier) pointing to a custom domain
**Repo**: Public GitHub repo (`culla-web`)
**Language**: English only (matches app's v1.0 language)

---

## The app — what Claude needs to know

**Name**: Culla
**Bundle ID**: `agu.culla`
**Category**: Photo & Video
**Developer**: Alejandro Gómez Urrea — agomezurrea@gmail.com
**Platform**: iOS, built entirely in Swift, follows Apple HIG as dogma

**What it does**: A swipe-based photo library organizer. Users go through their camera roll one photo at a time — swipe in four directions to sort, dismiss, favorite, or keep. Everything happens on-device, no cloud, no accounts.

**Core philosophy**:
- Local-first, private by architecture (not just policy)
- No gamification, no streaks, no productivity metrics
- Meditative, unhurried — the gesture disappears and you're just making decisions
- "Not a tool. Not a chore. An old photo album on a Sunday afternoon."

---

## Visual identity

**Icon**: Neon-glowing stack of photo cards on a near-black background. 3D render feel, very "glow" — emits light rather than reflects it.

**Color palette — two layers**:

*The canvas is quiet:*
- System backgrounds, semantic text colors, ultraThinMaterial glass
- Intentionally neutral — disappears so the photo stays the hero

*The accents are electric:*
- 10-color neon palette: hot pink, bright blue, neon green, electric purple, vivid yellow, orange, cyan, deep red, lime, magenta
- Each with hand-tuned light and dark mode variants
- Random accent color per session — each launch feels slightly different
- Each gallery gets its own color

*Swipe feedback uses color semantically*:
- Red = dismiss
- Yellow = favorite
- Blue = share
- Green = keep

**Palette philosophy**: neutral until it matters, then unmistakably vivid.

**Suggested CSS variables for the web**:
```css
--bg:      #080808;
--text:    #f0ece5;
--muted:   #6e6b65;
--pink:    #ff2d6b;
--blue:    #00aaff;
--green:   #2dff8a;
--purple:  #9b5fff;
```

**Typography direction**: Pair a serif display font (elegant, editorial — e.g. Cormorant Garamond) with a clean sans-serif body font. The contrast between delicate serif headings and neon accents mirrors the app's visual tension.

**Overall aesthetic**: Dark room where photos glow. The page is dark mode by default (not as an option). Color appears only when it means something. Grain overlay, ambient glow. Quiet until it isn't.

---

## Page structure

Single scrolling page with these sections in order:

### 1. Nav
- Logo: "Culla" (display font)
- App Store badge (top right, hidden on mobile)

### 2. Hero
- App icon (large, floating animation, glow shadow)
- H1: *"Your memories deserve better than scrolling past them."*
- Subhead: calm + private, one photo at a time, nothing leaves your phone
- App Store badge (primary CTA)

### 3. The Feeling
Label: "The feeling"
Quote (display font, italic):
> "Not a tool. Not a chore. An old photo album on a Sunday afternoon."

Body: ~2 short paragraphs on the emotional experience. Not features — the feeling. The Sunday afternoon, the ritual, the lack of pressure.

### 4. Features (4 cards)
Label: "Built with care"
Each card: dark surface, neon left border (each card its own color), icon + title + 2-line description.

| # | Color | Icon | Title | Core message |
|---|-------|------|-------|--------------|
| 1 | Pink  | 🔒 | Nothing leaves your phone | Zero networking code. Privacy by architecture, not policy. |
| 2 | Blue  | 👆 | Swipe as muscle memory | 4 directions, haptic feedback, no buttons to hunt for. |
| 3 | Green | ↩︎ | No guilt, no pressure | Full undo stack. "Dismissed" not "deleted." You can't mess this up. |
| 4 | Purple | ✦ | Your galleries are yours | Custom names, colors, icons. Curating your life, not file management. |

### 5. Privacy Policy
Anchor: `id="privacy"`
Label: "Privacy Policy"
Title (display font): *"Your photos stay on your device. Always."*

Sections:
- Intro paragraph (no server, no account, no analytics)
- **What we collect**: Nothing.
- **Photo library access**: Referenced by asset identifier only. Never copied, moved, or uploaded. Revocable in iOS Settings.
- **Data storage**: SwiftData, local only, removed on uninstall.
- **Third parties**: No SDKs, no analytics, no ad networks, no tracking.
- **Changes**: Will be posted at this URL.
- Meta: "Last updated: March 2026 · agomezurrea@gmail.com"

### 6. Footer
- Logo "Culla" (large, dim — almost a watermark)
- App Store badge
- "Built with ❤️ from Barcelona"
- agomezurrea@gmail.com (mailto link)
- © 2026 Culla · Privacy Policy (anchor link)

---

## Copy bank — emotional hooks

Use these as references for any copy decisions. They were developed alongside the app:

1. **"Nothing leaves your phone"** — trust through absence. No privacy policy needed because no privacy-violating code exists.
2. **"Your camera roll, without the chaos"** — the swipe loop turns a dreaded chore into something meditative.
3. **"Swiping as muscle memory"** — after 30 seconds, hands know the system. The gesture disappears; you're just making decisions.
4. **"Going back in time"** — the date picker is a time machine. "From the very first photo." "On This Day."
5. **"No guilt, no pressure"** — full undo stack, "Dismissed" not "Deleted", "Keep Going" not "You didn't finish."
6. **"Your galleries are yours"** — custom names, colors, icons. Swiping into a glowing neon panel labeled with your word.
7. **"A fresh start every time"** — random session accent color. Each launch is slightly different.

Hero tagline (final):
> *"Your memories deserve better than scrolling past them."*

---

## Technical notes

- Pure HTML/CSS/JS — no framework, no build step, no dependencies (except Google Fonts)
- App icon: `icon.png` in root directory
- App Store badge `href`: placeholder `#` until App Store URL is available
- Scroll reveal: IntersectionObserver (no library)
- Mobile: single-column layout, nav badge hidden
- The file delivered as `index.html` is the complete starting point — ready to drop into the repo

---

## What's still pending

- [ ] Purchase `culla.app` domain
- [ ] Connect domain to Netlify
- [ ] Replace App Store badge `href="#"` with real App Store URL once live
- [ ] Add real `icon.png` to repo root (use the neon glow icon)
- [ ] Update "Last updated" date in privacy policy if needed before submission
