# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page CV/landing page for Andreas Lang, a Junior QA Engineer graduating from Metropolia in January 2026. The site is built as a static HTML page with inline CSS and is designed to be QR-code friendly (minimal scrolling, mobile-first, quick to scan).

## Architecture

- **Single HTML file**: `index.html` contains all markup, styles, and structure
- **No build process**: Pure HTML/CSS, no dependencies or compilation needed
- **Inline CSS**: All styles are embedded in the `<style>` tag within the HTML
- **External dependency**: Font Awesome 6.4.0 CDN for icons (LinkedIn, GitHub, email, phone, etc.)

## Key Design Principles

1. **Responsive Design**: Mobile-first approach with breakpoints at 768px and 480px
2. **No Scrolling Goal**: Content fits on one viewport when possible (on desktop and tablets)
3. **QR-Code Friendly**: Designed to be accessed via QR codes - quick to load, easy to scan on mobile
4. **Finnish Language**: All content is in Finnish
5. **Professional Aesthetic**: Blue-purple gradient theme with clean typography

## Content Structure

The page follows this layout:
- **Header**: Name, title, graduation date, contact links (LinkedIn, GitHub, phone, email)
- **Intro**: Short bio (2-3 sentences about Andreas's background)
- **Main Grid** (2 columns on desktop, 1 on mobile):
  - Education (Metropolia, thesis info)
  - Work Experience (5 positions, most recent first)
  - Skills (3 categories: Testaus, Ohjelmointi, Muut)
  - Special Skills (differentiators: user understanding, teamwork, maturity)
- **Footer**: CTA and contact links

## Styling Details

- **Color Palette**:
  - Primary gradient: `#667eea` to `#764ba2` (blue-purple)
  - Header: `#2d3748` to `#4a5568` (dark gray gradient)
  - Accent: `#667eea` (blue)
  - Hover: `#90cdf4` (light blue)
- **Grid Layout**: CSS Grid with 2 columns on desktop (`grid-template-columns: 1fr 1fr`)
- **Responsive**: Uses `@media` queries for tablets (768px) and phones (480px)
- **Hover Effects**: Links and skill tags have subtle transform/color transitions

## Making Changes

When updating this CV:

1. **Personal Info**: Update header (`<header>`) and footer contact links
2. **Content Sections**: Each section is a `.section` div with Font Awesome icon in `<h2>`
3. **Skills**: Modify `.skill-tag` spans within `.skills-category` divs
4. **Responsive Testing**: Test at 1200px+ (desktop), 768px (tablet), 480px (mobile)
5. **Colors**: Search for hex codes to maintain consistent theming

## Testing

Open `index.html` directly in a browser (double-click or `file://` protocol). Test responsiveness by:
- Resizing browser window
- Using browser DevTools device emulation
- Actual mobile device testing

No local server required.
