# ClassGraph

ClassGraph helps UCSD students explore course prerequisites through interactive graphs built from up-to-date course data. The project combines automated scraping, prerequisite parsing, and visualization so complex course requirements are easier to understand.

**Live demo:** https://classgraph-black.vercel.app/

## Key Features
- **Class Search:** Search courses by code with support for multiple input formats.
- **Requirement Details:** Highlight nodes with the `(!)` icon to view additional requirements that may need to be fulfilled.
- **Prerequisite Visualization:** Explore prerequisite trees grouped by logical relationships and expand through complete prerequisite chains.
- **Academic History Uploads:** Upload an academic-history PDF to help visualize completed and remaining coursework.

## Architecture
```text
UCSD Course Catalog + Schedule of Classes Scraper (Automated)
    |
Course Tooling (merge datasets and verify prerequisites)
    |
Tree Generation (generate complete trees for each class)
    |
Frontend UI (select class / upload PDF / visualize course flow)
```

## Preparation and Deployment

### Prerequisites
- Python 3.12+
- Go 1.23+
- npm

### Deployment
```bash
# clone repository
git clone https://github.com/ncdev06/classgraph.git
cd classgraph

# install Python requirements
pip install -r requirements.txt

# scrape course catalog
python catalog_scraper/main.py

# scrape Schedule of Classes
cd soc_scraper
go build
./soc_scraper
cd ..

# cross-verify classes and build trees
python data/helpers/cross_check.py
python data/helpers/ast.py

# install frontend dependencies
npm install
npm run build
```

## Project Structure
```text
classgraph/
├── .github/
│   └── workflows/          # GitHub Actions CI/CD workflows
├── catalog_scraper/        # Course catalog scraper
├── data/                   # Scraped and processed course data
├── major_scraper/          # Major-specific data scraper
├── soc_scraper/            # Schedule of Classes scraper
├── src/                    # Frontend source code
├── .gitignore
├── README.md
├── index.html
├── package-lock.json
├── package.json
├── requirements.txt
├── tailwind.config.js
├── tailwind.css
└── vite.config.js
```

## Tech Stack
| Category | Technology | Purpose |
| :--- | :--- | :--- |
| Frontend | JavaScript, HTML | Application logic and interface |
| Styling | Tailwind CSS | UI styling |
| Build Tool | Vite | Frontend development and builds |
| Schedule Scraping | Go | Concurrent scraping from UCSD course data |
| Catalog Scraping | Python | Course catalog extraction |
| Data Processing | Python | Prerequisite parsing and dataset processing |
| Data Storage | JSON | Structured course and prerequisite data |
| CI/CD | GitHub Actions | Automated workflows and course-data updates |
| Deployment | Vercel | Live web application hosting |

## Testing
```bash
cd soc_scraper
go test ./... -v
```
