# BBL Buildings Data Catalog

**Status:** Prototype / Concept

This is a prototype **Data Catalog** for the Federal Office for Buildings and Logistics (BBL), Buildings Division. The goal is to provide transparent documentation and linking of business objects, metadata, and attributes according to the DCAT-AP CH standard.

## Live Demo

- Deployed: https://davras5.github.io/meta-bv/

![Preview](images/readme/Preview.JPG)

## Project Structure

```
meta-bv/
├── index.html              # Main single-file web application
├── content/
│   ├── about.html          # About page content
│   └── handbuch.html       # User manual/handbook
├── data/
│   ├── datasets.json       # Dataset definitions (buildings, contracts, etc.)
│   └── concepts.json       # Concept definitions (technical objects, spatial structures)
└── images/
    ├── BBL DCAT-AP CH.avif # DCAT-AP CH diagram
    ├── ch.png              # Swiss coat of arms
    └── readme/
        └── Preview.JPG     # Application preview screenshot
```

## Technology

This project is designed as a minimalist **single-file web prototype** to ensure maximum simplicity and rapid deployment.

- **HTML5:** Structure and layout
- **CSS3:** Styling with CSS variables and responsive design
- **JavaScript (Vanilla JS):** Dynamic data loading, hash-based routing, filtering, view switching (Grid/List), and detail view rendering
- **Data Source:** The catalog is populated via external JSON files (`datasets.json` and `concepts.json`)

## Features

- **Navigation:** Hash-based navigation between main views (Data Model, About, Manual)
- **Data Display:** Toggle between grid card view and detailed list view
- **Search/Filter:** Dynamic search across titles, descriptions, and tags
- **Detail View:** Detailed view of business objects including metadata and attribute tables (PK/FK/Format badges)
- **Corporate Design:** Uses the official Swiss coat of arms and the "Frutiger" font family (via fallback stack) for an authentic Swiss Federal Administration appearance
- **Documentation:** Integrated "About" and "Manual" sections for static concept documentation

## License
Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

*This is an unofficial mockup for demonstration purposes.*
