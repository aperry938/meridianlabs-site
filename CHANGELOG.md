# Meridian Labs Website — Changelog

All notable changes to [meridianlabs.us](https://meridianlabs.us) are documented here.

---

## [2026-02-16] Hero Polish & Scroll Arrows
**Commit:** `946686c`

### Changed
- **Hero banner:** Swapped to panoramic neural network streams image (dark mountain range at bottom)
- **Hero layout tightened:** Padding reduced to 72px/36px (desktop), 56px/28px (mobile) to make section more compact
- **Background position:** Changed to `center bottom` so dark mountains frame the CTA buttons
- **Tagline readability:** Bumped to `rgba(255, 255, 255, 0.92)` with `text-shadow` for contrast against busy background
- **Trust band spacing:** Reduced padding to 10px (was 20px) to close gap between CTA and trust pills
- **Stats margin:** Tightened to 24px (was 32px)
- **Bottom gradient fade:** Reduced to 60px (was 120px)

### Added
- **Carousel scroll arrows:** Glass-morphism circle buttons with accent-colored chevrons on desktop
  - Auto-show/hide based on scroll position (uses existing `scroll-start`/`scroll-end` classes)
  - 480px smooth scroll per click
  - Hidden on mobile (< 768px) where swipe is natural
- **Cache busting:** Incremented to `style.css?v=7`

---

## [2026-02-16] Methodology Hero Background
**Commit:** `acfcfa5`

### Changed
- Replaced methodology page hero background with matching neural network image
- Consistent visual language across homepage and methodology page

---

## [2026-02-16] Remove Demo Section
**Commit:** `c292ee1`

### Removed
- Interactive confidence calibration demo section from homepage
- Simplified page flow: Hero → Trust Band → Apps → Engine → About → Founder → Footer

---

## [2026-02-16] Fix Blank Subpages
**Commit:** `dad7897`

### Fixed
- Subpages (methodology, privacy, terms, support) were blank on load — missing `body.loaded` class toggle
- Added `document.body.classList.add('loaded')` and `<noscript>` fallback to all subpages

---

## [2026-02-16] Standardize Footers
**Commit:** `3653b4b`

### Fixed
- Standardized footer HTML across all subpages to match homepage footer
- Fixed broken links on subpages (relative paths, missing hrefs)

---

## [2026-02-16] Fix Broken Links
**Commit:** `dc6e924`

### Fixed
- Relative path links that 404'd on subpages
- Footer brand tab links now properly anchor to homepage sections
- Contact/support link corrections

---

## [2026-02-16] Tab Color Improvements
**Commit:** `14a89cd`

### Changed
- IT & Cybersecurity tab: updated to electric blue for better brand distinction
- Healthcare tab: updated to green-teal
- Better visual separation between brand categories

---

## [2026-02-16] CSS Cache Fix & SVG Hardening
**Commit:** `e9f0c29`

### Fixed
- Added `?v=` cache-busting query parameter to stylesheet link (prevents stale CSS after deploys)
- Hardened trust band SVG icons (inline SVGs instead of external references)

---

## [2026-02-16] Major Site Redesign
**Commit:** `0fc1125`

### Added
- **Two-line hero headline:** "Pass Your Exam." / "Guaranteed." with animated gradient text
- **Glow orb:** Pulsing radial gradient behind headline
- **Tab-based app filtering:** 4 brand tabs (IT, Healthcare, Professional, Beauty) with brand-colored styling
- **Horizontal scroll carousel:** Flex layout with scroll-snap for app cards
- **Scroll fade indicators:** Gradient overlays that show/hide based on scroll position
- **10 placeholder apps** from expansion roadmap (A+, AWS AIP, AWS CP, Network+, CNA, CMA, TEAS, Insurance, Cannabis, PMP)
- **10 new app icons** copied from future_builds
- **Vision section SVG icons** replacing emoji icons
- **Badge glow animation** for "Launching Soon" badges
- **Footer and engine section** gradient accent lines

### Changed
- Stats updated: 10→20 apps, 25K→55K+ questions (meta, OG, JSON-LD, hero, trust band)
- Secondary text color: `#8b92a5` → `#9ba2b5` (better contrast)
- Trust band opacity: 0.65→0.80 base, 0.85→1.0 hover
- App card text line-height: 1.5→1.6
- Founder card glow strengthened
- Hero background opacity: 0.35→0.20

### Removed
- Standalone "Audience Routing" section (replaced by tab navigation)
- Conflicting `.apps-grid-4` CSS grid rules

---

## [2026-02-16] Pre-Redesign Cleanup
**Commit:** `7526080`

### Changed
- Removed hero icon image
- Cleaned up footer (removed personal links, streamlined for commercial site)

---

## [2026-02-16] Initial Banner
**Commit:** `0334b97`

### Added
- Hero background banner image
- Centered icon in hero section

---

## [2026-02-15] Initial Site
**Commit:** `93f9a3b`

### Added
- Initial Meridian Labs commercial website
- Homepage with company overview, app showcase, methodology summary
- Privacy policy, terms of use, support pages
- Methodology deep-dive page
- Google verification file (`google9773f108dd372ff3.html`)
- Cloudflare Pages deployment configuration
