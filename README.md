# HR Analytics Dashboard (Power BI)

An interactive HR Analytics Dashboard built in **Power BI** to explore and explain **employee attrition** across demographics and job factors. The report ships with two pages:

- **Page 1 – Attrition Overview** (executive KPIs & high-level trends)
- **Page 2 – Workforce Profile & Trends** (drivers of attrition like gender, marital status, business travel, overtime, distance, education field)

> Sample output (from the included report): **1,470 employees**, **237 attritions**, **16.1% attrition rate**.

---

## 📷 Screenshots

Place your images in `assets/` and reference them here, e.g.

- Page 1 – Overview  
  `![Overview](Attrition Overview.png)`
- Page 2 – Workforce Profile  
  `![Profile](Workforce Profile & Trends.png)`

---

## 🧭 Report Pages & Highlights

### Page 1 – Attrition Overview
- KPI cards: Count of Employees, Attrition, Attrition Rate, Avg Age, Avg Salary, Avg Years. :contentReference[oaicite:2]{index=2}
- Visuals: Attrition by Education, Age, Salary Slab, Years at Company, Job Role; Job Satisfaction matrix.

### Page 2 – Workforce Profile & Trends
- Gender distribution and **Attrition Rate by Gender** (e.g., ~17% vs ~14.8%).
- **Attrition Rate by Marital Status** (Single highest). 
- **Attrition Rate by Business Travel** (Travel_Frequently ≈ 24.9% > Travel_Rarely > Non-Travel).
- **Attrition Rate by OverTime** (Yes ≈ 30.5% vs No ≈ 10.4%).
- **Distance from Home (Buckets)** with attrition % trend (0–5 km → 6–10 km → 10+ km). 

---

## 🧰 Tech Stack

- **Power BI Desktop**
- **DAX** for measures and calculated columns

---

## 📂 Data

Typical columns used (sample): `EmpID, Age, AgeGroup, Attrition, BusinessTravel, Department, DistanceFromHome, Education, EducationField, EnvironmentSatisfaction, Gender, JobLevel, JobRole, JobSatisfaction, MaritalStatus, MonthlyIncome, SalarySlab, OverTime, PercentSalaryHike, PerformanceRating, RelationshipSatisfaction, TotalWorkingYears, TrainingTimesLastYear, WorkLifeBalance, YearsAtCompany, YearsInCurrentRole, YearsSinceLastPromotion, YearsWithCurrManager`, etc.

Put your data file(s) in a `data/` folder, e.g. `data/HR_Analytics.csv` or include the `.pbix` with data imported.

---

## ⚙️ DAX 

### 1) Attrition Rate (Measure)
```DAX
Attrition Rate =
DIVIDE(
    CALCULATE(COUNTROWS('HR_Analytics'), 'HR_Analytics'[Attrition] = "Yes"),
    COUNTROWS('HR_Analytics')
)
