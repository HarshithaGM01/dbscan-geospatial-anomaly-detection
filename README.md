# Density-Based Anomaly Detection on Geospatial Data using DBSCAN

## Overview

This project applies **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** to real-world geospatial data to identify **dense urban hotspots** and **anomalous locations**.
Using Uber pickup locations in New York City, the model detects high-density pickup regions while explicitly labeling sparse, unusual pickup locations as anomalies.



## Motivation

Geospatial data often exhibits:

* uneven density
* irregular cluster shapes
* natural noise and outliers

Traditional clustering methods like K-Means struggle in such settings.
DBSCAN is well-suited because it:

* does **not** require the number of clusters in advance
* identifies **arbitrarily shaped clusters**
* explicitly labels **noise points** (anomalies)



## Dataset

* **Uber pickup locations (NYC)**
* Source: FiveThirtyEight Uber TLC FOIL dataset
* Features used:

  * `Lat` (latitude)
  * `Lon` (longitude)

Only pickup coordinates were used; no labels or heavy preprocessing were required.



## Methodology

1. Loaded and cleaned latitude–longitude data
2. Sampled data for computational efficiency
3. Applied **DBSCAN** with:

   * haversine distance (for spherical Earth geometry)
   * distance threshold defined in kilometers
4. Interpreted:

   * clusters → dense pickup hotspots
   * noise (`-1`) → anomalous / rare pickup locations
5. Visualized clusters and anomalies on a 2D map


## Evaluation

* **Silhouette Score** was computed **excluding noise points**
* Result:

  * DBSCAN silhouette score ≈ **0.25**
* A brief comparison with **K-Means** showed:

  * K-Means achieved a higher silhouette score
  * However, it failed to detect anomalies and forced spherical clusters

This highlights that **evaluation metrics can favor certain algorithms** and must be interpreted in the context of the problem.



## Key Insight

Although K-Means produced a higher silhouette score, **DBSCAN was more appropriate for geospatial anomaly detection** because it models density directly and explicitly identifies noise.
This project demonstrates that **metric alignment matters as much as metric value**.

---

## Visualization

* Dense regions correspond to major NYC pickup hotspots
* Red points represent anomalous or rare pickup locations
* Visualization clearly shows DBSCAN’s ability to separate structure from noise



## Technologies Used

* Python
* pandas
* numpy
* scikit-learn
* matplotlib


## Takeaway

This project shows how **density-based clustering** can be effectively applied to real-world geospatial data and why **choosing the right model and evaluation strategy** matters more than optimizing a single score.

