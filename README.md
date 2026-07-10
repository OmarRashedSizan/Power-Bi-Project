# 🩺 Medical Domain Analytics — Power BI

A Power BI dashboard built on a multi-table healthcare dataset, modeling patients, providers, visits, diagnoses, procedures, insurance, departments, and cities into a single connected data model with full time-intelligence support.

**Tech stack:** Power BI · Power Query (M) · DAX

---

## 📌 Project Overview

Healthcare data is naturally relational — a single patient visit touches a provider, a department, one or more diagnoses and procedures, an insurance record, and a location. This project takes that raw, multi-table structure and turns it into a connected Power BI data model with a dynamic date dimension, enabling time-based analysis (by year, quarter, month, and week) across the entire healthcare dataset from one dashboard.

## ❓ Problem Statement

With patient, provider, and visit data spread across separate files, there was no single view to answer questions like:

- How many patient visits are occurring, and how does that trend over time (year, quarter, month, week)?
- Which providers and departments handle the highest visit volume?
- What are the most common diagnoses and procedures?
- How is patient activity distributed across cities?
- How does insurance coverage relate to visits and procedures?

This project builds the data model and dashboard needed to answer those questions from one place instead of cross-referencing raw tables manually.

## 🗂️ Dataset

A relational healthcare dataset spread across multiple CSV files, each representing a core entity:

- `patients.csv` — patient records
- `providers.csv` — healthcare provider records
- `visits.csv` — patient visit (fact) records
- `diagnose.csv` — diagnosis records
- `procedures.csv` — procedure records
- `insurance.csv` — insurance records
- `department.csv` — hospital department reference data
- `cities.csv` — city/location reference data

## 🔧 Data Modeling

- Loaded all eight source tables into Power BI and built the relationships between patients, providers, visits, diagnoses, procedures, insurance, departments, and cities to support cross-filtering across the whole dashboard.
- Built a fully **dynamic date table** in Power Query (M), generated directly from the range of visit dates in the dataset rather than a hardcoded calendar. The date table includes Year, Quarter (with a "Year-Quarter" label), Month, short Month Name, Week of Year, Week of Month, Day Name, a Weekday/Weekend flag, and a combined "Mon-Year" label — giving the report full flexibility for time-based slicing and trend analysis.

## 🧠 Challenges & How They Were Solved

- **Connecting eight separate tables into one coherent model:** rather than analyzing each CSV in isolation, relationships were built around `visits.csv` as the central fact table, linking out to patients, providers, departments, diagnoses, procedures, insurance, and cities — enabling any visual to slice by any dimension.
- **No built-in time intelligence in the raw data:** the source data only had raw visit dates, with no year/quarter/week breakdown. This was solved by building a dynamic date table in Power Query that automatically spans the full date range of the dataset and derives every time attribute needed (year, quarter, month, week, weekday/weekend) instead of hardcoding a fixed calendar range.
- **Keeping the date table reusable:** the M script was written so the date range regenerates automatically from the underlying visit data, meaning the date table doesn't need to be manually updated if the dataset grows.

## ⚙️ How to Use

1. Clone this repository
2. Open `Medical_domain_project.pbix` in Power BI Desktop
3. Refresh the data source to load `patients.csv`, `providers.csv`, `visits.csv`, `diagnose.csv`, `procedures.csv`, `insurance.csv`, `department.csv`, and `cities.csv`
4. Explore the report pages to analyze visits, providers, departments, diagnoses, and procedures across time and location

## 🗃️ Repository Structure

```
├── patients.csv                     # Patient dimension
├── providers.csv                    # Provider dimension
├── visits.csv                       # Visit fact table
├── diagnose.csv                     # Diagnosis dimension
├── procedures.csv                   # Procedure dimension
├── insurance.csv                    # Insurance dimension
├── department.csv                   # Department dimension
├── cities.csv                       # City/location dimension
├── Dynamic_Date_Table_M_Code.txt      # Power Query M script for the dynamic date table
├── Medical_domain_project.pbix      # Power BI dashboard
└── README.md
```

## 👤 Author

**Omar Rashed**
[LinkedIn](https://linkedin.com/in/omar-rashed-sizan-4a497628a) · [GitHub](https://github.com/OmarRashedSizan)
