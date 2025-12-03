# CLAUDE.md

This document provides development guidelines for Claude Code when working on the BBL Buildings Data Catalog (meta-bv) project.

## Project Overview

This is a **minimalist single-file web application** for cataloging business objects and datasets for the Swiss Federal Office for Buildings and Logistics. The entire application runs from `index.html` with zero external JavaScript dependencies.

## Architecture

### Single-File Design
- All HTML, CSS, and JavaScript are contained in `index.html` (~2,180 lines)
- No build system, bundlers, or transpilers
- Data loaded from JSON files at runtime
- Hash-based client-side routing

### Code Organization in index.html

```
index.html
├── <head>
│   └── CSS styles (~900 lines)
├── <body>
│   └── HTML structure
└── <script>
    └── JavaScript application (~800 lines)
        ├── State management
        ├── Data loading
        ├── Routing
        ├── Rendering functions
        └── Event handlers
```

### Key Patterns
- **IIFE Pattern:** JavaScript wrapped to avoid global scope pollution
- **Hash Routing:** `window.location.hash` for navigation
- **URL as State:** Filter states stored in URL query parameters
- **Event Delegation:** Single listeners on container elements
- **Async Data Loading:** JSON files loaded via fetch()

## File Locations

| Purpose | Location |
|---------|----------|
| Main application | `index.html` |
| Business objects | `data/concepts.json` |
| Dataset definitions | `data/datasets.json` |
| About page content | `content/about.html` |
| User manual | `content/handbuch.html` |
| Concept images | `images/concepts/` |
| Dataset images | `images/datasets/` |

## Development Commands

```bash
# Start local development server
python3 -m http.server 8000
# or
npx http-server

# Open in browser
open http://localhost:8000
```

## Making Changes

### Adding a New Concept

1. Edit `data/concepts.json`
2. Add a new object with required fields:
   - `id`, `title`, `description`, `fullDescription`
   - `image`, `tags`, `meta`, `standards`, `attributes`
   - Optional: `responsiblePersons`
3. Add corresponding image to `images/concepts/`

### Adding a New Dataset

1. Edit `data/datasets.json`
2. Add a new object with required fields:
   - Same as concepts plus `distributions` and `publications`
3. Add corresponding image to `images/datasets/`

### Modifying Styles

All CSS is in the `<style>` section of `index.html`. Key CSS variables:

```css
--primary-color: #DC0018;    /* Swiss Red - use for accents */
--text-dark: #2F4356;        /* Main text color */
--bg-light: #F5F5F5;         /* Light backgrounds */
--border-color: #e5e5e5;     /* Borders and dividers */
```

### Adding New Features

When adding JavaScript functionality:
1. Locate the relevant section in the `<script>` block
2. Follow existing patterns for consistency
3. Use the existing state management approach
4. Update URL parameters if adding new filters

## Code Style Guidelines

### JavaScript
- Use vanilla JavaScript (no frameworks)
- Prefer `const` and `let` over `var`
- Use template literals for HTML generation
- Use async/await for data fetching
- Keep functions focused and small

### CSS
- Use CSS variables for colors and spacing
- Follow BEM-like naming (`.card-title`, `.filter-panel`)
- Mobile-first responsive design
- Use flexbox/grid for layouts

### HTML
- Use semantic elements (`<nav>`, `<main>`, `<article>`)
- Include proper accessibility attributes
- Keep structure minimal and clean

## Data Schema Reference

### Concept Object
```json
{
  "id": "string (unique identifier)",
  "title": "string (display name)",
  "description": "string (short summary)",
  "fullDescription": "string (detailed description)",
  "image": "string (path to image)",
  "tags": ["array", "of", "strings"],
  "meta": {
    "fachliche_id": "string",
    "termdat": "string (TERMDAT reference)",
    "fachbereich": "string",
    "system": "string (source system)",
    "klassifizierung": "Public|Intern|Vertraulich|Geheim",
    "personenbezogen": "Keine|Personenbezogen|Besonders schützenswert",
    "kommentar": "string",
    "version": "string (semver)"
  },
  "standards": [
    { "name": "string", "value": "string|array" }
  ],
  "attributes": [
    { "name": "string", "format": "string", "key": "PK|FK|-", "list": "string", "desc": "string" }
  ],
  "responsiblePersons": [
    { "admindirId": "string", "name": "string", "rolle": "string" }
  ]
}
```

### Dataset Object
```json
{
  // Same fields as concept, plus:
  "distributions": [
    {
      "name": "string",
      "format": "string",
      "identifikator": "string",
      "titel": "string",
      "zugriffsUrl": "string (URL)",
      "downloadUrl": "string (URL)",
      "status": "string",
      "dateiformat": "string",
      "lizenz": "string",
      "bemerkungen": "string"
    }
  ],
  "publications": [
    { "katalog": "string", "url": "string" }
  ]
}
```

## Testing

No automated tests exist. Manual testing:

1. Check all navigation routes work
2. Verify search and filter functionality
3. Test grid/list view toggle
4. Verify detail pages render correctly
5. Check responsive behavior on mobile
6. Test print functionality
7. Test share functionality

## Common Tasks

### Fix styling issues
- Check `<style>` section in `index.html`
- Use browser dev tools to identify CSS conflicts
- Maintain Swiss Federal Administration design guidelines

### Add new filter option
1. Add filter UI in the filter panel HTML
2. Add state variable for the filter
3. Update `applyFilters()` function
4. Update URL parameter handling

### Debug data loading
- Check browser console for fetch errors
- Verify JSON file syntax is valid
- Check file paths are correct

## Important Notes

- **No build step required** - changes are immediately visible on refresh
- **Keep dependencies at zero** - this is intentional for simplicity
- **Preserve Swiss Federal styling** - use official colors and fonts
- **Follow DCAT-AP CH standard** - metadata structure must comply
- **German is primary language** - all content in German, UI labels in German
