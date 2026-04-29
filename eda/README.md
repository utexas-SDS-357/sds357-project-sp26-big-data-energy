## Overview
This directory contains the notebooks used for the Exploratory Data Analysis and visual summaries of the San Antonio traffic stop data. These scripts perform categorical aggregation and temporal analysis to visualize racial disparities and the specific impacts of federal executive orders.

## Notebook Descriptions

| Notebook | Key Actions | Primary Output |
| :--- | :--- | :--- |
| **sanantonio2-Sarah.ipynb** | Performs temporal trend analysis by calculating monthly extreme outcome rates for each demographic group. | Racial baseline plots |
| **eda2-Copy1.ipynb** | Conducts comparative policy impact analysis by isolating the Obama and Trump eras to examine the effects of federal executive orders. | graph.png |
| **finalEDA.ipynb** | Applies smoothing techniques and professional color palettes to temporal outcome plots for high-resolution reporting. | demo.png |

## Key Analytical Tasks
* **Temporal Trend Analysis**: Identifying shifts in enforcement patterns and outcome rates across the 2014 to 2019 study period.
* **Demographic Benchmarking**: Aggregating data to calculate mean outcome rates for Black, Hispanic, and White drivers to establish baseline disparities.
* **Policy Impact Visualization**: Creating comparative visualizations to evaluate how administrative transitions correspond to changes in policing behavior.

## Dependencies

| Library | Purpose |
| :--- | :--- |
| **pandas** | Data manipulation and monthly temporal aggregation |
| **matplotlib** | Time-series plotting and high-resolution figure customization |
| **seaborn** | Statistical data visualization and categorical bar charts |
