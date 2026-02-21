# 🌸 Bloom — Your Pregnancy Companion

A beautifully designed, single-file pregnancy tracking web app built with vanilla HTML, CSS, and JavaScript. Bloom provides week-by-week pregnancy information, symptom tracking, appointment management, and baby development data — all wrapped in a warm, elegant interface.

## Features

**Home Dashboard**
- Animated week circle displaying the current pregnancy week and baby size comparison (e.g., "🥑 Avocado")
- Trimester progress bar with days elapsed and days remaining
- Weekly development updates covering key milestones
- Interactive symptom tracker with toggle buttons
- Upcoming appointments and daily health tips

**Baby Page**
- Week-by-week baby weight and length estimates
- Development milestone checklist
- Fun facts about the baby's current stage of growth

**Calendar Page**
- Full interactive monthly calendar with navigation
- Appointment dates highlighted visually

**Health Page**
- Doctor and clinic contact information pulled from the user's profile

**Profile Page**
- Personal profile display (name, current week, due date, doctor/clinic)
- Editable via an onboarding/auth overlay

## Getting Started

No installation or build step required. Just open the file in any modern web browser:

```bash
open pregnancy-platform.html
```

Or simply double-click the file in your file explorer.

On first load, an onboarding overlay will prompt you to enter:
- Your name
- Current pregnancy week (1–40)
- Due date
- Doctor's name
- Clinic name

This data is saved to `localStorage` so your profile persists between sessions.

## Tech Stack

| Layer | Technology |
|---|---|
| Structure | HTML5 |
| Styling | CSS3 (custom properties, grid, flexbox, animations) |
| Logic | Vanilla JavaScript (ES6+) |
| Fonts | Google Fonts — Cormorant Garamond & DM Sans |
| Storage | Browser `localStorage` |

No frameworks, no build tools, no dependencies beyond Google Fonts.

## Project Structure

The entire application lives in a single file (`pregnancy-platform.html`) with the following internal sections:

```
pregnancy-platform.html
├── <head>          — Meta, fonts, CSS custom properties & all styles
├── <body>
│   ├── Auth overlay     — Onboarding / profile edit modal
│   ├── Header           — Logo and current date
│   ├── Pages
│   │   ├── #page-home    — Main dashboard
│   │   ├── #page-calendar
│   │   ├── #page-baby
│   │   ├── #page-health
│   │   └── #page-profile
│   └── Bottom nav       — Fixed tab bar for page switching
└── <script>        — All application logic
    ├── Auth / localStorage helpers
    ├── Baby size & milestone data (weeks 1–40)
    ├── updateUI()        — Renders week-specific content
    ├── Page loaders      — loadCalendar(), loadBabyPage(), etc.
    └── Event listeners
```

## Customisation

**Colour palette** — All colours are defined as CSS custom properties at the top of the `<style>` block and can be changed in one place:

```css
:root {
  --rose: #E8B4B8;
  --blush: #F5D6D8;
  --cream: #FDF6F0;
  --sage: #8BAF8D;
  --terracotta: #C97B62;
  --warm-dark: #3D2C2C;
}
```

**Appointment dates** — Hardcoded appointment days in `loadCalendar()` can be replaced with dynamic data or a local array stored in `localStorage`.

**Weekly content** — The `weekUpdates` and `babyFunFacts` objects in the `<script>` section contain all week-by-week text. Edit or extend these to customise the content shown at any week.

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires JavaScript enabled and access to Google Fonts for the intended typography.

## Notes

- All user data is stored locally in the browser via `localStorage`. Nothing is sent to a server.
- The app is locale-aware for date formatting (currently set to `en-IN`). Change the locale string in `toLocaleDateString()` calls if needed.
- Appointment highlighting in the calendar uses a static array (`['26', '5', '14']`) as a placeholder — this can be wired up to a real data source.
