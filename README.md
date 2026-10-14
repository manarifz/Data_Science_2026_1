# 🌾 Geospatial Estimation of Paddy Field Area via Binary Classification and Economic Simulation

> **A data-driven pipeline to map paddy fields and translate physical land measurements into real-world economic impacts for smallholder farmers.**

This repository contains a complete data-driven pipeline designed to map paddy fields in the Pendang district of Kedah, Malaysia, and translate those physical land measurements into real-world economic impacts for local smallholder farmers. Rice serves as the cornerstone of Malaysia's national food security, and Kedah known as the *"Rice Bowl of Malaysia"* is the nation's most critical domestic producer.

---

## 🎯 Project Objectives

- **🛰️ Spatial Delineation:** Accurately estimate the total area of cultivated paddy fields (in hectares) using Earth Observation satellite data and advanced machine learning algorithms.
- **💰 Economic Simulation:** Quantify farm-level economic viability by simulating land allocation, yield production, gross income, government input subsidies, production costs, net profit, and obligatory religious taxes (zakat).

---

## ⚙️ Methodology Overview

The project workflow is structured into six core stages:

1. **📡 Raw Satellite Image Data Retrieval**  
   Retrieves 18 satellite image variables for the Pendang area spanning the entirety of 2023 using the Google Earth Engine platform. The automated pipeline filters Sentinel-2 imagery for less than 7.03% cloud cover, applies advanced cloud masking, and utilizes a temporal median reducer to flatten overlapping satellite passes into a single, stable composite. This processed composite is exported as a 100-meter resolution GeoTIFF (EPSG:4326) to perfectly format the spatial matrices for machine learning.

2. **🛠️ Feature Engineering**  
   Extracts spatial data from 18 multi-spectral, radar, and nighttime light satellite variables, utilizing K-Nearest Neighbors (KNN) imputation to intelligently fill missing data caused by cloud cover or sensor errors.

3. **🧹 Data Pre-Processing**  
   Standardizes geographic coordinate headers and removes redundant, un-processed raw variables to ensure spatial uniqueness and prevent data leakage.

4. **🔗 Data Integration**  
   Projects datasets into a shared Cartesian coordinate system (EPSG:3375) and pairs ground-truth observations with their closest satellite pixels using a strict 50-meter maximum distance threshold.

5. **🧠 Model Development**  
   Trains, optimizes, and evaluates five algorithms—**Random Forest, Support Vector Machine (SVM), XGBoost, Multilayer Perceptron (MLP), and a 1D Convolutional Neural Network (CNN)**—using rigorous 5-Fold Spatial Block Cross-Validation.

6. **📈 Yield & Economic Simulation**  
   Translates spatial area predictions into financial metrics to simulate the livelihoods of 10,000 local smallholder farmers. The simulation calculates land allocation and uses regional benchmarks (4.7 tonnes of yield per hectare) to formulate gross yield income, factoring in the base market price, the Skim Subsidi Harga Padi (SSHP), input subsidies, production costs, and obligatory religious taxes (zakat).

---

## 📊 Key Findings

| Metric | Insight |
| :--- | :--- |
| 🏆 **Model Performance** | **Random Forest** achieved the highest predictive fidelity on the hold-out test set, recording an Overall Accuracy of `93.10%`, a Sensitivity (Recall) of `96.04%`, and an F1-Score of `93.27%`. |
| 🗺️ **Area Estimation** | The Random Forest model estimated a total paddy extent of **19,252.00 hectares**, aligning closely (`+4.28%` variance) with the official district-wide inventory from Pihak Berkuasa Tempatan (PBT) Kedah. |
| 🔍 **Feature Importance** | Sentinel-1 Synthetic Aperture Radar cross-polarized backscatter (**SAR_VH**) emerged as the single most decisive predictor for tropical paddy delineation across all models. |
| ⚖️ **Economic Impact** | The simulation highlights the absolute indispensability of federal interventions; **government price support and input subsidies account for approximately 65.56% of a farmer's net take-home profit**, safeguarding rural livelihoods. |

---
