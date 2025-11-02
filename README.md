<!-- PROJECT TITLE BANNER -->
<div align="center">

# 🌦️ Weather-Aware Accident Risk Platform  
### *A Data-Driven Approach to Understand How Weather Impacts Road Accidents in the U.S.*

[![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Dataset](https://img.shields.io/badge/Dataset-Kaggle-blue?logo=kaggle)](https://www.kaggle.com/datasets/ajjjuupd/us-accedent-updated)
[![Dynamic Connection](https://img.shields.io/badge/Data%20Source-SharePoint%20(Online)-orange)](#)
[![License](https://img.shields.io/badge/Status-Completed-success)](#)
</div>

---

## 🚗 Project Overview

The **Weather-Aware Accident Risk Platform** is an analytical project built to explore the relationship between **weather conditions** and **road accidents** across the United States.  

This platform helps public safety departments, policy makers, and road transport agencies gain a **real-time understanding** of accident trends. Using **Power BI**, the dashboard provides interactive visuals showing how factors such as **temperature, visibility, humidity, and precipitation** affect road safety.

---

## 🎯 Project Goals

1. **Understand the relationship** between weather parameters and accident occurrence or severity.  
2. **Visualize accident trends** across U.S. regions using Power BI dashboards.  
3. **Build dynamic connectivity** via SharePoint for live, auto-refreshing data.  
4. **Generate actionable insights** that improve awareness and safety measures.  
5. **Establish scalability** to include more datasets such as vehicle types or traffic data in the future.  

---

<div align="center">

✨ *Scroll down to explore how the dataset was sourced, transformed, modeled, and visualized in Power BI.* ✨  

</div>

---
## 🧩 Data Source & Dynamic Data Connection

### 📦 Dataset Origin
The data used in this project comes from **Kaggle**, a trusted platform for open datasets.  
We used the following dataset for analysis:

🔗 **Dataset Link:** [US Accidents (Updated)](https://www.kaggle.com/datasets/ajjjuupd/us-accedent-updated)

This dataset contains detailed records of road accidents across the United States, including:
- Accident ID, severity, and location (city, state, zipcode)
- Time and date of the accident  
- Weather details such as temperature, humidity, pressure, visibility, wind speed, and precipitation  
- Environmental and roadway conditions (amenity, bump, crossing, etc.)

---

### 🌐 Dynamic Data Connection (SharePoint Integration)

To ensure our Power BI dashboard reflects **live data updates**, we connected the dataset dynamically using **Microsoft SharePoint / OneDrive**.

### ⚙️ Connection Workflow

> **End-to-End Data Flow:** From Kaggle dataset to Power BI dynamic dashboard

---

#### 🟨 Step 1 – Kaggle Dataset
We collected the accident data from [Kaggle](https://www.kaggle.com/datasets/ajjjuupd/us-accedent-updated), which contains U.S. accident details such as severity, location, weather, and time.

⬇️

#### 🟩 Step 2 – Data Cleaning & Filtering
Cleaned the dataset in **Excel / Power Query**, removing unnecessary columns, fixing missing values, and converting date-time fields.

⬇️

#### 🟦 Step 3 – Upload to SharePoint / OneDrive
The cleaned files were uploaded to **SharePoint Online / OneDrive** to enable live web-based access.

⬇️

#### 🟪 Step 4 – Generate Shareable Link
A public read-only link was generated from SharePoint to be used directly inside Power BI.

⬇️

#### 🟧 Step 5 – Load into Power BI Desktop
In **Power BI Desktop**, we used:  
`Home → Get Data → Web → Paste URL → Load`  
to fetch both sheets — *Accident_Data* and *Weather_Data*.

⬇️

#### 🟥 Step 6 – Dynamic Dashboard with Auto Refresh
Because the dataset is hosted on SharePoint, any updates to the files are reflected automatically in Power BI after refresh.

---

## 🧮 Data Preparation & Transformation Process

Before creating visual dashboards, the dataset required extensive **cleaning and transformation** to ensure accurate analysis and smooth model performance in Power BI.

---

### 🧹 Step 1 – Initial Data Inspection
The original Kaggle dataset contained **47 columns** and **millions of rows**.  
We reviewed the fields and decided to **retain only those relevant to accident and weather insights.**

**Unnecessary columns removed:**
`Amenity`, `Bump`, `Crossing`, `Give_Way`, `Junction`, `No_Exit`, `Railway`,  
`Roundabout`, `Station`, `Stop`, `Traffic_Calming`, `Traffic_Signal`, `Turning_Loop`,  
`Civil_Twilight`, `Nautical_Twilight`, and similar roadway indicators.

---

### 🧩 Step 2 – Splitting the Dataset
To simplify relationships and improve refresh speed, the dataset was **divided into two structured tables:**

| File Name | Description |
|------------|-------------|
| **Accident_Data** | Includes accident-related details — ID, location, severity, time, distance, city, county, and state. |
| **Weather_Data**  | Includes hourly weather information — temperature, humidity, pressure, visibility, wind speed, and precipitation. |

Each file was uploaded to **SharePoint** and linked dynamically inside Power BI.
---

### 💾 Step 5 – Final Output
- **File 1:** `Accident_Data.xlsx` → uploaded to SharePoint  
- **File 2:** `Weather_Data.xlsx` → uploaded to SharePoint  
- Both connected dynamically in Power BI for live visualization.
  
---
## 🧠 Data Modeling & DAX Calculations

After completing all data preparation steps, datasets were loaded into **Power BI Desktop** for modeling and insight generation.

---

### 🧾 Step 1 – Power Query Editor Refinement
Using **Power Query Editor**, we performed an additional validation before loading data into the report view:

- Checked for **duplicate records** in both Accident and Weather tables.  
- Used **Fill Up** and **Fill Down** transformations to replace missing values.  
- Verified **data profiling** (column quality, distribution, and completeness) to ensure no nulls or format mismatches remained.  

Once data quality was confirmed, both tables were loaded into the **Power BI Report Editor**.

---

### 🧩 Step 2 – Data Modeling Structure
We created a simple yet efficient **data model** linking all tables through key relationships.

**Model Components:**
- `Accident_Data` (Fact Table)  
- `Weather_Data` (Lookup Table)  
- `Dim_Date` – created using the `CALENDAR()` DAX function for date-based analysis  
- `Dim_Hour` – created for time-based insights (0–23 hour range)

**Relationships:**
- `Dim_Date[Date]` → `Accident_Data[Start_Date]` (1:* relationship)  
- `Dim_Hour[Hour]` → `Accident_Data[Start_Hour]` (1:* relationship)  
- `Weather_Data[GeoKey]` → `Accident_Data[GeoKey]` (1:* relationship)  

---

### 📊 Step 3 – DAX Tables and Measures

After the model was built, several **DAX measures** were created to drive insights across dashboards.  
These measures were defined in the **Report Editor** (not Power Query) to allow faster, dynamic calculations.

| Measure Name | Formula / Description |
|---------------|-----------------------|
| **Total Accidents** | `COUNTROWS(Accident_Data)` – Calculates total number of accident records. |
| **Average Temperature (°F)** | `AVERAGE(Weather_Data[Temperature(F)])` – Finds mean temperature during accidents. |
| **Average Visibility (mi)** | `AVERAGE(Weather_Data[Visibility(mi)])` – Measures average visibility at accident time. |
| **Accidents by Severity** | Used in bar visuals to count accidents grouped by `Severity`. |
| **Accidents by Year** | `CALCULATE(COUNTROWS(Accident_Data), VALUES(Dim_Date[Year]))` – Used in line/area charts. |
| **Weather Impact Index** | Custom ratio comparing accident count vs. precipitation and visibility. |

---

<div align="center">

✅ *The data model and DAX measures form the analytical backbone of the Power BI dashboard — ensuring accurate, real-time insights across all visuals.*

</div>

---
## 📈 Dashboard Design & Insights

The **Weather-Aware Accident Risk Platform Dashboard** was designed in **Power BI Desktop** to make the analysis simple, visual, and interactive.  
Each page of the dashboard focuses on specific objectives and KPIs, allowing users to explore accident patterns by weather, time, and location.

---

### 🧭 Page 1 – Overview Dashboard

**Purpose:**  
Provide a one-glance summary of total accident trends across the United States.

**Key Visuals:**
- **Total Accidents (KPI Card):** Displays the total count of accident records.  
- **Accidents by Year (Area Chart):** Shows year-wise fluctuations from 2016 to 2024.  
- **Accidents by Severity (Bar Chart):** Highlights severity levels (1 – minor to 4 – major).  
- **Accidents by State (Map Visual):** Geographic distribution of accident density.  
- **Weather Impact KPI:** Combines average visibility and precipitation levels to show risk intensity.

**Insights:**
- Peak accident years coincide with higher precipitation averages.  
- States with low visibility (fog / snow) show increased severity scores.  

---

### 🌦 Page 2 – Weather Impact Analysis

**Purpose:**  
Study how weather parameters influence accident frequency and severity.

**Visuals Used:**
- **Temperature vs Accidents (Line + Clustered Column Chart)**  
- **Precipitation vs Accidents (Scatter Plot)**  
- **Visibility Impact (Bar Chart)**  
- **Average Humidity and Wind Speed (KPI Cards)**  

**Insights:**
- Accident counts rise sharply when visibility < 5 miles.  
- Light rain / snow conditions contribute to over 40 % of moderate-severity cases.  
- Higher humidity correlates with longer response times in severe accidents.

---

### ⏱ Page 3 – Time & Trend Analysis

**Purpose:**  
Identify the most accident-prone hours, days, and months.

**Visuals Used:**
- **Accidents by Hour (Heatmap):** Color-coded hourly density.  
- **Day of Week Pattern (Column Chart):** Compares weekday vs weekend trends.  
- **Monthly Trend (Area Chart):** Shows seasonality in accident counts.

**Insights:**
- Rush hours (7–9 AM and 4–7 PM) record the highest accident frequency.  
- Fridays and winter months show noticeably higher incidents.  

---

### 🗺 Page 4 – Regional Comparative Analysis

**Purpose:**  
Enable state-wise and regional comparison using dynamic filters.

**Visuals Used:**
- **State Filter Dropdown (Slicer)**  
- **Top 10 Cities by Accident Count (Table)**  
- **Severity Distribution (Donut Chart)**  
- **Weather Condition Breakdown (Stacked Bar)**  

**Insights:**
- Southern and Eastern states show greater correlation between precipitation and severe accidents.  
- Cities with denser traffic have higher “minor accident” proportions, implying congestion-related risks.  

---

<div align="center">

✅ *The final Power BI dashboard provides end-to-end visibility into how weather conditions influence U.S. road accidents, enabling proactive safety planning and policy improvements.*

</div>

---


