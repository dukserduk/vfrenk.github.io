# GitHub Copilot Instructions for this Repo

## Overview
- This repo is a single-page resume site built as static HTML + CSS.
- The main entry point and only rendered page is [index.html](index.html).
- [README.md](README.md) currently mirrors the HTML structure of the page rather than traditional Markdown docs.

## Tech Stack & Layout
- No build tooling, bundlers, or frameworks; everything is plain HTML with inline `<style>` in the `<head>` of [index.html](index.html).
- Layout is driven by:
  - `.container` as the centered card.
  - `.header` (name, title, contact) with flexbox.
  - `.content` grid with two columns: left main content, right `<aside>` sidebar.
- Visual sections use the shared `.section` + `.section-title` pattern.
- Experience, Education, Projects share the `.item`, `.item-header`, `.item-subtitle`, `.item-date` structure.

## Editing & Extension Patterns
- When updating the user’s information (name, contact, summary, experience, education, skills, etc.), edit the existing placeholders in [index.html](index.html) rather than adding new styling by default.
- To add a new section (e.g., "Publications" or "Volunteer Work"):
  - Follow the existing markup pattern:
    - Wrap it in `<section class="section">`.
    - Use `<div class="section-title">Section Name</div>`.
    - Use `.item` blocks if you need repeated entries.
- To add new skills or tags in the sidebar, append `<li>` items inside the relevant `.skills-list` `<ul>`.
- Keep CSS changes inside the existing `<style>` block to preserve the single-file design unless the user explicitly requests external stylesheets.
- Reuse existing utility classes (`.small`, `.skills-list`, `.item-*`) instead of creating near-duplicates.

## Responsive Behavior
- The layout becomes single-column on small screens via the `@media (max-width: 768px)` rule:
  - `.content` switches from a 2-column grid to 1 column.
  - `.header-contact` text alignment changes.
- When changing structure or adding columns, preserve this breakpoint and ensure new blocks degrade gracefully on narrow viewports.

## Workflows & Preview
- There is no build or test step; changes should be immediately visible.
- For local preview, either:
  - Open [index.html](index.html) directly in a browser, or
  - Serve the repo as a static site (e.g., `python -m http.server`) from the project root.
- The repo name (`resume.github.io`) suggests GitHub Pages hosting from the `main` branch; assume that `index.html` at the repo root is what is deployed.

## Conventions & Constraints
- Prefer minimal, semantic HTML (e.g., `<header>`, `<section>`, `<aside>`, `<ul>/<li>`), consistent with the current structure.
- Do not introduce JavaScript, libraries, or build tools unless explicitly asked.
- Keep typography and spacing consistent with existing CSS (system UI font stack, subtle box-shadows, rounded container).
- When making significant layout or structural changes, mirror them in [README.md](README.md) only if the user requests README to remain an HTML preview; otherwise, prioritize [index.html](index.html) as the source of truth.
- Preserve accessibility basics: readable contrast, logical heading order, and meaningful link text when modifying content.
