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
AttritionRate = SUM(HR_Analytics[Attrition Count])/SUM(HR_Analytics[EmployeeCount])

### 2) Distance Bucket (Calculated Column)

Create a New Column:

Distance Bucket = 
SWITCH(
    TRUE(),
    'HR_Analytics'[DistanceFromHome] >= 0 && 'HR_Analytics'[DistanceFromHome] <= 5, "0-5 km",
    'HR_Analytics'[DistanceFromHome] > 5 && 'HR_Analytics'[DistanceFromHome] <= 10, "6-10 km",
    'HR_Analytics'[DistanceFromHome] > 10, "10+ km",
    "Unknown"
)

### 3) Distance Sort (Calculated Column) — for correct left→right order
Distance Sort = 
SWITCH(
    TRUE(),
    'HR_Analytics'[DistanceFromHome] >= 0 && 'HR_Analytics'[DistanceFromHome] <= 5, 1,
    'HR_Analytics'[DistanceFromHome] > 5 && 'HR_Analytics'[DistanceFromHome] <= 10, 2,
    'HR_Analytics'[DistanceFromHome] > 10, 3,
    4
)

## Option A — Build from scratch (reproducible)

1. Get Data → Import data/HR_Analytics.csv.

2. Create the DAX objects above (one measure + two columns).

3. Build visuals:

    Page 1: KPIs + charts (Education, Age, Salary Slab, Years at Company, Job Role, Job Satisfaction). 

    Page 2: Donut (Gender), Bar/Column charts for Attrition Rate by Gender/Marital Status/Business Travel/OverTime/EducationField and a Line/Column for Distance Bucket. 

4. Sort the Distance chart by Distance Sort to enforce 0–5 km → 6–10 km → 10+ km.

 ## Repo Structure  .
├── assets/
│   ├── page1_overview.png
│   └── page2_profile.png
├── data/
│   └── HR_Analytics.csv
├── HR_Analytics_Dashboard.pbix
└── README.md

## Reference Output

The included PDF shows representative visuals, KPIs, and percentages used in this project (e.g., KPIs on Page 1; gender/business travel/overtime/distance analyses on Page 2)
