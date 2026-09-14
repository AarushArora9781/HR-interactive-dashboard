# HR Analytics Dashboard

An interactive **HR Analytics Dashboard** built in **Power BI** to analyze employee data, attrition, employee demographics, job satisfaction, and other HR metrics.

## Dashboard Overview

The dashboard provides a quick view of important HR KPIs and allows users to explore employee and attrition data using interactive visuals and filters.

### Key KPIs

- **Overall Employees:** 1,470
- **Attrition Count:** 237
- **Attrition Rate:** 16.12%
- **Active Employees:** 1,233
- **Average Age:** 36.92

## Dashboard Features

### Department-wise Attrition
Shows employee attrition across different departments such as:

- R&D
- Sales
- HR

### Education Field-wise Attrition
Analyzes attrition based on employees' education fields and age groups, with gender-wise comparison.

### Job Satisfaction Rating
Displays job satisfaction ratings across different job roles and provides a total employee count for each role.

### Age Group Analysis
Employees are grouped into the following age bands:

- Under 25
- 25 - 34
- 35 - 44
- 45 - 54
- Over 55

The dashboard shows attrition by each age group.

### Education Field Attrition
Compares attrition counts across different education fields.

### Gender-wise Analysis
Allows comparison of employee and attrition data between female and male employees.

## Tools & Technologies

- **Power BI**
- **DAX**
- **Data Visualization**
- **Data Analysis**
- **Power BI Slicers & Filters**

## DAX

The project uses DAX measures and calculated columns for KPI calculations, employee status, age-group classification, attrition analysis, and percentage calculations.

All DAX formulas used in the dashboard are available in:

[`dax.md`](dax.md)

## Key DAX Measures

```DAX
Overall Employees =
SUM('HR data'[Employee Count])
```

```DAX
Attrition Count =
CALCULATE(
    SUM('HR data'[Employee Count]),
    'HR data'[Attrition] = "Yes"
)
```

```DAX
Active Employees =
CALCULATE(
    SUM('HR data'[Employee Count]),
    'HR data'[Attrition] = "No"
)
```

```DAX
Attrition Rate =
DIVIDE(
    [Attrition Count],
    [Overall Employees],
    0
)
```

```DAX
Average Age =
AVERAGE('HR data'[Age])
```

## Project Structure

```text
HR-Analytics-Dashboard/
│
├── HR Data.xlsx
├── dax.md
├── README.md
└── HR Analytics Dashboard.pbix
```

## How to Use

1. Open the `.pbix` file in **Microsoft Power BI Desktop**.
2. Use the available filters and visuals to explore the HR data.
3. Select departments, education fields, age groups, job roles, or gender categories to analyze specific segments.
4. Refer to `dax.md` for the DAX measures and calculated columns used in the dashboard.

## Project Objective

The objective of this project is to transform raw HR data into an interactive dashboard that helps identify employee attrition patterns and provides useful insights into workforce demographics, job satisfaction, and employee status.
