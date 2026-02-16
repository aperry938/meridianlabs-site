# Meridian Labs Website — Handoff Document
**Last Updated:** February 16, 2026
**Repo:** `aperry938/meridianlabs-site` (Cloudflare Pages — deploys on push to `main`)
**Local:** `~/Desktop/meridianlabs-site/`
**Live URL:** https://meridianlabs.us

---

## Current State (as of commit `946686c`)

### What's Working
- **Hero section:** Compact layout with panoramic neural network banner, animated gradient "Guaranteed." text, glow orb, counter animations, dark mountain region framing CTA buttons
- **Tab navigation:** 4 brand tabs (IT & Cybersecurity, Healthcare, Professional, Beauty) with brand-colored styling
- **Horizontal scroll carousel:** App cards with scroll-snap, fade indicators, and arrow buttons for desktop scroll affordance
- **20 app cards** across 4 brands (10 live/skeleton + 10 "Launching Soon" placeholder)
- **Subpages:** methodology.html, privacy.html, terms.html, support.html — all with standardized footers, body.loaded reveal, noscript fallback
- **Mobile responsive:** Hamburger menu, scaled cards, tab sizing, arrows hidden on mobile
- **Accessibility:** `prefers-reduced-motion`, ARIA roles, noscript fallback, focus-visible
- **Deployed** to Cloudflare Pages via push to `main`

### What Needs Review / Potential Issues
1. **Mobile device testing** — verify horizontal scroll, snap, and fade indicators on iOS Safari + Android Chrome
2. **iPad testing** — verify layout at tablet widths (768-1024px)
3. **"Launching Soon" links** — all placeholder app badges link to `#` — will need real store links when apps launch
4. **Card width** — 220px desktop / 180px mobile may need tuning based on user feedback
5. **Hero image size** — panoramic banner is ~3MB (was 738KB) — could benefit from WebP conversion/compression

---

## What Still Needs to Be Done

### High Priority
- [ ] **Real store links** for live apps (Esthetics, Cosmetology, Barber, Nail Tech on App Store/Play Store)
- [ ] **PTCB, ASVAB, SecAI+** — update badges from "Launching Soon" to actual store links once live
- [ ] **Mobile device testing** — iOS Safari + Android Chrome
- [ ] **iPad testing** — tablet widths (768-1024px)

### Medium Priority
- [ ] **App card store badges** — small App Store / Play Store download icons on live app cards
- [ ] **Analytics** — Cloudflare Web Analytics or similar (privacy-first, no cookie consent needed)
- [ ] **Performance audit** — hero banner (3MB) + 10 placeholder JPEG icons not optimized (convert to WebP, compress)
- [ ] **OG image** — currently uses the hero background; consider a designed social sharing image
- [ ] **Methodology page styling** — verify it still looks good after all CSS changes (has its own hero background now)

### Low Priority
- [ ] **Footer brand links** — currently link to `#brand-it` etc. anchors; should also trigger the tab switcher JS
- [ ] **SEO** — individual app landing pages would help search rankings per exam
- [ ] **Favicon** — verify favicon-32.png and apple-touch-icon.png are current

---

## File Structure

```
meridianlabs-site/
├── index.html              ← Main homepage
├── style.css               ← All styles (cache-busted via ?v=7)
├── methodology.html        ← Methodology deep-dive page
├── privacy.html            ← Privacy policy
├── terms.html              ← Terms of use
├── support.html            ← Support/FAQ page
├── HANDOFF.md              ← This file
├── CHANGELOG.md            ← Version history
├── images/
│   ├── MeridianLabs_header.jpg   ← Hero background (panoramic neural streams)
│   ├── founder-headshot.png       ← Founder photo
│   ├── esthetics-icon.png         ← Live app icons (10)
│   ├── cosmetology-icon.png
│   ├── barber-icon.png
│   ├── nailtech-icon.png
│   ├── ptcb-icon.png
│   ├── asvab-icon.png
│   ├── secai-icon.png
│   ├── securityplus-icon.png
│   ├── snowflake-icon.png
│   ├── itil5-icon.png
│   ├── aplus-icon.jpeg            ← Placeholder icons (10)
│   ├── awsaip-icon.jpeg
│   ├── awscp-icon.jpeg
│   ├── cannabis-icon.jpeg
│   ├── cma-icon.jpeg
│   ├── cna-icon.jpeg
│   ├── insurance-icon.jpeg
│   ├── networkplus-icon.jpeg
│   ├── pmp-icon.jpeg
│   └── teas-icon.jpeg
├── favicon-32.png
├── apple-touch-icon.png
└── google9773f108dd372ff3.html   ← DO NOT DELETE (Google verification)
```

**Hero banner candidates archived at:** `meridian-labs/branding/website-heroes/`

---

## Key CSS Architecture

| Concept | Implementation |
|---------|---------------|
| **Gradient text** | `.hero-gradient-text` — `background-clip: text` with animated `background-position` |
| **Glow orb** | `.hero-content::before` — radial gradient pseudo with pulse keyframe |
| **Tab system** | `.app-tab` buttons + `.brand-section` show/hide via `.brand-section-active` |
| **Horizontal scroll** | `.apps-grid` — `display: flex; overflow-x: auto; scroll-snap-type: x mandatory` |
| **Scroll fades** | `.apps-grid-wrapper::before/::after` — gradient overlays toggled by `scroll-start`/`scroll-end` classes |
| **Scroll arrows** | `.scroll-arrow` — glass circle buttons, auto-show/hide based on scroll position, hidden on mobile |
| **Hero layout** | Compact padding (72px/36px), `background-position: center bottom`, 60px bottom gradient |
| **Drop shadow on gradient text** | Use `filter: drop-shadow()` NOT `text-shadow` (incompatible with `-webkit-text-fill-color: transparent`) |
| **Cache busting** | `style.css?v=7` in `<link>` tag — increment on CSS changes |
| **Reduced motion** | All animations stopped, opacity forced to 1, transforms removed |

---

## JavaScript Functions

| Function | Purpose |
|----------|---------|
| Page load reveal | Adds `.loaded` class to body |
| Scroll reveal | IntersectionObserver adds `.visible` to `.scroll-reveal` elements with stagger |
| Stat counters | Animated count-up on hero stats when visible |
| Mobile menu | Hamburger toggle with Escape key close |
| Tab switcher | Shows/hides brand sections, re-triggers scroll reveal |
| Scroll fade | Updates `scroll-start`/`scroll-end` classes on `.apps-grid-wrapper` |
| Scroll arrows | Click handlers for `.scroll-arrow` buttons — smooth scroll 480px per click |
