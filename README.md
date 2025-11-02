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

```mermaid
%% Works on GitHub
graph LR
    A[Kaggle Dataset] --> B[Data Cleaning & Filtering (Excel Power Query)]
    B --> C[Upload Cleaned Files to SharePoint or OneDrive]
    C --> D[Generate Shareable Link]
    D --> E[Power BI Desktop - Get Data from Web URL]
    E --> F[Dynamic Dashboard with Auto Refresh]

    %% Simple color scheme
    classDef source fill:#f9f871,stroke:#d6b600,stroke-width:2px,color:#000;
    classDef process fill:#a5d6a7,stroke:#2e7d32,stroke-width:2px,color:#000;
    classDef share fill:#90caf9,stroke:#1565c0,stroke-width:2px,color:#000;
    classDef end fill:#f48fb1,stroke:#ad1457,stroke-width:2px,color:#000;

    class A source;
    class B,C process;
    class D,E share;
    class F end;

