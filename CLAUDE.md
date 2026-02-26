# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static single-page HTML visualization of a Balanced Scorecard **Strategy Map** for an accounting/advisory consulting context. The application is entirely self-contained in [index.html](index.html) — no build tools, package manager, or dependencies required.

## Running the App

Open `index.html` directly in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8080
# or
npx serve .
```

## Architecture

The entire application lives in a single [index.html](index.html) (~171 lines) with three sections:

- **Inline CSS** (lines 8–43): Custom styles for `.node`, `.arrow-up`, `.line`, `.highlight`, and hover transitions
- **HTML body** (lines 45–154): Four perspective lanes rendered top-to-bottom (Impact → Klant → Proces → Basis), connected by CSS arrow dividers. Each clickable node calls `showInfo()` inline via `onclick`.
- **JavaScript** (lines 156–169): A single `showInfo(title, text)` function that reveals and populates `#detailBox` at the bottom of the page

**Perspective hierarchy (top to bottom in the UI, cause flows bottom-up):**
1. **Basis** (amber) — Human, Information, Organization capital
2. **Proces** (emerald) — Automated data flow, Real-time reporting
3. **Klant** (blue) — Contextual insights, Strategic partnership
4. **Impact** (purple) — Intellectual, Social, Human capital value

**Styling:** Tailwind CSS loaded via CDN (`https://cdn.tailwindcss.com`). Each perspective uses a color family (amber/emerald/blue/purple) consistently across badge, border, heading, and text colors.

**Interactivity:** Node click → `showInfo()` → unhides `#detailBox` and populates `#detailTitle` / `#detailText`, then smooth-scrolls to it.

## Content Language

All user-facing content is in **Dutch** (nl). Keep new content in Dutch to match the existing application.
