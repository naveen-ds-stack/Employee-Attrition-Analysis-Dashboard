# Workforce Attrition Risk Analysis

37.9% of 1,000 employees left. Overtime workers leave at 43.7% vs 32.8% for non-overtime staff — the single most actionable signal in the dataset. This project identifies the behavioural and structural drivers of attrition across departments, age bands, and salary tiers, and delivers an interactive Excel dashboard for HR leadership.

---

## Business Problem

High attrition is expensive. Replacing an employee costs 50–200% of their annual salary in recruiting, onboarding, and lost productivity. This project goes beyond reporting the attrition rate to identifying which employee groups are highest risk, which drivers are actionable, and what HR can do about each one.

---

## Key Findings

| Finding | Detail |
|---|---|
| Overall attrition rate | 37.9% (379 of 1,000 employees left) |
| Highest risk department | Sales — 42.4% attrition |
| Second highest department | Finance — 40.6% attrition |
| Lowest risk department | HR — 22.5% (worth studying for replicable practices) |
| Overtime workers | 43.7% attrition vs 32.8% non-overtime — strongest single signal |
| New employees (<2 yrs) | 46.7% attrition — highest of any tenure group |
| Young employees (<30) | 47.3% attrition — highest of any age group |
| Frequent travelers | 44.5% attrition — hybrid or travel allowances may help |
| Salary finding | Low salary band (< ₹50K) has one of the lowest attrition rates (28.9%) — salary alone is not the primary driver |

**Critical insight:** The High salary band (₹80–120K) shows the highest attrition at 41%. This challenges the assumption that paying more retains employees. Workload, growth opportunities, and work-life balance appear to be stronger drivers than compensation at these salary levels.

---

## Analytical Workflow

**Stage 1 — Raw Data**
- 1,000 employee records, 18 columns
- Source: HR Information System
- Intentional missing values included for data cleaning practice

**Stage 2 — Data Cleaning**
- 38 missing values across Age, Department, Monthly Salary, and Job Satisfaction
- Each imputed with a documented method: median (continuous), mode (categorical), or "Unknown" (unresolvable)
- Domain logic validation: "Years_At_Company cannot exceed Age minus 21" applied to catch impossible records
- Outlier detection: IQR method for Age and Salary, Z-score for Distance_From_Home
- Duplicate check: 0 duplicates found
- Full audit trail documented in the Documentation sheet

**Stage 3 — Feature Engineering (7 derived columns)**

| Column | Logic | Purpose |
|---|---|---|
| Attrition_Flag | 1/0 from Yes/No | Enables numeric aggregation |
| Age_Group | Young (<30), Mid (30-40), Senior (40-50), Veteran (50+) | Age-band analysis |
| Salary_Band | Low (<50K), Mid (50-80K), High (80-120K), Premium (120K+) | Compensation segment analysis |
| Tenure_Group | New (<2 yrs), Developing (2-5), Established (5-10), Veteran (10+) | Tenure risk analysis |
| Satisfaction_Label | Text mapped from 1–5 score | Dashboard readability |
| Performance_Label | Text mapped from 1–5 score | Dashboard readability |
| WLB_Label | Text mapped from 1–5 score | Dashboard readability |

**Stage 4 — Analysis (6 breakdown tables)**
- Attrition rate by Department, Age Group, Salary Band, Tenure Group, OverTime, Business Travel
- Each table includes headcount, leavers, attrition rate, and risk flag

**Stage 5 — Dashboard**
- One-page interactive view with Department and Gender slicers
- KPI cards: Total Employees, Employees Left, Attrition Rate, Retention Rate, Avg Salary, Avg Tenure, Avg Age
- 6 charts: Department, Age Group, Salary Band, Tenure Group (bar), OverTime (stacked bar), Business Travel (donut)

---

## Workbook Structure

| Sheet | Purpose |
|---|---|
| Raw_Data | Original 1,000-row, 18-column dataset |
| Data_Cleaning | Cleaned dataset with 27 columns including 7 engineered features |
| Documentation | Full audit trail: null checks, domain logic rules, outlier methodology, cleaning log |
| Analysis | 6 breakdown tables with attrition rates and risk flags |
| Dashboard | Interactive one-page view with slicers and KPI cards |

---

## Tech Stack

- Excel PivotTables and PivotCharts
- Slicers for interactive cross-chart filtering
- Formulas: COUNTIF, AVERAGE, QUARTILE, SKEW, STDEV, nested IF for feature binning
- IQR and Z-score outlier detection
- Power BI for departmental heatmaps and tenure breakdown visualisations

---

## Repository Structure

```
workforce-attrition-risk-analysis/
├── README.md
└── Employee_Attrition_Analysis.xlsx
    ├── Raw_Data
    ├── Data_Cleaning
    ├── Documentation
    ├── Analysis
    └── Dashboard
```

---

## How to Use

1. Download `Employee_Attrition_Analysis.xlsx` and open in Excel (2016 or later recommended for full slicer support)
2. Go to the **Dashboard** tab for the interactive view
3. Use the **Department** and **Gender** slicers to filter all charts and KPIs simultaneously
4. Open the **Analysis** tab to see the breakdown tables behind each chart
5. Check the **Documentation** tab for the full data cleaning methodology and audit trail

---

## Planned Enhancements

- Additional slicers for OverTime, Business Travel, Age Group, and Tenure Group
- A toggle to isolate "Left" vs "Stayed" employees across all visuals simultaneously
- Migration to Power BI for richer interactivity and drill-through capability
