# HR Analytics Dashboard

A Tableau dashboard analyzing employee dataset covering headcount, attrition, demographics, compensation, and performance across departments and workforce (2015–2024).

**[View the live interactive dashboard on Tableau Public](https://public.tableau.com/views/HRDashboard_17900643829960/EmpRecords?:language=en-GB&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

![HR Summary Dashboard](images/hr-summary-dashboard.png)

## Key Metrics

| Metric | Value |
|---|---:|
| Total employee records | 8,950 |
| Active employees | 7,984 (89.2%) |
| Terminated employees | 966 (10.8%) |
| Departments | 7 |
| States represented | 8 |
| Data window | 2015–2024 |
| Gender split | 54% Male / 46% Female |
| Average salary | $70,951 |
| Avg. tenure (active) | 6.5 years |

A full breakdown by department, education, tenure, and compensation is available in the dashboard above.

## Dataset

- **File:** [`data/dataset.csv`](data/dataset.csv) — 8,950 rows, semicolon-delimited
- **Fields:** Employee ID, First/Last Name, Gender, State, City, Education Level, Birthdate, Hire Date, Termination Date, Department, Job Title, Salary, Performance Rating
- **Note:** Data in this file are synthetic/sample data generated for portfolio and learning purposes.

## Employee Records (detail view)

![Employee Records Dashboard](images/employee-records-dashboard.png)

A filterable, row-level view of every employee — ID, name, age, education, role, department, location, salary, hire status and tenure - with filters by department and employment status.

**[View on Tableau Public](https://public.tableau.com/views/HRDashboard_17900643829960/EmpRecords?:language=en-GB&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

## Tech stack

- **Visualization:** Tableau (Tableau Public)
- **Source data:** [`data/dataset.csv`](data/dataset.csv)

## Repository structure

```
hr-analytics-dashboard/
├── README.md
├── data/
│   └── dataset.csv                         # source data (8,950 employee records)
└── images/
    ├── hr-summary-dashboard.png            # dashboard: overview, demographics, income
    └── employee-records-dashboard.png      # dashboard: row-level employee detail
```

## Author

**Sree Malathik**
[GitHub](https://github.com/Sreemalathi) · [LinkedIn](https://linkedin.com/in/sree-malathik)

