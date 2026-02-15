# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **AI Automation Basingstoke** (aiautomationbasingstoke.co.uk), a satellite SEO site in the "Hampshire Domination" network. It's part of a geographically-targeted local SEO strategy for AI automation services, operated by Antek Automation.

**Domain:** aiautomationbasingstoke.co.uk
**Brand:** Basingstoke AI Automation (or similar - verify in index.html)
**Parent Company:** Antek Automation (antekautomation.com)
**Target Area:** Basingstoke, Hampshire, and surrounding towns

### Satellite Site Network

This site is one of several Hampshire-focused satellites:
- aiautomationandover.co.uk (base template)
- aiautomationportsmouth.co.uk
- aiautomationsouthampton.co.uk
- **aiautomationbasingstoke.co.uk** (this site)
- aiserviceswinchester.co.uk
- aiautomationfarnborough.co.uk
- aiserviceshampshire.co.uk (regional hub)

## Tech Stack

**Static HTML site with zero build tooling:**
- Single `index.html` with inline CSS and vanilla JavaScript
- No frameworks, no dependencies, no build step, no package.json
- Google Fonts (Sora + DM Sans) loaded asynchronously
- Cal.com embedded booking widget
- n8n webhook for contact form submissions

**JavaScript Features:**
- IntersectionObserver for scroll-reveal animations
- FAQ accordion (single-open-at-a-time pattern)
- Animated stat counters with easing
- Contact form submission to n8n webhook
- Mobile navigation toggle
- Waveform animation (24 bars with staggered delays)

**No Git Repository Yet:** This site hasn't been initialized with git. When ready to commit, follow the git workflow in [SATELLITE_BUILD_INSTRUCTIONS.md](SATELLITE_BUILD_INSTRUCTIONS.md#git--github-process).

## File Structure

```
.
├── index.html                         # Complete single-page site
├── privacy-policy.html                # Privacy policy page
├── terms.html                         # Terms & conditions page
├── robots.txt                         # Search engine crawl rules
├── sitemap.xml                        # XML sitemap
├── images/
│   └── bolt.png                       # Bolt Electrical case study image
├── SATELLITE_BUILD_INSTRUCTIONS.md    # Detailed transformation guide
├── CLAUDE.md                          # This file
└── README.md                          # Project documentation
```

## Critical: Content Uniqueness Requirements

**SEO Penalty Risk:** Google penalizes duplicate content across domains. Every satellite site MUST have unique copy in key sections to avoid penalties and keyword cannibalization.

### Sections That MUST Be Unique (see SATELLITE_BUILD_INSTRUCTIONS.md for details)

1. **Hero subheadline** — completely rewritten with local landmarks
2. **Pain points subtitle** — different sentence structure, city-specific examples
3. **Pain point card descriptions** — all 3 reworded with Basingstoke context
4. **Services subtitle** — unique wording with local business examples
5. **Industries subtitle** — references local business vibe
6. **Why Us local card** — completely rewritten from scratch
7. **All FAQ answers** — same questions, different wording/structure (16 answers)
8. **GEO/AI statement** — same info, different expression

### Test for Uniqueness
Before committing changes, read this site and Portsmouth side-by-side. If any paragraph sounds identical or uses the same sentence patterns, rewrite it. Content should read as if freshly written, not templated.

## Key Development Commands

**No build commands needed.** This is a static HTML site.

### Local Development
```bash
# Serve locally (any method works)
python3 -m http.server 8000
# or
npx serve .
# or
open index.html  # Direct file:// preview
```

### Deployment
No build step required. Deploy entire directory to:
- **GitHub Pages** — enable in repo settings after push
- **Netlify** — publish directory: `/`
- **Vercel** — framework preset: Other
- **Any static host** — upload all files

### Git Workflow (when ready)
```bash
# Initialize repository
git init
git add .
git commit -m "Initial commit: Basingstoke AI satellite site

- Basingstoke-specific branding and content
- Unique copy throughout to avoid duplicate content penalties
- SEO optimized for Basingstoke & Hampshire
- JSON-LD structured data with Basingstoke geo coordinates
- Cross-links to Hampshire satellite network

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# Create GitHub repo first, then:
git remote add origin https://github.com/USERNAME/REPO.git
git branch -M main
git push -u origin main
```

## Architecture & Implementation Patterns

### Single-File Architecture
All HTML, CSS, and JavaScript are inline in `index.html`. This approach:
- Eliminates build tooling complexity
- Ensures instant page load (no render-blocking external resources except fonts)
- Makes deployment trivial (just upload files)
- Keeps all code searchable in one place

### CSS Architecture
Custom properties (CSS variables) define the design system:
```css
--bg-primary: #0a0f1c;        /* Dark background */
--bg-secondary: #0f1729;      /* Secondary dark */
--text-primary: #f8fafc;      /* White text */
--text-secondary: #cbd5e1;    /* Gray text */
--accent-primary: #3b82f6;    /* Blue */
--accent-secondary: #06b6d4;  /* Cyan */
--success: #10b981;           /* Green (CTAs) */
```

**CTA Styling:** All primary CTAs use solid green (`#10b981`) background with black text — do not change this brand pattern.

### JavaScript Patterns

