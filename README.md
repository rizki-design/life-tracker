<div align="center">

# [Life & Body Tracker](https://rizki-design.github.io/life-tracker)

**A personal weekly discipline tracker built around one principle: recovery speed matters more than streak length.** 

![Version](https://img.shields.io/badge/version-1.2.4-4C9ADE?style=flat-square)
![Platform](https://img.shields.io/badge/platform-PWA-5DAE63?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-E8A435?style=flat-square)
![No Backend](https://img.shields.io/badge/backend-none-1B8A5A?style=flat-square)

</div>

## About

Life & Body Tracker is a lightweight, installable Progressive Web App for tracking weekly objectives and body weight on a 52-week calendar. It was built to solve one very specific failure mode: the all-or-nothing spiral where a single missed day becomes a justification for abandoning the entire week.

Most habit trackers reward streaks. This one rewards **bouncing back**.

The app intentionally limits itself to a single HTML file, no build step, no backend, no account, no analytics, no tracking. Your data lives in your browser's local storage and goes nowhere else. You can export it as JSON and restore it on any device.

### Core Philosophy

> **The metric isn't your streak. It's how fast you get back up.**

Every design decision reflects this. Verdicts are soft, not punitive. A "Recovered" week is celebrated, not apologized for. The year overview shows momentum, not perfection.

---

## Features

### Life Tracker
- **Custom weekly objectives** with configurable daily targets and maxima
- **Category system** — Body, Mind, Growth — each with their own color family
- **Weekly verdicts** auto-calculated from completion rates, with four tiers:
  - **Locked In** — Every objective maxed out
  - **Solid** — A strong week, most things hit
  - **Recovered** — Slipped but bounced back
  - **Spiraled** — A rough week, it happens
- **Manual verdict override** — Tap any verdict to reflect how the week actually felt. You know the context better than the math does.
- **Per-week snapshots** — Changes to objectives only affect future weeks. Past weeks stay locked to whatever you were tracking at the time.
- **Rotating motivational copy** — 10+ evidence-informed messages per verdict tier, served based on week number.

### Body Tracker
- **Daily weight logging** with a tap-to-log UX and drag slider for fast entry
- **Target-relative status** — "On Track" / "Over Target" / "Under Target" based on proximity to your goal
- **Progress chart** with smart adaptive X-axis labeling and auto-tightening Y-axis
- **Time range selector** — Week, 1M, 3M, 6M, All views with anchor-aware filtering (historical weeks anchor to that week's end, not today)
- **Week-over-week trend colors** in the year overview (Dropped / Maintained / Gained)

### Shared
- **Journal** — Auto-sizing, serif-typeset weekly reflection space that persists across modes
- **Year Overview** — 52-week calendar grid with tier-colored cells and an inline stats legend
- **Dark / Light theme** with a single-tap toggle
- **Fully installable PWA** — Add to home screen on any modern mobile browser
- **Offline-first** — Service worker caches all assets, works without a connection
- **Data portability** — Copy/paste JSON export and import, no files required

---

## Tech Stack

- **React 18** via CDN (no build step)
- **Babel Standalone** for in-browser JSX compilation
- **Vanilla CSS** with CSS variables for theming
- **localStorage** for persistence
- **Service Worker** for offline support and PWA installability
- **Single `index.html` file** — roughly 80KB, zero dependencies

The entire application is one file by design. No bundler, no npm install, no deployment pipeline. Edit, reload, commit.

---

## Design Principles

### All-or-nothing is the enemy
The app explicitly counter-programs catastrophizing. A missed objective is data, not a verdict. The verdict override system exists because giving users agency over their own narrative matters more than mathematical purity.

### Information architecture over decoration
Weekly and yearly views are designed to communicate at-a-glance state. Colors map to emotional meaning (green = progress, amber = recovery, red = spiral, emerald = mastery). The Year Overview legend doubles as a stats summary so two UI surfaces become one.

### Respect the user's attention
No notifications. No streaks to guilt you. No daily engagement metrics. The app opens, shows you where you stand, and gets out of the way.

### Progressive disclosure
Settings, objective editing, and verdict overrides are all one tap away, but never in your face. The default experience is "see your week, mark your dots, move on."

---

## Installation

### Use the live app
Open [https://rizki-design.github.io/life-tracker](https://rizki-design.github.io/life-tracker) on any modern mobile browser and tap "Install" / "Add to Home Screen." The PWA will install with its own icon and open full-screen without browser chrome.

### Run your own copy
```bash
git clone https://github.com/rizki-design/life-tracker.git
cd life-tracker
# Serve any way you like — no build step
python3 -m http.server 8000
```
Open `http://localhost:8000` in a browser. That's it.

### Fork and customize
The entire app is `index.html`. Edit it directly. Objective categories, default objectives, color palette, motivational messages, and verdict thresholds are all defined at the top of the file as plain constants.

---

## Data Format

Your data is stored under the `lt-v9` localStorage key as JSON:

```json
{
  "weeks": {
    "w15": {
      "counts": { "cardio": 5, "gym": 2 },
      "objectives": [
        { "id": "cardio", "label": "Morning Cardio", "category": "body", "target": 5, "max": 7 }
      ],
      "verdictOverride": "solid"
    }
  },
  "notes": { "w15": "Rough start but recovered by Thursday." },
  "theme": "dark",
  "bodyData": {
    "entries": { "w15": [{ "day": 0, "kg": 82.5 }] },
    "target": 75,
    "height": 170
  }
}
```

Export via Settings → Export Data. Import via Settings → Restore from Backup. The format tag (`_format: "life-body-tracker"`) is validated on import.

---

## Roadmap

- [ ] Cross-device sync (currently manual via export/import)
- [ ] Import/Sync with body scanner data Chart expansion with more metrics (BF%, muscle mass, measurements)
- [ ] Weekly / monthly check-in flow for setting upcoming priorities
- [ ] Custom objective icons
- [ ] Light mode refinements

---

## License

MIT — do whatever you want with it, just don't blame me.

*Built with intent, not velocity.*

</div>
