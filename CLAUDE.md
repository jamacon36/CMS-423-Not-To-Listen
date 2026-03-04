# CLAUDE.md

## Project Overview

**Honeycomb Framework Diagram** — a single-file interactive HTML tool for visualizing regulatory or analytical frameworks using a hexagon/honeycomb layout with editable content panels.

Course: CMS-423

## Stack

- **Pure HTML/CSS/JS** — no build tools, no package manager, no dependencies to install
- **Google Fonts**: Playfair Display, Source Serif 4 (loaded via CDN)
- **Inline SVG** for the central hexagon diagram
- Single file: `index.html`

## Architecture

Everything lives in `index.html`:
- CSS in `<style>` block (lines 8–222)
- SVG diagram with `<foreignObject>` for the editable center label (lines 274–357)
- Editable panels (Sections A–D) surrounding the SVG using CSS Grid
- Minimal JS (lines 388–395) — only prevents Enter key from inserting `<div>` in panel titles

## Design Tokens (CSS variables)

```css
--navy: #1a2744
--gold: #b8975a
--gold-light: #d4b47a
--gold-pale: #f5edd8
--cream: #f8f4ee
```

## Layout Structure

The main grid (`diagram-layout`) uses 3 columns × 3 rows:
- **Top center**: Section A panel
- **Left**: Section B panel
- **Center**: SVG hexagon diagram
- **Right**: Section C panel
- **Bottom center**: Section D panel

The hexagon is divided into 4 segments (A, B, C, D) with dashed connector lines leading to the surrounding panels.

## Editing Notes

- All user-facing text uses `contenteditable="true"` — the diagram is designed to be filled in directly in the browser
- The `data-placeholder` attribute sets placeholder text for empty contenteditable fields
- The center circle label ("Regulatory Nexus") is inside a `<foreignObject>` in the SVG
- To add new sections or change the diagram geometry, edit the SVG `<polygon>` coordinates in the `svg-area` div

## Workflow

No build step required. Open `index.html` directly in a browser to view and edit.
