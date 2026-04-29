## Overview
This directory contains the supplemental datasets required to contextualize, filter, and model the raw traffic stop data from the Stanford Open Policing Project. These files provide the geographic and legislative framework used to refine the dataset from 880,810 observations to the final sample of 824,051 valid records.

---

## File Descriptions

### 1. `policy_data.csv`
* **Role**: Legislative Framework for Interrupted Time Series (ITS) Modeling.
* **Contents**: A manually curated timeline of 20 federal, state, and local policies.
* **Key Attributes**:
    * `policy_name`: The official title of the directive (e.g., EO 13688, Texas SB 4).
    * `jurisdiction_level`: Categorization into Federal, State, or Local.
    * `effective_date`: The start date used to trigger the binary "active" indicator.
    * `policy_description`: Summary of the policy’s intent (e.g., limits on militarized equipment acquisition).
* **Project Function**: In the `final_data_policy.ipynb` notebook, this file is used to generate 14 binary indicator variables. These indicators allow our models to quantify "level shifts" and "slope changes" in policing outcomes based on the active administrative regime.

### 2. `COSABoundary.geojson`
* **Role**: Spatial Integrity and Geographic Filtering.
* **Source**: [City of San Antonio (COSA) Open Data Portal](https://data.sanantonio.gov/).
* **Contents**: High-resolution MultiPolygon coordinates representing the official municipal boundaries of San Antonio.
* **Project Function**: During the preprocessing phase (`filtering.ipynb`), we convert stop-level coordinate data into a GeoDataFrame. We perform a point-in-polygon intersection using this GeoJSON to remove 56,759 out-of-bounds records, ensuring the analysis strictly represents municipal SAPD enforcement.

---

## Data Dictionary (policy_data.csv)

| Column | Description | Type |
| :--- | :--- | :--- |
| `policy_name` | The name of the executive order or statute. | String |
| `jurisdiction_level` | The level of government enacting the policy. | String |
| `effective_date` | The date the policy was officially implemented. | Date (M/D/YYYY) |
| `end_date` | The date the policy was rescinded (if applicable). | Date (M/D/YYYY) |
| `policy_description` | Summary of the policy's impact on policing strategy. | String |
| `source_url` | Direct link to the legislative or executive document. | URL |

---

## Usage in the Pipeline

These reference files are called by the following notebooks in the sequential pipeline:

1.  **`filtering.ipynb`**: Loads `COSABoundary.geojson` to execute spatial filtering and verify geographic jurisdiction.
2.  **`final_data_policy.ipynb`**: Loads `policy_data.csv` to merge legislative timestamps with traffic stop records, creating the finalized dataset (`teamb_final_data.csv`) used for inferential modeling.

---

## Note on Raw Data
Due to file size limitations and licensing agreements, the primary raw stop-level dataset (`sanantonio.csv`) from the Stanford Open Policing Project is not hosted in this directory. It must be downloaded separately and placed in the project root as described in the main repository instructions.


This folder stores the data that has been used.

The data is not included due to file size.

To run this project:
Download the raw dataset from (https://drive.google.com/file/d/1OOtmfKbKMdL0MT3K2EzVS4sQiFX_ngkY/view?usp=sharing)

(https://drive.google.com/file/d/1azd3j0kRz1m-w_ktVIvk9p3RE5KjmBDh/view?usp=sharing)

(https://drive.google.com/file/d/1-HU4DmndKhlMdB9RhrpM0o6HKWA00p0V/view?usp=sharing)

(https://drive.google.com/file/d/1SJUAYjuZEyBeNG9hgiHEa79QCoca6zCq/view?usp=sharing)

Final Dataset:
(https://drive.google.com/file/d/1gakJlQINviXV8w_RQL5waRCAm-DyhxKj/view?usp=sharing)





