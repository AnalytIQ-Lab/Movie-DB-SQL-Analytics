# Movie Analytics Project: From Relational Data to Business Insights

## Project Overview

This project demonstrates an end-to-end data analytics workflow using a relational movie database. It transforms raw relational data into structured analytical data marts, performs data quality checks and exploratory data analysis, applies advanced SQL techniques, and translates analytical results into business insights and recommendations.

The project emphasizes analytical accuracy, data integrity, appropriate table grain, and reproducible analysis.

## Business Objectives

The project aims to:

- Assess the quality, completeness, and consistency of the source data.
- Explore relationships across movies, artists, genres, languages, keywords, and production entities.
- Build analytical data marts that simplify downstream analysis.
- Evaluate movie financial performance using budget, revenue, profit, and return on investment (ROI), where valid.
- Investigate movie popularity, genre distribution, release trends, and artist participation.
- Translate analytical findings into actionable recommendations.
- Produce executive-ready KPIs, a business insight register, and an executive summary.

## Technology Stack

| Technology | Application |
|---|---|
| Python | Data manipulation, validation, and analysis |
| Pandas | Data cleaning, transformation, aggregation, and EDA |
| SQL | Relational queries, joins, CTEs, and advanced analysis |
| SQLAlchemy | Database connectivity |
| Jupyter Notebook | Interactive, reproducible analysis |
| VS Code | Development environment |
| Matplotlib / Seaborn | Visual exploration, where used |
| Git and GitHub | Version control and project documentation |

*The final list of dependencies should reflect the libraries actually used in the notebooks.*

## Project Workflow

The project is organized into seven analytical notebooks.

| Notebook | Focus | Key Activities |
|---|---|---|
| `03_Data_Quality.ipynb` | Data quality | Validate uniqueness, missing values, mappings, numerical validity, dates, and relationships |
| `04_SQL_Joins.ipynb` | Relational analysis | Explore joins, table relationships, and multi-table queries |
| `05_Analytics_Marts.ipynb` | Data modeling | Build analytical data marts from relational source tables |
| `06_Artist_Diary_EDA.ipynb` | Artist analysis | Explore artist participation, character roles, and associated movie attributes |
| `07_Movie_Master_EDA.ipynb` | Movie analysis | Examine movie attributes, financial metrics, release patterns, and distributions |
| `08_Advanced_SQL.ipynb` | Advanced querying | Apply advanced SQL techniques to analytical questions |
| `09_Business_Insights.ipynb` | Business intelligence | Validate KPIs, interpret findings, prioritize recommendations, and export reports |

> **Note:** Notebook numbering begins at `03` because this README documents the current analytical sequence. Add earlier notebooks if they form part of the published repository.

## Analytical Data Marts

### 1. Artist Diary

The Artist Diary mart combines artist and character participation with associated movie attributes.

Previously recorded structure: **106,257 rows and 12 columns**.

Fields include:

- Artist ID and artist name
- Gender
- Character name
- Movie title
- Popularity
- Budget and revenue
- Languages
- Production companies
- Production countries
- Release status

**Analytical grain:** one row per artist–movie–character combination.

This grain is important because a movie can have multiple artists and characters. Movie-level financial metrics must therefore be deduplicated or calculated at the movie grain before aggregation.

### 2. Movie Master

The Movie Master is intended to provide a movie-level analytical dataset, with one record per unique movie.

It supports analysis of:

- Movie portfolio composition
- Financial performance
- Release patterns
- Popularity
- Genre associations, where available

The actual schema and uniqueness constraints should be validated against the final implementation.

## Data Quality and Analytical Controls

The project incorporates checks designed to improve the reliability of analytical outputs.

Examples include:

- Duplicate primary-key checks
- Missing-value and empty-string checks
- Orphaned mapping records
- Numerical validity checks
- Date validation
- Many-to-many relationship validation
- Categorical consistency
- Financial metric validation
- Duplicate movie detection before movie-level aggregation

These checks help distinguish genuine business patterns from data quality issues.

## Business Analysis

The final business insights notebook investigates supported questions across several analytical areas.

### Movie Portfolio

- How many unique movies are represented?
- How is the catalogue distributed across release years?
- Which release periods contribute the most records?

### Financial Performance

- How are budget, revenue, and profit distributed?
- How many movies are profitable among records with valid financial data?
- Which movies have the highest recorded revenue?
- Which movies have the highest ROI among eligible records?

