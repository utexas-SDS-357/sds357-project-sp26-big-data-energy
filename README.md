[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/MFzEnxem)





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
   
