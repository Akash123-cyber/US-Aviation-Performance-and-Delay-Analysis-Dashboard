# US-Aviation-Performance-and-Delay-Analysis-Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=power-bi)
![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python)
![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)

**US-Aviation-Performance-and-Delay-Analysis-Dashboard** is a fully dynamic, 5-page Power BI executive dashboard designed to analyze US airline flight delays, cancellations, and operational efficiency. Built using 2023 flight data from the Bureau of Transportation Statistics (BTS), this project demonstrates end-to-end data engineering—from raw CSV processing with Python to advanced DAX modeling and AI-driven insights in Power BI.

---

## 📊 Dashboard Overview

The report is divided into a strategic landing page plus 5 analytical views, each targeting a specific stakeholder group:

| Page | Name | Target Audience | Key Insights |
| :--- | :--- | :--- | :--- |
| **0** | **Home / Landing** | All Users | Navigation hub with project context and links to external resources (GitHub/LinkedIn). |
| **1** | **Executive Control Tower** | C-Suite / VPs | High-level KPIs (OTP%, Cancellation Rate), Monthly Trends, and Financial Impact ($). |
| **2** | **Geo-Spatial Analysis** | Ops Managers | Interactive flow maps of routes, congestion heatmaps, and long-haul performance. |
| **3** | **Carrier Benchmarking** | Strategy Team | Head-to-head comparison of airlines (e.g., Delta vs. United) on reliability and speed. |
| **4** | **Root Cause Analysis** | Engineers | AI Decomposition Tree breaking down delays by Weather, NAS, Carrier, and Security factors. |
| **5** | **Airport Deep Dive** | Station Managers | Granular hourly congestion analysis and taxi-in/out efficiency for specific hubs. |

---

## 🛠️ Tech Stack & Tools

* **Data Visualization:** Microsoft Power BI Desktop
* **Data Processing:** Python (Pandas)
* **Data Source:** US Bureau of Transportation Statistics (BTS)
* **Key Techniques:**
    * Advanced DAX (Calculated Measures, Time Intelligence)
    * AI Visuals (Decomposition Tree, Key Influencers, Smart Narratives)
    * Python Scripting for ETL (Downsampling & Merging)
    * Figma/PowerPoint for UI/UX Design (Glassmorphism Layouts)

---

## 📂 Repository Structure

```text
├── data/
│   ├── scripts/
│   │   ├── downsample_csv.py       # Reduces dataset to 10% random sample
│   │   ├── combine_csvs.py         # Merges monthly files into a master dataset
│   │   └── filter_columns.py       # Drops unused columns to optimize performance
│   └── (Data files not included due to size limits)
├── designs/
│   ├── backgrounds/                # UI Background images/templates
│   
├── US-Aviation-Performance-and-Delay-Analysis-Dashboard.pbix       # The main Power BI file
└── README.md
```

---

## 🚀 How to Run This Project

### 1. Data Setup (Python ETL)
Since the raw BTS data is massive (~6M rows), use the provided Python scripts to prepare a lightweight version for testing.

**Prerequisites:**
```bash
pip install pandas
```

**Steps:**
1.  Download raw data from [BTS TranStats](https://www.transtats.bts.gov/DL_SelectFields.asp?gnoyr_VQ=FGJ&QO_fu146_ezua=XP) (or use `data/sample_data.csv` if provided).
2.  Run the downsampler to reduce file size (optional):
    ```bash
    python data/scripts/downsample_csv.py
    ```
3.  Clean unnecessary columns to speed up Power BI:
    ```bash
    python data/scripts/filter_columns.py
    ```

### 2. Launch the Dashboard
1.  Install **Microsoft Power BI Desktop**.
2.  Open `SkyMonitor_Dashboard.pbix`.
3.  If prompted, change the Data Source setting to point to your local `.csv` file location (`Home > Transform Data > Data Source Settings`).

---

## 📈 Key Features & DAX Logic

* **On-Time Performance (OTP):** Calculated dynamically based on 15-minute standard.
    ```dax
    OTP % = DIVIDE(
        CALCULATE(COUNTROWS('Flights'), 'Flights'[ArrDelay] < 15),
        COUNTROWS('Flights'),
        0
    )
    ```
* **Pareto Analysis:** Identifies the top 20% of airports causing 80% of delays using cumulative totals.
* **Dynamic Scenarios:** "What-if" parameters to estimate cost savings by reducing taxi times.

---

## 📸 Screenshots

*(Place your dashboard screenshots here)*

| Executive Overview | Geo-Spatial Map |
| :---: | :---: |
| ![Page 1](path/to/image1.png) | ![Page 2](path/to/image2.png) |

---

## 👤 Author

**[Akash Kumar Malik]**
* Data Science Student Lovely Professional University
---

**Disclaimer:** This project uses public data from the US Department of Transportation. It is for educational and analytical demonstration purposes only.