**Vanilla JS only** — no jQuery, no frameworks. Key patterns:
- IntersectionObserver for performance-efficient scroll animations
- Single-open accordion pattern (auto-close siblings)
- Eased counter animations (cubic ease-out)
- Form submission via fetch() to n8n webhook

### SEO Implementation

**Structured Data (JSON-LD):**
- LocalBusiness schema with geo coordinates
- Organization schema with parent company reference
- FAQPage schema (16 questions)

**Key SEO Elements:**
- Semantic HTML5 with proper heading hierarchy (single h1, logical h2/h3)
- Meta descriptions under 155 characters
- Titles under 60 characters
- Open Graph and Twitter Card meta tags
- Canonical URLs
- Geo meta tags (geo.region, geo.position, ICBM)
- UK English spelling throughout

**Target Keywords:** Naturally woven into copy (avoid keyword stuffing):
- AI voice agents Basingstoke
- AI automation Basingstoke
- Chatbots Hampshire
- Business automation Basingstoke
- AI receptionist
- Automated phone answering

## Making Changes to This Site

### For Content/Copy Updates

**Always reference [SATELLITE_BUILD_INSTRUCTIONS.md](SATELLITE_BUILD_INSTRUCTIONS.md)** for:
- Exact variable values for Basingstoke (geo coordinates, nearby towns, local landmarks)
- Content uniqueness guidelines
- Section-by-section transformation checklist
- Quality control checklist before deployment

### For Design/CSS Changes

**CRITICAL:** Design must stay identical across all satellite sites. If making a CSS change:
1. Verify it doesn't break the established brand pattern
2. Consider applying it to all satellites in the network
3. Test responsive behavior (320px to 1440px+)
4. Ensure CTAs remain solid green with black text

### For JavaScript Changes

All JavaScript is at the bottom of `index.html` in a `<script>` tag (no external .js files). When modifying:
- Use vanilla JS (no libraries to import)
- Test in modern browsers (IntersectionObserver is ES6+)
- Maintain scroll animation patterns (don't break reveal system)
- Preserve accordion single-open behavior

### For SEO/Schema Changes

**Update all three JSON-LD blocks:**
1. LocalBusiness schema (lines ~42-66)
2. Organization schema (lines ~69-78)
3. FAQPage schema (lines ~81+)

Validate changes at [Google's Rich Results Test](https://search.google.com/test/rich-results).

## Cross-Linking Strategy

**Footer Satellite Links:** Each site links to all other satellites EXCEPT itself. When Basingstoke is live, ensure it's excluded from its own footer satellite list.

**Always Preserve:**
- Links to Antek Automation (parent company)
- Links to retellai.com/partner/antek-automation (certified partner badge)
- Shared phone number: 0333 038 9960

## Contact Form Integration

Form submits to n8n webhook with hidden fields:
```html
<input type="hidden" name="source" value="aiautomationbasingstoke.co.uk">
<input type="hidden" name="city" value="Basingstoke">
```

These fields enable lead source tracking. Update `source` and `city` values if copying to a new satellite.

## Quality Checklist Before Git Commit

Reference the complete checklist in [SATELLITE_BUILD_INSTRUCTIONS.md](SATELLITE_BUILD_INSTRUCTIONS.md#quality-control-checklist), but key items:

- [ ] All variable placeholders replaced (zero `[BRACKETS]` remaining)
- [ ] Brand name consistent throughout
- [ ] Domain correct in all meta tags, canonical, schema, sitemap
- [ ] Geo coordinates accurate for Basingstoke
- [ ] Email address: `hello@aiautomationbasingstoke.co.uk` (or verify actual email)
- [ ] All FAQ answers rewritten for uniqueness
- [ ] Local landmarks and nearby towns mentioned naturally
- [ ] Antek Automation linked in trust bar, Why Us section, footer
- [ ] Retell AI partner link present
- [ ] Footer cross-links exclude current site
- [ ] No horizontal scroll on mobile
- [ ] UK English spelling (favour, optimise, recognised, etc.)
- [ ] JSON-LD validates

## Post-Deployment Actions

After site goes live:
1. Submit to Google Search Console
2. Submit sitemap.xml
3. Request indexing for homepage
4. Set up Google Business Profile (if possible for Basingstoke location)
5. Submit to Bing Webmaster Tools
6. Add link from antekautomation.com
7. Monitor rankings and check for keyword cannibalization between satellites

## Additional Resources

- **Detailed build process:** [SATELLITE_BUILD_INSTRUCTIONS.md](SATELLITE_BUILD_INSTRUCTIONS.md)
- **Base site reference:** aiautomationandover.co.uk
- **Portsmouth example:** aiautomationportsmouth.co.uk (first completed satellite)
- **Parent company:** [antekautomation.com](https://antekautomation.com)

## Notes for AI Assistants

- **Do not create unnecessary files** — everything goes in the existing HTML files
- **Preserve inline architecture** — don't suggest extracting CSS/JS to separate files
- **Content uniqueness is paramount** — never copy/paste paragraphs from other satellites
- **UK English only** — colour not color, optimise not optimize
- **Maintain brand consistency** — green CTAs, dark premium theme, animations
- **No framework migrations** — this is intentionally vanilla HTML/CSS/JS
