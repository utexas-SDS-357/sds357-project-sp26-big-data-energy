[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MFzEnxem)


# 📊 Team Big Data Energy: San Antonio Traffic Stop Analysis

[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MFzEnxem)

---

## 📖 Project Description
[cite_start]This study evaluates how shifting political climates and federal Executive Orders influence police behavior and traffic stop outcomes over time in San Antonio, Texas[cite: 952, 953]. [cite_start]San Antonio’s unique demographic profile, with a **65% Hispanic population**, serves as a critical marker for examining how ethnic disparities fluctuate across different administrative regimes[cite: 954, 955].

### **Core Research Question**
[cite_start]Do traffic stop outcomes (searches and arrests) differ significantly between the **Obama Era** (EO 13688) and the **Trump Era** (EO 13773), and how do these transitions impact the racial "disparity gap" in high-discretion policing? [cite: 1062, 1066, 1101]

---

## 📂 Overview of Data Folder
[cite_start]This directory contains the essential reference files required to contextualize, filter, and model the raw stop data[cite: 981, 1042].

| File | Type | Project Role |
| :--- | :--- | :--- |
| `policy_data.csv` | Supplemental Dataset | [cite_start]Contains 20 records of federal, state, and local policies used to create **14 binary indicators** for the ITS model [cite: 1062-1068]. |
| `COSABoundary.geojson` | Spatial Boundary | [cite_start]Official San Antonio municipal limits used to refine the dataset from **880,810 to 824,051 observations**[cite: 981, 1112]. |
| `sanantonio.csv` | Raw Data | [cite_start]Original stop-level records sourced from the **Stanford Open Policing Project**[cite: 953]. |

---




Overview of data folder

This directory contains the supplemental datasets required to contextualize and filter the raw San Antonio traffic stop data. These files are used in the Data Integration and Preprocessing stages of the pipeline to align individual stops with specific policy regimes and municipal boundaries.

1. policy_data.csv
   - Supplemental Policy Dataset
   - Manually constructed from federal executive orders, state statutes, and SAPD municipal ordinances
   - Contains 20 distinct policy records including effective dates and jurisdiction levels
   - Used to create 14 binary policy variables
   - Delineates Obama Era and Trump Era for trend analysis
   - Acts as Intervention indicator for interactions terms of regression models

2. COSABoundary.geojson
   - Geographic Boundary File
   - From City of San Antonio Open Data Portal
   - Polygons representing official municipal boundaries of San Antonio
   - Used for spatial filtering during cleaning pipeline process
   - Removes out-of-bounds stop locations and refines initial dataset down to usable municipal sample




Overview of data_wrangling folder

This directory contains the modular Jupyter notebooks used to execute the data science pipeline. The workflow follows a strict sequential order to ensure data integrity, statistical rigor, and reproducibility. These scripts handle initial cleaning, categorical encoding, spatial filtering, and the final integration of policy-level indicators.



Execution Order of Notebooks

1. sanantonio-Sarah01.ipynb - Initial Cleaning
   - Loads raw San Antonio dataset
   - Removes redundant columns to reduce memory overhead
   - Standardizes data formats and performs preliminary record validation
2. initalencoding.ipynb - Feature Engineering
   - Transforms categorical variables into binary numeric indicators
   - Generates Extreme Outcomes by combining search and arrest indicators
3. filtering.ipynb - Spatial Verification
   - Converts stop-level coordinate data into GeoDataFrame
   - Utilizes .geojson file to perform point-in polygon intersection
   - Filters out coordinates falling outside of official City of San Antonio municipal boundaries
   - Refines overall dataset into valid observations
4. final_data_policy.ipynb - Final Integration
   - Merges the filtered stop data with the supplemental policy indicators
   - Performs final datetime truncation and column reordering for time-series analysis
   - Ensures dataset is ready for the Interrupted Time Series model
   

Overview of eda folder

This directory contains the notebooks used for the Exploratory Data Analysis (EDA) and Visual Summaries of the San Antonio traffic stop data. These scripts perform categorical aggregation and temporal analysis to visualize racial disparities and the specific impacts of federal Executive Orders.

1. sanantonio2-Sarah.ipynb
   - Temporal Trend Analysis and Racial Baseline
   - Loads processed final data
   - Reconstructs categorical "Race" labels from one-hot encoded variables for professional plotting
   - Calculates the monthly Extreme Outcome Rate (searches and arrests) for each demographic group
   - Generates the "Extreme Outcome Rates Over Time by Race" line plot, which identifies the long-term trends used to justify our Interrupted Time Series model
  
2. eda.ipynb
   - Comparative Policy Impact Analysis
   - Isolates the Obama Era and Trump Era to examine the specific effects of EO 13688 and EO 13773
     - Obama Era (Impact of EO 13688): Visualizes the change in "militarization" outcomes following the 2015 order
     - Trump Era (Impact of EO 13773): Demonstrates the escalation in extreme outcome rates after the 2017 policy transition
   - Calculates mean outcome rates for Black, Hispanic, and White drivers before and after each policy implementation



Overview of modeling folder

This directory contains the primary inferential model for the project: the Interrupted Time Series analysis. This model is designed to quantify changes in both the "level" and "trend" of extreme policing outcomes, specifically searches and arrests, before and after the January 20, 2017, administrative shift.

its_modeling.ipynb
- Loads final data and aggregates records into monthly Extreme Outcome rates
- Defines an Ordinary Least Squares (OLS) regression model incorporating time (trend), an intervention dummy (January 2017), and a post-intervention trend variable
- Calculates the "Obama Counterfactual", which is a projection of what the policing trends might have looked like had the 2017 policy shift not occurred
- Includes Extreme Outcome Rate comprehensive plot displaying observed data points, the fitted ITS model prediction, and the counterfactual baseline
- Statistically validates whether the shift in 2017 was a significant departure from previous trends
