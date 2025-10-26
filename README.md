## Requirements
- Power BI Desktop (May 2024+)
- RAM: 8GB+

## How to run
1. Clone/download repo.
2. Deschide `HR_Analytics_Dashboard.pbix` în Power BI Desktop.
3. Dacă e nevoie, actualizează calea spre `WA_Fn-UseC_-HR-Employee-Attrition.csv` (Transform data → Data source settings → Change Source).
4. Refresh.

## Key DAX (principalele măsuri)
```DAX
Employees = DISTINCTCOUNT('HR'[EmployeeNumber])
Attrition Rate =
DIVIDE( CALCULATE([Employees], 'HR'[Attrition] = "Yes"), [Employees] )
% OverTime =
DIVIDE( CALCULATE([Employees], 'HR'[OverTime] = "Yes"), [Employees] )
Average Monthly Income = AVERAGE('HR'[MonthlyIncome])
Average Years at Company = AVERAGE('HR'[YearsAtCompany])
Average Job Satisfaction = AVERAGE('HR'[JobSatisfaction])
Average Environment Satisfaction = AVERAGE('HR'[EnvironmentSatisfaction])
Attrition Rate by Department =
DIVIDE( CALCULATE([Employees], 'HR'[Attrition]="Yes"), CALCULATE([Employees]) )
markdown
Copy code
## Data dictionary (scurt)
- `Attrition` (Yes/No) – status plecare
- `Department`, `JobRole`, `JobLevel`
- `MonthlyIncome` – venit lunar
- `YearsAtCompany`, `TotalWorkingYears`
- `OverTime` (Yes/No)
- `JobSatisfaction`, `EnvironmentSatisfaction` (1–4)

## Executive summary
- Attrition total ~16%; cel mai ridicat în Sales/HR.
- ~28% angajați cu OverTime; corelație pozitivă cu attrition.
- Satisfacția medie ~2.7/4; oportunități în departamentele cu scoruri <3.

## Screenshots
![Dashboard](images/dashboard_preview.png)
