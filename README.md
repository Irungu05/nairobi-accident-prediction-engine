# 🚗 Two-Step Hierarchical ML Framework for Urban Traffic Risk & Severity Prediction

A two-step hierarchical machine learning framework designed to predict urban traffic accident occurrence, severity, and spatial risk in Nairobi, Kenya. 

This project addresses extreme spatial-temporal data sparsity and class imbalance by decoupling spatial occurrence screening (Step 1 CNN) from multi-class severity classification (Step 2 ML Engine).

---

## 📌 Project Architecture

1. **Step 1: Spatial Grid Screening (Gatekeeper)**
   * A **Convolutional Neural Network (CNN)** screens a 100m x 100m spatial grid matrix of Nairobi to filter out >90% of zero-accident spatial noise.
2. **Step 2: Multi-Class Severity Engine**
   * Active hazard grid cells are passed to multi-class models (**Random Forest**, **Deep Neural Network**, and **Naïve Bayes**) to classify severity levels.
3. **Accident Risk Index (ARI)**
   * Normalizes human injury severity by traffic volume exposure ($V$) to isolate true structural hazards from high-density traffic corridors:
   
   $$\text{ARI} = \frac{1.0 \times \text{DEATH} + 0.7 \times \text{SERI} + 0.3 \times \text{SLTWD}}{V}$$


---

## 🛠️ Data Sources

* **Crash Telemetry:** World Bank Nairobi Crowdsourced Crash Dataset (31,064 historical records, 2012–2023).
* **Spatial & Road Infrastructure:** OpenStreetMap (OSM) via `OSMnx` and `GeoPandas`[cite: 1].
* **Meteorological Streams:** ERA5 atmospheric reanalysis (hourly rainfall, surface wetness, visibility)[cite: 1].
* **Traffic Flow:** Uber Movement velocity archives and regional traffic estimates[cite: 1].
