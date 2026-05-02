## Overview
This directory contains the primary inferential model for the project: the Interrupted Time Series analysis. This model is designed to quantify changes in both the level and trend of extreme policing outcomes, specifically searches and arrests, before and after the January 20, 2017, administrative shift.

## Notebook Descriptions

| Notebook | Key Actions | Primary Output |
| :--- | :--- | :--- |
| **its_modeling.ipynb** | Implementation of OLS regression to compare observed data against the Obama counterfactual baseline. | its_graph.png |

## Key Modeling Components
* **Intervention Point**: The model utilizes January 20, 2017, as the primary intervention point to evaluate the impact of the federal executive transition.
* **Obama Counterfactual**: A statistical projection used to estimate what policing trends would have looked like had the pre-2017 policy environment persisted.
* **Level and Trend Shifts**: Quantification of immediate changes in outcome rates versus long-term alterations in the trajectory of policing behavior.
* **Aggregated Time Series**: Monthly aggregation of the validated stop records to stabilize variance and ensure model reliability for longitudinal analysis.

## Dependencies

| Library | Purpose |
| :--- | :--- |
| **statsmodels** | Implementation of Ordinary Least Squares regression and statistical validation |
| **pandas** | Time-series data manipulation and monthly temporal aggregation |
| **matplotlib** | Generation of high-resolution Interrupted Time Series visualizations |
| **numpy** | Numerical operations and matrix handling for counterfactual calculations |
