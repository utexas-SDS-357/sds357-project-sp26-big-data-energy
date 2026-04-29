## Overview
This directory contains the modular Jupyter notebooks used to execute the data science pipeline. The workflow follows a strict sequential order to ensure data integrity, statistical rigor, and reproducibility. These scripts handle initial cleaning, categorical encoding, spatial filtering, and the final integration of policy-level indicators.

## Pipeline Execution Order
The following execution order must be maintained to successfully generate the finalized analytical dataset.

| Step | Notebook | Primary Action |
| :--- | :--- | :--- |
| 1 | **sanantonio-Sarah01.ipynb** | Initial cleaning and column removal |
| 2 | **initalencoding.ipynb** | Feature engineering and categorical encoding |
| 3 | **filtering.ipynb** | Spatial verification and municipal filtering |
| 4 | **final_data_policy.ipynb** | Final integration and policy merging |

## Notebook Descriptions

| Notebook | Key Actions | Primary Output |
| :--- | :--- | :--- |
| **sanantonio-Sarah01.ipynb** | Loads the raw sanantonio.csv file, removes redundant vehicle-related columns, and standardizes data formats. | new_san_antonio.csv |
| **initalencoding.ipynb** | Transforms categorical variables into binary numeric indicators and generates the extreme_cases feature. | san_antonio_cleaned.csv |
| **filtering.ipynb** | Performs a point-in-polygon intersection to remove 56,759 records falling outside municipal boundaries. | sa_policy_filtered.csv |
| **final_data_policy.ipynb** | Merges filtered stop data with supplemental policy indicators and performs final datetime truncation. | teamb_final_data.csv |

## Dependencies
The following libraries are required to execute the notebooks within this directory.

| Library | Purpose |
| :--- | :--- |
| **pandas** | Core data manipulation and CSV ingestion |
| **geopandas** | Geographic data handling and spatial filtering |
| **shapely** | Geometric operations for coordinate verification |
