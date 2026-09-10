# ClassGraph

ClassGraph is a full-stack course-planning tool that helps UCSD students understand complicated prerequisite structures through interactive graphs built from live course data.

**Live demo:** https://classgraph-black.vercel.app/

## Impact
- Modeled **1,000+ UCSD courses** and **100+ prerequisite chains** as directed graphs.
- Built logic for recursive prerequisite traversal and validation, including alternative `OR` requirements and duplicate-node handling.
- Supports academic-history PDF uploads so students can compare completed coursework against prerequisite paths.
- **1st Place** project.

## My Contribution
This was a team project. I worked on the graph and product logic, including recursive prerequisite validation, course search, academic-history PDF uploads, `OR` grouping for alternative prerequisites, and duplicate-node handling.

## Key Features
- **Class Search:** Search courses by code with support for multiple input formats.
- **Requirement Details:** Highlight nodes with the `(!)` icon to view additional requirements that may need to be fulfilled.
- **Prerequisite Visualization:** Explore prerequisite trees grouped by logical relationships and expand through complete prerequisite chains.
- **Academic History Uploads:** Upload an academic-history PDF to help visualize completed and remaining coursework.

## Architecture
```text
UCSD Course Catalog + Schedule of Classes Scraper
    |
Course Tooling (merge datasets and verify prerequisites)
    |
Tree Generation (generate complete trees for each class)
    |
Frontend UI (select class / upload PDF / visualize course flow)
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

## Run Locally

### Prerequisites
- Python 3.12+
- Go 1.23+
- npm

```bash
git clone https://github.com/ncdev06/classgraph.git
cd classgraph
pip install -r requirements.txt
python catalog_scraper/main.py

cd soc_scraper
go build
./soc_scraper
cd ..

python data/helpers/cross_check.py
python data/helpers/ast.py

npm install
npm run build
```

## Testing
```bash
cd soc_scraper
go test ./... -v
```
