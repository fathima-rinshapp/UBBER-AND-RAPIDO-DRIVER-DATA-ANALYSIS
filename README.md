# Uber and Rapido Driver Data Analysis 

## Project Overview
End-to-end data analysis project on 46K+ drivers for Uber & Rapido. 
The project covers the complete journey from candidate interview to active driver performance.

**Objective:** To identify why 50% fleet is inactive, why selection rate is only 34%, and who are the top vs low performing drivers.

## Workflow: Excel to Power BI

### Phase 1: Data Cleaning using Excel
Raw data had quality issues, cleaned before importing to Power BI.

1. **Duplicate Check:** Removed duplicate Driver IDs using Remove Duplicates.
2. **Text Cleaning:** Used TRIM() and CLEAN() to remove extra spaces.
3. **Standardization:**
      - Platform column: Fixed `uber, UBER, Uber_, UNKNOWN` to `Uber, Rapido, Ola, Unknown`
      - Experience Level: Fixed `fresher, FRESHER` to `FRESHER, 0-1 YR, 1-3 YR, 3-5 YR`
      - Rejection Reason: 40% was UNKNOWN - flagged as Needs Review
4. **Data Type Fix:** Converted Communication Score, Driving Score, Customer Handling Score from Text to Number using Text to Columns. This fixed the blank visual issue.
5. **Null Handling:** Document Score blanks replaced with 0 and marked as Failed. Background Check Pending kept for tracking.
6. **Outlier Check:** Age 37 had abnormal high scores - flagged. Rating >5 corrected to 5.

**Output:** `UBER DRIVER DATA CLEANED.xlsx`
https://drive.google.com/drive/folders/1xj6f0WECKtdM7-LkbRWQfJg3DftM7ux5?usp=sharing
Final clean file imported to Power BI.

### Phase 2: Data Visualization using Power BI

**Data Modeling:**
- Imported cleaned Excel file to Power Query
- Created DAX Measures:
    - Total Drivers = COUNT(Driver ID)
    - Active Drivers = COUNT where Is_Active = Yes
    - Avg Rating = AVERAGE(Rating)
    - Selection Rate = Selected / Total Interview
    - Document Pass Rate = 22.79%

**Dashboard Theme:**
- Dark Theme #121212 with Neon Green #06C167

### Dashboards Created

**1. Executive Overview**
- KPIs: Total Drivers 46K, Active Drivers 23K, Avg Daily Earning 1.43K, Avg Rating 3.83
- Visuals: Active Driver by City Map, Platform Split Bar Chart, Rating Distribution Donut, Language Distribution

**2. Driver Performance Analysis**
- KPIs: Top Rated 4+ (11K), Low Rated <3 (2K), High Earners >2K (10K), Low Completion <50% (9K)
- Visuals: Trip Completion Rate by Rating, Driver by Vehicle Type Donut, Experience vs Platform Treemap, Score by Age Line Chart

**3. Interview Result Analysis**
- KPIs: Total Interview 46K, Selection Rate 34%, Document Pass Rate 22.79%, Avg Interview Score 6.42
- Visuals: Background Check Status Donut, Interview Funnel (Selected/Rejected/On Hold), Rejection Reason Bar Chart, Platform Comparison

**4. Insights & Recommendations Page**
- Consolidated findings from all 3 dashboards

## Key Insights

- 50% fleet is idle (23K inactive out of 46K)
- Average rating is 3.83, 30% drivers are rating 3 only
- 9K drivers have less than 50% trip completion
- Top 3 hubs: Mumbai, Pune, Bangalore
- Selection rate is only 34% due to 77% document verification failure
- Rejection Reason UNKNOWN is highest - data quality issue
- Fresher candidates scored higher than 3-5 Yrs experienced

## Recommendations

- Re-engage 23K inactive drivers with bonus
- Deactivate 2K low rated and 9K low completion drivers
- Retain 11K top rated and 10K high earners with incentives
- Fix document verification process immediately
- Make Rejection Reason mandatory to remove UNKNOWN
- Focus hiring in Top 5 cities only
- Provide language training for 1-language drivers

## Tools Used
- **Excel:** Data Cleaning, TRIM, Text to Columns, Remove Duplicates
- **Power BI:** Power Query, DAX, Data Modeling, Visualization
- **DAX:** COUNT, AVERAGE, CALCULATE, DIVIDE

## Files in Repository
- `UBER AND RAPIDO DRIVER DATA.pbix` - Power BI File
- `UBER DRIVER DATA CLEANED.xlsx` - Cleaned Data
- `uber_rapido_driver_dirty.csv` - Raw Data
- `/images` - Dashboard Screenshots

## How to Run
1. Download the .pbix file
2. Open in Power BI Desktop
3. Explore dashboards with slicers

## Author
**Aspiring Data Analyst | Excel | Power BI **

---
⭐ Star this repository if you found it useful!
