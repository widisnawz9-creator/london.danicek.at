# London & Oxford 2026 - Travel Itinerary Website

A static single-page website for planning and organizing a 4-day trip to London and Oxford (April 30 - May 3, 2026).

## Project Overview

This is a **pure static HTML website** for three travelers (Marion, Markus, Martin) visiting London and Oxford. The site serves as a digital travel companion with day-by-day itinerary, restaurant reservations, interactive checklists, and backup plans.

**Language:** German (all content is in German)  
**Domain:** london.danicek.at  
**Target Date:** April 30 - May 3, 2026

## Technology Stack

| Component | Technology |
|-----------|------------|
| Structure | HTML5 (single file) |
| Styling | CSS3 with CSS Custom Properties (variables) |
| Logic | Vanilla JavaScript (ES6) |
| Fonts | Google Fonts (Fraunces + Outfit) |
| Images | External Unsplash URLs (hot-linked) |
| Hosting | Static (GitHub Pages or similar) |

**No build tools, no package managers, no dependencies.**

## Project Structure

```
.
├── index.html          # Complete website (HTML + CSS + JS) ~1350 lines
├── CNAME               # Domain configuration (london.danicek.at)
└── AGENTS.md           # This file
```

The entire application is contained in a single `index.html` file:
- **Lines 1-762:** CSS styles in `<style>` block
- **Lines 763-1279:** HTML content
- **Lines 1280-1346:** JavaScript in `<script>` block

## Architecture

### 1. Layout Sections

The page uses a tab-based SPA (Single Page Application) navigation:

| Section | ID | Description |
|---------|-----|-------------|
| Tagesplan | `#plan` | Day-by-day itinerary (default) |
| Restaurants | `#restaurants` | All restaurant contacts and links |
| Checkliste | `#checklist` | Interactive to-do and packing lists |
| Backup | `#backup` | Alternative plans and useful links |

### 2. CSS Architecture

Uses CSS Custom Properties for theming:
```css
--cream: #F5F0E8;           /* Background */
--green: #1B3A2D;           /* Primary brand color */
--gold: #B8860B;            /* Accent color */
--terracotta: #C17850;      /* Secondary accent */
--charcoal: #2C2C2C;        /* Text headings */
--text: #3A3530;            /* Body text */
```

Key CSS patterns:
- **BEM-like naming:** `.day-card`, `.timeline-item`, `.checklist-text`
- **Utility classes:** `.tag`, `.btn`, `.priority.high`
- **Responsive breakpoints:** 768px (tablet), 480px (mobile)
- **Print styles:** `@media print` hides nav and adjusts colors

### 3. JavaScript Features

**Navigation:**
```javascript
function showSection(sectionId, btn)
```
- Switches visible section
- Updates active nav button state
- Smooth scroll to navigation

**Checklist Persistence:**
```javascript
function toggleCheck(element)     // Toggle checked state
function saveChecklist()          // Save to localStorage
function loadChecklist()          // Restore from localStorage
```
- Key: `londonChecklist2026`
- Stores array of boolean values for each checklist item

**Countdown Timer:**
```javascript
function updateCountdown()
```
- Calculates days/hours/minutes until trip start (April 30, 2026 18:25)
- Updates every 60 seconds
- Shows "Die Reise hat begonnen!" when trip starts

## Content Organization

### Day Cards Structure

Each day follows this pattern:
```html
<div class="day-card">
    <div class="day-header">
        <h2 class="day-title">Day Name – Activity</h2>
        <span class="day-date">Date</span>
    </div>
    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-time">HH:MM</div>
            <div class="timeline-content">...</div>
        </div>
    </div>
</div>
```

### Tag System

Tags categorize activities:
- `.food` - Meals and dining
- `.drink` - Bars, cafes, cocktails
- `.transport` - Flights, trains, tubes
- `.highlight` - Special recommendations

## Development Guidelines

### Making Changes

1. **Edit `index.html` directly** - no build step required
2. **Test locally** by opening the file in a browser
3. **Deploy** by pushing to the hosting repository

### Adding a New Day

1. Copy an existing `.day-card` block
2. Update `.day-title` and `.day-date`
3. Add `.timeline-item` elements for each activity
4. Use appropriate tags (`.tag`, `.tag.food`, etc.)
5. For images, use Unsplash URLs with `?w=800` parameter

### Adding Checklist Items

1. Find the checklist section (`id="checklist"`)
2. Add a `.checklist-item` div:
```html
<div class="checklist-item" onclick="toggleCheck(this)">
    <div class="checkbox"></div>
    <div class="checklist-text">
        <h4>Title</h4>
        <p>Description</p>
    </div>
    <span class="priority high">Priority Label</span>
</div>
```
3. Priority classes: `.high`, `.medium`, `.low`

### Styling Conventions

- **Colors:** Always use CSS variables (`var(--green)` not `#1B3A2D`)
- **Spacing:** Use rem units (1rem = base font size)
- **Borders:** 2px radius (subtle rounding)
- **Shadows:** Use `--shadow` or `--shadow-deep` variables

## Deployment

### Current Setup

- **Domain:** london.danicek.at (configured in `CNAME`)
- **Hosting:** Likely GitHub Pages (repository-based)
- **SSL:** Automatic (if using GitHub Pages or Cloudflare)

### Deployment Steps

1. Commit changes to repository
2. Push to main/master branch
3. Changes are live within minutes

No CI/CD pipeline, no build artifacts to generate.

## Browser Compatibility

Targets modern browsers with:
- CSS Grid (`display: grid`)
- CSS Custom Properties
- ES6 JavaScript
- `localStorage` API

Tested/supported:
- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers (iOS Safari, Chrome Android)

## Testing Checklist

Before committing changes:
- [ ] Site loads without console errors
- [ ] Navigation tabs work correctly
- [ ] Checklist items toggle and persist (test localStorage)
- [ ] Countdown displays correctly
- [ ] Responsive layout works on mobile (320px+)
- [ ] Print preview shows all sections
- [ ] External images load (Unsplash URLs valid)
- [ ] All restaurant reservation links work

## Security Considerations

- **No user input** - all content is static
- **No backend** - no database or server-side code
- **External resources:** Google Fonts and Unsplash images (HTTPS)
- **localStorage:** Only stores checklist state, no sensitive data

## External Dependencies

| Resource | URL | Purpose |
|----------|-----|---------|
| Google Fonts | fonts.googleapis.com | Fraunces & Outfit fonts |
| Unsplash | images.unsplash.com | Location photos |

All external resources use HTTPS and have no authentication requirements.

## Key Dates & Times

| Event | Date/Time | Location |
|-------|-----------|----------|
| Arrival | April 30, 2026 18:25 | London Heathrow (BA 795) |
| Hotel Check-in | April 30, 2026 ~21:00 | The Z Hotel Victoria |
| Mamma Mia Musical | May 1, 2026 19:30 | Novello Theatre |
| Oxford Day Trip | May 2, 2026 | Christ Church, Punting |
| Departure | May 3, 2026 17:15 | London Heathrow (BA 794) |

---

*Last updated: March 2026*
