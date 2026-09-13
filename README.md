# UBBER AND RAPIDO DRIVER DATA ANALYSIS & DASHBOARD
<p align="center">
  <img src="images/data_analyst_avatar.png" width="180" style="border-radius:50%">
</p>

<h1 align="center">🚖 Uber & Rapido Driver Analytics | Excel to Power BI</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Excel-Data%20Cleaning-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white">
  <img src="https://img.shields.io/badge/Power%20BI-Visualization-06C167?style=for-the-badge&logo=powerbi&logoColor=white">
  <img src="https://img.shields.io/badge/Project-Completed-121212?style=for-the-badge">
</p>

---

### 👨‍💻 About Me
Aspiring Data Analyst | Excel, Power BI, SQL, DAX
Focused on end-to-end projects: Cleaning → Modeling → Visualization → Business Insights

---

### 📌 Project Overview
Analyzed 46K drivers for Uber & Rapido to solve business problems like 50% inactive fleet, low 3.83 avg rating, and 34% selection rate.
This project shows my complete workflow from raw messy data to final executive dashboards.

### 🔄 End-to-End Workflow

#### Phase 1: Data Cleaning in Excel (First Step)
Raw file had major quality issues. Cleaned entirely in Excel before Power BI.

**1. Duplicate & Structure Check:**
- Removed duplicate Driver IDs using `Remove Duplicates`
- Checked total rows: 46K+ records
- Trimmed extra spaces using `=TRIM()` and `=CLEAN()`

**2. Standardized Text Columns:**
- `PLATFORM` column had `UNKNOWN`, `uber`, `UBER`, `Uber_` - Standardized to `Uber, Rapido, Ola, Unknown` using `PROPER()` + Find & Replace
- `EXPERIENCE LEVEL` had `fresher, Fresher, FRESHER, 0-1yr` - Fixed to `FRESHER, 0-1 YR, 1-3 YR, 3-5 YR, 5+ YR`
- `REJECTION REASON` - 40% was `UNKNOWN` - Marked as `Needs Review` instead of deleting to track data quality

**3. Data Type Fix (Critical for Blank Visual Issue):**
- `COMMUNICATION SCORE, CUSTOMER HANDLING SCORE, DRIVING TEST SCORE` were stored as Text in Excel
- Converted to Number using `Data > Text to Columns > General`
- `AGE` column had text values like `38 yrs` - Extracted number using `=VALUE(LEFT())`

**4. Null & Missing Value Handling:**
- `DOCUMENT VERIFICATION SCORE` had blanks - Replaced with 0 and flagged as `Failed`
- `BACKGROUND CHECK STATUS` - `Pending` kept as is for business tracking
- `DAILY EARNING` blanks replaced with average earning

**5. Outlier Check:**
- Found spike at Age 38 with very high scores - Kept but flagged as outlier for Power BI
- Rating >5 found in 2 rows - Corrected to 5 max

**6. Final Cleaned File Saved As:** `driver_data_cleaned.xlsx` - Ready for Power BI import.

#### Phase 2: Data Modeling & Visualization in Power BI

**1. Power Query:**
- Imported cleaned Excel file
- Verified Data Types again (Whole Number for Scores)
- Created reference tables: `City Master`, `Platform Master`

**2. DAX Measures Created:**
```DAX
Total Drivers = COUNT(driver_data[Driver ID])
Active Drivers = CALCULATE(COUNT(driver_data[Driver ID]), driver_data[Is_Active]="Yes")
Avg Rating = AVERAGE(driver_data[Rating])
Avg Daily Earning = AVERAGE(driver_data[Daily Earning])
Selection Rate = DIVIDE([Selected Count], [Total Interview])
Document Pass Rate = DIVIDE([Doc Passed], [Total Interview])
