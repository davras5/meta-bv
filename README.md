# BBL Buildings Data Catalog (meta-bv)

**Status:** Prototype / Concept
**Version:** 1.0.0

A data catalog for the Federal Office for Buildings and Logistics (Bundesamt für Bauten und Logistik - BBL), Buildings Division. This prototype provides transparent documentation and linking of business objects, metadata, and attributes according to the **DCAT-AP CH v3.0** standard.

## Live Demo

**Deployed:** https://davras5.github.io/meta-bv/

![Preview](images/readme/Preview.JPG)

## Features

### Core Functionality
- **Data Catalog:** Browse 8 business object concepts and 11 datasets with comprehensive metadata
- **Full-Text Search:** Search across titles, descriptions, and tags
- **Advanced Filtering:** Filter by tags, system, data classification, and personal data status
- **Dual View Modes:** Switch between grid view (cards) and list view (table)

### Detail Pages
- Complete metadata display for each catalog item
- Standards conformance information (ISO, eBKP-H, DIN 276)
- Attributes table with format, key type (PK/FK), and value list references
- Responsible persons with Swiss Admin Directory integration
- Distribution formats (CSV, Excel, REST API, JSON)
- Publication references to external catalogs

### User Experience
- Hash-based navigation (no server-side routing required)
- Print functionality for catalog entries
- Share modal with social media integration
- Mobile-responsive design
- Official Swiss Federal Administration styling

## Project Structure

```
meta-bv/
├── index.html                    # Main single-file web application (~2,180 lines)
├── README.md                     # Project documentation
├── CLAUDE.md                     # Development guidelines for Claude Code
│
├── content/                      # Static content pages
│   ├── about.html                # About the data catalog
│   └── handbuch.html             # User manual/handbook
│
├── data/                         # JSON data files
│   ├── concepts.json             # 8 business object definitions
│   └── datasets.json             # 11 dataset definitions
│
└── images/
    ├── ch.png                    # Swiss coat of arms logo
    ├── BBL DCAT-AP CH.avif       # DCAT-AP CH architecture diagram
    ├── concepts/                 # Images for business concepts
    ├── datasets/                 # Images for datasets
    └── readme/
        └── Preview.JPG           # Application screenshot
```

## Technology Stack

This project is designed as a **minimalist single-file web application** with zero external dependencies.

| Technology | Purpose |
|------------|---------|
| HTML5 | Structure and semantic markup |
| CSS3 | Styling with CSS variables, responsive design |
| Vanilla JavaScript | Dynamic functionality, hash-based routing |
| Material Design Icons | Google Material Symbols (via CDN) |
| JSON | Data storage for concepts and datasets |

### No Build Required
- No npm/yarn dependencies
- No build step or compilation
- Runs directly in any modern browser

## Standards Compliance

| Standard | Description |
|----------|-------------|
| **DCAT-AP CH v3.0** | Swiss Data Catalog Application Profile |
| **TOGAF** | 3-tier metadata model (Business, Logical, Technical) |
| **DCAT v3** | W3C standard for data catalogs |
| **Dublin Core** | Metadata properties (dct:Standard, dct:conformsTo) |
| **SKOS** | Simple Knowledge Organization System |
| **IFC/ISO 16739** | Building Information Model standard |
| **eBKP-H 2020** | Swiss building classification |
| **DIN 276** | German building cost classification |

## Getting Started

### Quick Start

1. **Clone the repository:**
   ```bash
   git clone https://github.com/davras5/meta-bv.git
   cd meta-bv
   ```

2. **Start a local server:**
   ```bash
   # Python 3
   python3 -m http.server 8000

   # Or Node.js
   npx http-server
   ```

3. **Open in browser:**
   ```
   http://localhost:8000
   ```

### Development

Edit the following files to customize the catalog:

- `index.html` - Main application logic and styling
- `data/concepts.json` - Business object definitions
- `data/datasets.json` - Dataset definitions
- `content/about.html` - About page content
- `content/handbuch.html` - User manual content

## Data Structure

### Concepts (Business Objects)

Each concept in `concepts.json` contains:

```json
{
  "id": "unique-id",
  "title": "Display Title",
  "description": "Short description",
  "fullDescription": "Detailed description",
  "image": "images/concepts/image.jpg",
  "tags": ["tag1", "tag2"],
  "meta": {
    "fachliche_id": "Business ID",
    "system": "Source system",
    "klassifizierung": "Public|Internal|Confidential|Secret",
    "personenbezogen": "Keine|Personenbezogen|Besonders schützenswert"
  },
  "standards": [
    { "name": "Standard Name", "value": "Mapping value" }
  ],
  "attributes": [
    { "name": "Field", "format": "Type", "key": "PK|FK|-", "list": "Value list", "desc": "Description" }
  ],
  "responsiblePersons": [
    { "admindirId": "ID", "name": "Name", "rolle": "Role" }
  ]
}
```

### Datasets

Each dataset in `datasets.json` contains similar structure plus:

```json
{
  "distributions": [
    { "name": "Export Name", "format": "Excel|CSV|API", "zugriffsUrl": "URL" }
  ],
  "publications": [
    { "katalog": "Catalog Name", "url": "URL" }
  ]
}
```

## URL Structure

The application uses hash-based routing:

| Route | Description |
|-------|-------------|
| `#/` or `#/concept` | Concepts overview |
| `#/dataset` | Datasets overview |
| `#/concept/{id}` | Concept detail page |
| `#/dataset/{id}` | Dataset detail page |
| `#/about` | About page |
| `#/handbuch` | User manual |

### Query Parameters

- `?tags=tag1,tag2` - Filter by tags
- `?view=grid|list` - Set view mode
- `?system=value` - Filter by source system
- `?klassifizierung=value` - Filter by classification
- `?personenbezogen=value` - Filter by personal data status

## Configuration

### CSS Variables

Key styling variables defined in `index.html`:

```css
--primary-color: #DC0018;    /* Swiss Red */
--text-dark: #2F4356;
--bg-light: #F5F5F5;
--footer-bg: #263645;
--spacing-xs: 8px;
--spacing-sm: 15px;
--spacing-md: 20px;
--spacing-lg: 30px;
--spacing-xl: 50px;
```

### Layout

- Max content width: 1200px
- Filter panel width: 280px
- Responsive grid: auto-fill minmax(300px, 1fr)

## Deployment

### GitHub Pages

The project is configured for GitHub Pages deployment. Push to the `main` branch to auto-deploy.

### Custom Server

Simply serve the files from any static web server. No special configuration required.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Make your changes
4. Commit (`git commit -m 'Add my feature'`)
5. Push to the branch (`git push origin feature/my-feature`)
6. Open a Pull Request

## License

Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## Contact

- **Email:** dares@bbl.admin.ch
- **Repository:** https://github.com/davras5/meta-bv

---

*This is an unofficial mockup for demonstration purposes.*
