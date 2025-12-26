# Wildfire Susceptibility Dataset

This repository contains a dataset used for training a **Wildfire Susceptibility Assessment Model**. The dataset is collected from **Google Earth Engine (GEE)** and uses **MODIS** data for labeling. It integrates multiple environmental factors to assess the likelihood of wildfire occurrences in a given region.

## Dataset Overview

The dataset is designed for assessing wildfire susceptibility by combining environmental and anthropogenic factors. It is used to build machine learning models that predict wildfire-prone areas, helping in risk management and early warning systems. 

### Key Features of the Dataset:

- **Data Source**: Data was collected using **Google Earth Engine (GEE)**, leveraging a variety of environmental data sources.
- **Labeling Method**: Fire occurrences were labeled using **MODIS (Moderate Resolution Imaging Spectroradiometer)** thermal anomaly data (MOD14A1).
- **Data Type**: This dataset includes both **natural** (climate, vegetation, and topography) and **anthropogenic** (population density and fire sources) factors that influence wildfire behavior.

### Dataset Attributes:
| Attribute            | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **NDVI**              | Normalized Difference Vegetation Index (NDVI) — vegetation conditions       |
| **NDII7**             | Normalized Difference Infrared Index 7 — moisture content                   |
| **LST**               | Land Surface Temperature — thermal conditions                               |
| **Precipitation**     | Daily total precipitation in mm                                            |
| **Soil Moisture**     | Monthly average soil moisture at 0-10 cm depth                             |
| **Elevation**         | Elevation (meters above sea level)                                          |
| **Wind Speed**        | Daily maximum wind speed (m/s) at 10 meters                                |
| **Wind Direction**    | Wind direction (degrees) at 10 meters                                      |
| **Population Density**| Gridded population density                                                 |
| **FireMask**          | Binary fire occurrence mask from MODIS (MOD14A1)                            |
| **Day of the Year**   | Day of the year when the fire occurred, capturing seasonal effects          |

### Data Preprocessing

The dataset was preprocessed as follows:
1. **Data Aggregation**: Data from various sources was aggregated into 1 km² resolution grids.
2. **Fire Labeling**: Fire occurrence was labeled using the **MODIS Fire Mask** (MOD14A1). Pixels with values 7, 8, or 9 were considered fire-positive, while other pixels were labeled as fire-negative.
3. **Sampling**: Positive samples were chosen within a 5 km buffer zone around historical fire points, and negative samples were randomly selected outside the buffer to reduce spatial autocorrelation.
4. **Missing Data**: Missing values were handled using the **Isolation Forest** algorithm to improve data quality.

## Purpose of the Dataset

This dataset is designed for use in developing models that assess wildfire susceptibility. The goal is to predict areas that are at higher risk of experiencing wildfires, helping to support wildfire prevention efforts and improve disaster management.
