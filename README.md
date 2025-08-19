# HR Analytics Dashboard (Power BI)

An interactive HR Analytics Dashboard built in **Power BI** to explore and explain **employee attrition** across demographics and job factors. The report ships with two pages:

- **Page 1 – Attrition Overview** (executive KPIs & high-level trends)
- **Page 2 – Workforce Profile & Trends** (drivers of attrition like gender, marital status, business travel, overtime, distance, education field)

> Sample output (from the included report): **1,470 employees**, **237 attritions**, **16.1% attrition rate**. :contentReference[oaicite:1]{index=1}

---

## 📷 Screenshots

Place your images in `assets/` and reference them here, e.g.

- Page 1 – Overview  
  `![Overview](assets/page1_overview.png)`
- Page 2 – Workforce Profile  
  `![Profile](assets/page2_profile.png)`

---

## 🧭 Report Pages & Highlights

### Page 1 – Attrition Overview
- KPI cards: Count of Employees, Attrition, Attrition Rate, Avg Age, Avg Salary, Avg Years. :contentReference[oaicite:2]{index=2}
- Visuals: Attrition by Education, Age, Salary Slab, Years at Company, Job Role; Job Satisfaction matrix. :contentReference[oaicite:3]{index=3}

### Page 2 – Workforce Profile & Trends
- Gender distribution and **Attrition Rate by Gender** (e.g., ~17% vs ~14.8%). :contentReference[oaicite:4]{index=4}
- **Attrition Rate by Marital Status** (Single highest). :contentReference[oaicite:5]{index=5}
- **Attrition Rate by Business Travel** (Travel_Frequently ≈ 24.9% > Travel_Rarely > Non-Travel). :contentReference[oaicite:6]{index=6}
- **Attrition Rate by OverTime** (Yes ≈ 30.5% vs No ≈ 10.4%). :contentReference[oaicite:7]{index=7}
- **Distance from Home (Buckets)** with attrition % trend (0–5 km → 6–10 km → 10+ km). :contentReference[oaicite:8]{index=8}

---

## 🧰 Tech Stack

- **Power BI Desktop**
- **DAX** for measures and calculated columns

---

## 📂 Data

Typical columns used (sample): `EmpID, Age, AgeGroup, Attrition, BusinessTravel, Department, DistanceFromHome, Education, EducationField, EnvironmentSatisfaction, Gender, JobLevel, JobRole, JobSatisfaction, MaritalStatus, MonthlyIncome, SalarySlab, OverTime, PercentSalaryHike, PerformanceRating, RelationshipSatisfaction, TotalWorkingYears, TrainingTimesLastYear, WorkLifeBalance, YearsAtCompany, YearsInCurrentRole, YearsSinceLastPromotion, YearsWithCurrManager`, etc.

Put your data file(s) in a `data/` folder, e.g. `data/HR_Analytics.csv` or include the `.pbix` with data imported.

---

## ⚙️ DAX (copy/paste)

> Use these exactly-named fields/tables or adjust to your model.

### 1) Attrition Rate (Measure)
```DAX
Attrition Rate =
DIVIDE(
    CALCULATE(COUNTROWS('HR_Analytics'), 'HR_Analytics'[Attrition] = "Yes"),
    COUNTROWS('HR_Analytics')
)
