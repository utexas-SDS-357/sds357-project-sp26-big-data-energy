[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MFzEnxem)


# Team Big Data Energy: San Antonio Traffic Stop Analysis

---

## Project Description
This study evaluates how shifting political climates and federal Executive Orders influence police behavior and traffic stop outcomes over time in San Antonio, Texas. San Antonio’s unique demographic profile, with a **65% Hispanic population**, serves as a critical marker for examining how ethnic disparities fluctuate across different administrative regimes.

### **Core Research Question**
Do traffic stop outcomes (searches and arrests) differ significantly between the **Obama Era** (EO 13688) and the **Trump Era** (EO 13773), and how do these transitions impact the racial "disparity gap" in high-discretion policing?

---

## **1. Data Folder**
This directory contains the essential reference files required to contextualize, filter, and model the raw stop data.

| File | Type | Project Role |
| :--- | :--- | :--- |
| `policy_data.csv` | Supplemental Dataset | Contains 20 records of federal, state, and local policies used to create **14 binary indicators** for the ITS model. |
| `COSABoundary.geojson` | Spatial Boundary | Official San Antonio municipal limits used to refine the dataset from **880,810 to 824,051 observations**. |
| `sanantonio.csv` | Raw Data | Original stop-level records sourced from the **Stanford Open Policing Project**. |

---


### **2. Data Wrangling Folder**
This directory executes the core data science pipeline in a strict sequential order to ensure data integrity and statistical rigor.

| Execution Order | Notebook | Key Operations |
| :--- | :--- | :--- |
| **Step 1** | `sanantonio-Sarah01.ipynb` | **Initial Cleaning**: Loads raw San Antonio dataset; removes redundant columns; standardizes data formats; performs preliminary record validation. |
| **Step 2** | `initalencoding.ipynb` | **Feature Engineering**: Transforms categorical variables into binary numeric indicators; generates "Extreme Outcomes" by combining search and arrest indicators. |
| **Step 3** | `filtering.ipynb` | **Spatial Verification**: Converts stop-level coordinate data into a GeoDataFrame; utilizes `.geojson` to filter coordinates falling outside official City of San Antonio boundaries. |
| **Step 4** | `final_data_policy.ipynb` | **Final Integration**: Merges filtered stop data with supplemental policy indicators; performs final datetime truncation and column reordering for time-series analysis. |

### **3. EDA Folder**
This directory handles categorical aggregation and temporal analysis to visualize racial disparities and policy impacts.

| Notebook | Project Role | Analysis Details |
| :--- | :--- | :--- |
| `sanantonio2-Sarah.ipynb` | **Temporal Trend Analysis** | Loads processed data; reconstructs "Race" labels from one-hot variables; calculates monthly Extreme Outcome Rates; generates line plots used to justify the ITS model. |
| `eda.ipynb` | **Policy Impact Analysis** | Isolates Obama/Trump eras to examine EO 13688 (militarization) and EO 13773 (2017 transition); calculates mean outcome rates for Black, Hispanic, and White drivers. |

### **4. Modeling Folder**
This directory houses the primary inferential model designed to quantify changes in policing trends.

| Notebook | Model Type | Functional Components |
| :--- | :--- | :--- |
| `its_modeling.ipynb` | **Interrupted Time Series (ITS)** | Defines OLS regression (trend/intervention); calculates the **Obama Counterfactual**; statistically validates the 2017 shift; generates comprehensive Observed vs. Predicted plots. |

---

## Usage Instructions
To reproduce the analysis from raw data to final inference, follow the sequence below.

| Phase | Step | Notebook | Description |
| :--- | :--- | :--- | :--- |
| **Wrangling** | 1 | `sanantonio-Sarah01.ipynb` | Run first to ingest and clean the raw Stanford Open Policing Project data. |
| | 2 | `initalencoding.ipynb` | Run to encode demographic features and define the "Extreme Outcomes" target. |
| | 3 | `filtering.ipynb` | Apply the spatial filter to refine the dataset to **824,051 valid observations**. |
| | 4 | `final_data_policy.ipynb` | Execute to produce the final `teamb_final_data.csv` used for all remaining analysis. |
| **Exploration** | 5 | `eda.ipynb` / `sanantonio2-Sarah.ipynb` | Generate visual summaries of racial disparities and policy-specific impact charts. |
| **Modeling** | 6 | `its_modeling.ipynb` | Run final regression to produce the ITS model predictions and the Obama Counterfactual projection. |

---

## Dependencies
This project requires a Python 3.8+ environment with the following libraries.

| Library | Purpose |
| :--- | :--- |
| `pandas` | Primary data manipulation, CSV ingestion, and categorical encoding. |
| `geopandas` | Geographic data handling and point-in-polygon spatial filtering. |
| `statsmodels` | Statistical modeling, OLS regression, and Interrupted Time Series execution. |
| `seaborn` | Advanced categorical visualization and policy comparison bar charts. |
| `matplotlib` | Standard time-series plotting and comprehensive ITS graph generation. |
| `shapely` | Geometric operations required for spatial verification. |
| `numpy` | Numerical operations and matrix handling for modeling. |

---
