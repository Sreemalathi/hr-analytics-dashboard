# HR Analytics Dashboard

A Tableau dashboard analyzing an 8,950-record employee dataset covering headcount, attrition, demographics, compensation, and performance across a 7-department, 8-state workforce (2015–2024).

![HR Summary Dashboard](images/hr-summary-dashboard.png)

## Overview

| Metric | Value |
|---|---|
| Total employee records | 8,950 |
| Active employees | 7,984 |
| Terminated employees | 966 |
| **Overall attrition rate** | **10.79%** |
| Departments | 7 |
| States / Cities represented | 8 / 20+ |
| Data window | Jan 2015 – Dec 2024 |
| Avg. tenure (active employees) | 6.5 years |
| Avg. tenure at exit (terminated) | 1.9 years |

## Dataset

- **File:** [`data/dataset.csv`](data/dataset.csv) — 8,950 rows, semicolon-delimited
- **Fields:** Employee ID, First/Last Name, Gender, State, City, Education Level, Birthdate, Hire Date, Termination Date, Department, Job Title, Salary, Performance Rating
- **Note:** Names in this file are synthetic/sample data generated for portfolio and learning purposes — not real employee records.

## Key Metrics

### Headcount & attrition by department

| Department | Active | Terminated | Total | Attrition Rate |
|---|---:|---:|---:|---:|
| Operations | 2,429 | 289 | 2,718 | 10.6% |
| Sales | 1,634 | 201 | 1,835 | 11.0% |
| Customer Service | 1,489 | 184 | 1,673 | 11.0% |
| IT | 1,243 | 139 | 1,382 | 10.1% |
| Marketing | 648 | 70 | 718 | 9.7% |
| Finance | 389 | 63 | 452 | **13.9%** (highest) |
| HR | 152 | 20 | 172 | 11.6% |

### Gender demographics

| | All records | Active only |
|---|---:|---:|
| Male | 53.6% (4,801) | 53.7% (4,291) |
| Female | 46.4% (4,149) | 46.3% (3,693) |

### Education mix (active employees)

| Education Level | Headcount | Avg. Salary |
|---|---:|---:|
| Bachelor | 4,809 | $69,929 |
| High School | 1,633 | $62,115 |
| Master | 1,109 | $82,450 |
| PhD | 433 | $86,166 |

### Compensation

| Metric | Value |
|---|---:|
| Average salary (active) | $70,951 |
| Median salary (active) | $66,598 |
| Salary range | $51,835 – $149,377 |

**Average salary by department:**

| Department | Avg. Salary |
|---|---:|
| IT | $81,855 |
| Finance | $76,667 |
| Sales | $76,132 |
| Marketing | $67,425 |
| Customer Service | $65,841 |
| Operations | $65,463 |
| HR | $64,239 |

**Highest-paid roles (active, avg. salary):**

| Job Title | Avg. Salary | Headcount |
|---|---:|---:|
| Finance Manager | $125,518 | 8 |
| IT Manager | $113,714 | 25 |
| Sales Manager | $103,349 | 41 |
| Operations Manager | $96,588 | 49 |
| Marketing Manager | $95,976 | 23 |
| Software Developer | $93,372 | 569 |

**Gender pay gap by education (active, avg. salary):**

| Education | Female | Male |
|---|---:|---:|
| High School | $61,342 | $62,782 |
| Bachelor | $65,715 | $73,519 |
| Master | $85,933 | $79,496 |
| PhD | $92,749 | $79,614 |

### Performance ratings (all records)

| Rating | Share |
|---|---:|
| Good | 42.0% |
| Satisfactory | 27.9% |
| Excellent | 17.5% |
| Needs Improvement | 12.5% |

Performance skews strongly with education: 47.7% of PhD holders and 35.4% of Master's holders are rated "Excellent," vs. 12.9% of High School-level employees — who also account for 34.0% "Needs Improvement" ratings, the highest of any group.

### Age distribution (active employees, as of dataset snapshot)

| Age Band | Headcount |
|---|---:|
| <25 | 869 |
| 25–34 | 1,763 |
| 35–44 | 2,474 |
| 45–54 | 1,926 |
| 55+ | 952 |

Median age: 40 · Mean age: 40.4

### Top locations (active employees)

| State | Headcount |
|---|---:|
| New York | 5,579 |
| Michigan | 867 |
| Pennsylvania | 392 |
| North Carolina | 390 |
| Illinois | 251 |
| Ohio | 249 |
| Virginia | 162 |
| West Virginia | 94 |

## Employee Records (detail view)

![Employee Records Dashboard](images/employee-records-dashboard.png)

A filterable, row-level view of every employee — ID, name, age, education, role, department, location, salary, hire status, and tenure — with filters by department and employment status.

## Key insights

- **Finance has the highest attrition rate (13.9%)** despite being the third-smallest department, and pays the second-highest average salary after IT — suggesting attrition there is not purely compensation-driven.
- **Terminated employees leave early:** average tenure at exit is 1.9 years vs. 6.5 years for active staff, pointing to an onboarding/early-retention gap rather than late-career churn.
- **Education correlates with both pay and performance:** PhD holders earn ~39% more than High School-level employees on average and are rated "Excellent" nearly 4x as often.
- **A gender pay gap reverses by education level:** men out-earn women at High School and Bachelor levels, while women out-earn men at Master's and PhD levels in this dataset.
- **Workforce is concentrated geographically:** New York alone accounts for ~70% of active headcount.

## Tech stack

- **Visualization:** Tableau (Tableau Public)
- **Data:** CSV, processed with Python/pandas for the metrics above
- **Source data:** [`data/dataset.csv`](data/dataset.csv)

## Repository structure

```
hr-analytics-dashboard/
├── README.md
├── data/
│   └── dataset.csv              # source data (8,950 employee records)
├── images/
│   ├── hr-summary-dashboard.png # dashboard: overview, demographics, income
│   └── employee-records-dashboard.png  # dashboard: row-level employee detail
├── HRSummary.pdf                 # original dashboard export (PDF)
└── EmpRecords.pdf                 # original dashboard export (PDF)
```

## Reproducing the metrics

The figures above were derived directly from `data/dataset.csv` with pandas:

```python
import pandas as pd

df = pd.read_csv("data/dataset.csv", sep=";")
df["Termdate"] = pd.to_datetime(df["Termdate"], format="%d/%m/%Y", errors="coerce")
df["Status"] = df["Termdate"].isna().map({True: "Active", False: "Terminated"})

attrition_rate = (df["Status"] == "Terminated").mean() * 100
print(f"Attrition rate: {attrition_rate:.2f}%")
```

## Author

**Sree Malathik**
[GitHub](https://github.com/Sreemalathi) · [LinkedIn](https://linkedin.com/in/sree-malathik)

Built as part of the WBS Coding School Data Analytics with AI bootcamp.
