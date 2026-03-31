[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MFzEnxem)



📖 1. Project Description
This study evaluates how shifting political climates and federal Executive Orders influence police behavior and traffic stop outcomes over time. By focusing on San Antonio—a city where approximately 65% of the population identifies as Hispanic or Latino—we examine ethnic disparities through the lens of changing administrative regimes.

Core Research Question
Do traffic stop outcomes (searches and arrests) differ significantly between the Obama Era (defined by EO 13688) and the Trump Era (defined by EO 13773), and how do these transitions impact the racial "disparity gap"?

.
├── data/
│   ├── COSABoundary.geojson      # Municipal boundary for spatial filtering
│   └── policy_data.csv           # Supplemental federal/state policy timeline
├── data_wrangling/
│   ├── sanantonio-Sarah01.ipynb  # Initial cleaning and column removal
│   ├── initalencoding.ipynb      # Categorical encoding & target creation
│   ├── filtering.ipynb           # Spatial point-in-polygon filtering
│   └── final_data_policy.ipynb   # Merging stop data with policy indicators
├── eda/
│   ├── sanantonio2-Sarah.ipynb   # Temporal trend analysis by race
│   └── eda2.ipynb                # Comparative bar charts for EOs
├── modeling/
│   └── its_modeling.ipynb        # Interrupted Time Series (ITS) regression
└── README.md                     # Comprehensive Project Overview

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