### Popularity and Revenue

- Is movie popularity associated with recorded revenue?
- How strong is the observed relationship?
- What limitations affect interpretation?

### Genre Analysis

- Which genres appear most frequently?
- How does recorded financial performance vary across genres?
- How can overlapping genre assignments affect aggregate totals?

### Artist Participation

- Which artists have the highest movie participation?
- How is participation distributed across artists?
- What limitations affect artist-level comparisons?

The analyses and final conclusions should reflect the available source fields and validated results. The questions above describe the analytical scope, not guaranteed findings.

## Key Metrics

The project evaluates metrics such as:

| Metric | Definition |
|---|---|
| Distinct Movies | Count of unique movie identifiers |
| Profit | Revenue minus budget, when both values are valid |
| ROI | Profit divided by budget, where budget is greater than zero |
| Profitability | Recorded revenue exceeds recorded budget for valid financial records |
| Artist Participation | Number of distinct movies associated with an artist |
| Revenue Concentration | Share of recorded revenue attributable to a defined group of movies |

Metric definitions, denominators, exclusions, and aggregation grain should be documented alongside the final results.

## Deliverables

The final project includes the following intended outputs:

- **`executive_summary.md`** — concise summary of validated findings and recommendations.
- **`verified_insight_register.csv`** — structured findings with evidence, business implications, confidence, and priorities.
- **`executive_kpis.csv`** — key performance indicators and their interpretations.
- **`analysis_validation_report.csv`** — validation checks and their results.
- **Jupyter notebooks** — documented analytical workflow and reproducible code.

Only include files in this list that are present in the final repository and have been validated.

## Repository Structure

A suggested structure is:

```text
movie-analytics-project/
│
├── notebooks/
│   ├── 03_Data_Quality.ipynb
│   ├── 04_SQL_Joins.ipynb
│   ├── 05_Analytics_Marts.ipynb
│   ├── 06_Artist_Diary_EDA.ipynb
│   ├── 07_Movie_Master_EDA.ipynb
│   ├── 08_Advanced_SQL.ipynb
│   └── 09_Business_Insights.ipynb
│
├── data/
│   ├── raw/
│   └── processed/
│
├── outputs/
│   ├── executive_summary.md
│   ├── verified_insight_register.csv
│   ├── executive_kpis.csv
│   └── analysis_validation_report.csv
│
├── requirements.txt
├── .gitignore
└── README.md
```

Adapt this structure to your actual repository. Avoid publishing private, licensed, or sensitive source data, database credentials, or unnecessary large generated files.

## Getting Started

### Prerequisites

- Python installed
- Visual Studio Code
- Jupyter extension for VS Code
- Access to the source database or a supported local database copy

### Installation

Clone the repository:

```bash
git clone <your-github-repository-url>
cd movie-analytics-project
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Configure the database connection using your project's documented configuration method. Keep credentials in environment variables or an untracked local configuration file.

Open the repository in VS Code and execute the notebooks in their intended order, ensuring that the required database and source tables are available.

## Important Analytical Considerations

- **Grain:** Artist-level and movie-level tables answer different questions.
- **Double-counting:** Many-to-many relationships can inflate movie counts and financial totals.
- **Missing data:** Missing revenue is not necessarily zero revenue.
- **ROI:** ROI should not be calculated for zero or invalid budgets.
- **Correlation:** Association between popularity and revenue does not establish causation.
- **Evidence:** Business recommendations should be traceable to actual calculations and documented limitations.
- **Reproducibility:** Notebook outputs should be regenerated from the documented workflow rather than depending on manually created variables.

## Skills Demonstrated

- SQL querying and relational data analysis
- Data quality assessment
- Data modeling and analytical mart development
- Python and Pandas
- Exploratory data analysis
- Financial KPI calculations
- Analytical validation and documentation
- Business insight development
- Executive reporting
- Git and GitHub workflow

## Conclusion

This project demonstrates a structured approach to transforming relational data into reliable analytical datasets and business-facing outputs. It brings together data validation, SQL, Python, analytical modeling, exploratory analysis, and evidence-based reporting within a reproducible workflow.

The ultimate objective is not simply to produce charts or metrics, but to establish a clear connection between data quality, analytical reasoning, and defensible business recommendations.
