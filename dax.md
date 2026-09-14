# HR Analytics Dashboard — DAX

## Measures

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

## Calculated Columns

```DAX
CF_current Employee =
IF(
    'HR data'[Attrition] = "No",
    1,
    0
)
```

```DAX
CF_attrition label =
IF(
    'HR data'[Attrition] = "Yes",
    "Ex-Employees",
    "Current Employees"
)
```

```DAX
CF_age band =
SWITCH(
    TRUE(),
    'HR data'[Age] < 25, "Under 25",
    'HR data'[Age] <= 34, "25 - 34",
    'HR data'[Age] <= 44, "35 - 44",
    'HR data'[Age] <= 54, "45 - 54",
    "Over 55"
)
```

## Department-wise Attrition

```DAX
Department Attrition =
CALCULATE(
    [Attrition Count],
    ALLEXCEPT(
        'HR data',
        'HR data'[Department]
    )
)
```

## Education Field-wise Attrition

```DAX
Education Field Attrition =
CALCULATE(
    [Attrition Count],
    ALLEXCEPT(
        'HR data',
        'HR data'[Education Field]
    )
)
```

## Job Satisfaction Rating

```DAX
Job Satisfaction Count =
COUNT('HR data'[Job Satisfaction])
```

## Age Group Attrition

```DAX
Age Group Attrition =
CALCULATE(
    [Attrition Count],
    ALLEXCEPT(
        'HR data',
        'HR data'[CF_age band]
    )
)
```

## Gender-wise Attrition

```DAX
Gender Attrition =
CALCULATE(
    [Attrition Count],
    ALLEXCEPT(
        'HR data',
        'HR data'[Gender]
    )
)
```

## Useful Percentage Measures

```DAX
Active Employee Rate =
DIVIDE(
    [Active Employees],
    [Overall Employees],
    0
)
```

```DAX
Attrition Percentage =
DIVIDE(
    [Attrition Count],
    [Overall Employees],
    0
)
```

## Formatting

Set these measures to **Percentage** format in Power BI:

- `Attrition Rate`
- `Active Employee Rate`
- `Attrition Percentage`

Set `Average Age` to **2 decimal places**.
