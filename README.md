# Optimising NYC Taxi Operations 🚖📊

## 📌 Project Overview
This project involves a comprehensive analysis of the **2023 New York City Yellow Taxi trip data**. As an analyst for an upcoming taxi operator, the goal is to uncover data-driven insights to optimise fleet operations, maximise revenue, and enhance the passenger experience.

The analysis follows a structured approach ranging from data cleaning and sampling to exploratory data analysis (EDA) and strategic recommendations.

## 🎯 Objectives
* **Service Efficiency:** Match supply with demand by identifying peak hours and popular locations.
* **Revenue Maximisation:** Propose pricing strategies based on trip patterns and fare analysis.
* **Passenger Experience:** Understand customer behavior regarding tipping, payment methods, and ride preferences.

## 🛠️ Technologies Used
* **Language:** Python 🐍
* **Libraries:**
    * `pandas` & `numpy` (Data Manipulation)
    * `matplotlib` & `seaborn` (Data Visualisation)
* **Format:** Jupyter Notebook (`.ipynb`)

## 📂 Dataset
The dataset used consists of **2023 Yellow Taxi Trip Records** provided by the NYC Taxi and Limousine Commission (TLC).
* **Source Format:** Parquet files (monthly).
* **Sampling Strategy:** Due to the large volume of data, a **5% random sample** was extracted from each month to create a representative dataset of approximately **1.9 million records**.

## ⚙️ Methodology

### 1. Data Preparation & Loading
* Loaded monthly parquet files.
* Implemented a sampling method extracting 5% of data per month to ensure computational feasibility while maintaining statistical significance.

### 2. Data Cleaning
* **Handling Missing Values:**
    * `passenger_count`: Nulls replaced with 1 (assumption: at least one passenger per trip)[cite: 180].
    * `RatecodeID`: Nulls replaced with Standard Rate (1)[cite: 183].
    * `congestion_surcharge`: Imputed using the median value[cite: 187].
* **Feature Engineering:** Combined duplicate airport fee columns into a single consolidated column[cite: 170, 171].
* **Outlier Removal:**
    * Removed invalid trips with `payment_type = 0`[cite: 193].
    * Filtered unrealistic trip distances (e.g., > 250 miles or 0 miles with nonzero fare)[cite: 198, 199].

### 3. Exploratory Data Analysis (EDA)
* **Temporal Trends:** Analyzed pickup demand by hour, day of the week, and month.
    * *Insight:* Demand peaks in the early evening and mid-week (Wed-Thu), with a drop on Sundays[cite: 27, 28].
* **Revenue Analysis:** Examined monthly revenue trends and fare distributions.
* **Geospatial Patterns:** Investigated pickup/drop-off zones (using `PULocationID` and `DOLocationID`).

## 💡 Key Recommendations
Based on the analysis, the following strategies are proposed to optimise operations:

1.  **Dynamic Fare Management:** Implement real-time fare adjustments based on demand spikes and traffic patterns.
2.  **Tiered & Zoned Pricing:** Introduce fixed or tiered pricing for long-distance trips to reflect complexity.
3.  **Shared Ride Incentives:** Promote carpooling to improve fleet efficiency and reduce passenger costs.
4.  **Smarter Surcharges:** Apply peak surcharges transparently to maintain customer trust.

## 🚀 How to Run
1.  Clone this repository.
2.  Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn pyarrow
    ```
3.  Open the Jupyter Notebook:
    ```bash
    jupyter notebook Python-Jupyter-Notebook.ipynb
    ```

## 📈 Future Work
* Integrate weather data to analyse its impact on taxi demand.
* Develop a machine learning model to predict fare amounts or trip duration.
* Perform A/B testing on pricing strategies.

---
*Disclaimer: This analysis is based on a sampled dataset from NYC TLC 2023 records.*
