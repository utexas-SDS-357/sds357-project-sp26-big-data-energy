This folder stores the data that has been used.

The data is not included due to file size.
To run this project:
Download the raw dataset from (https://drive.google.com/file/d/1OOtmfKbKMdL0MT3K2EzVS4sQiFX_ngkY/view?usp=sharing)

Processed Data
(https://drive.google.com/file/d/1azd3j0kRz1m-w_ktVIvk9p3RE5KjmBDh/view?usp=sharing)

(https://drive.google.com/file/d/1-HU4DmndKhlMdB9RhrpM0o6HKWA00p0V/view?usp=sharing)

(https://drive.google.com/file/d/1SJUAYjuZEyBeNG9hgiHEa79QCoca6zCq/view?usp=sharing)

(https://drive.google.com/file/d/1gakJlQINviXV8w_RQL5waRCAm-DyhxKj/view?usp=sharing)


Overview

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


