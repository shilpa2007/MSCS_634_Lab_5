# MSCS_634_Lab_5 — Clustering Techniques Using DBSCAN and Hierarchical Clustering

**Name:** Shilpa Mesineni  
**Course:** MSCS 634 – Advanced Data Mining and Big Data Analytics  
**Lab:** Lab 5 – Clustering Techniques Using DBSCAN and Hierarchical Clustering

---

## Purpose

This lab explores unsupervised clustering techniques applied to the Wine dataset from `sklearn.datasets`. The goal is to understand how Hierarchical (Agglomerative) Clustering and DBSCAN work, how their parameters influence cluster formation, and how to evaluate and compare clustering quality using Silhouette, Homogeneity, and Completeness scores.

---

## Dataset

The **Wine dataset** contains 178 samples and 13 numerical features (alcohol content, malic acid, ash, etc.) representing chemical measurements of wines from three different cultivars. There are no missing values and features were standardized before clustering using `StandardScaler`.

---

## Key Insights

**Hierarchical Clustering:**
- The dendrogram using Ward linkage clearly suggested 3 natural clusters, aligning with the 3 known wine cultivars.
- At n_clusters=3, the model achieved the best balance: Silhouette ≈ 0.28, Homogeneity ≈ 0.87, Completeness ≈ 0.86.
- Performance degraded as n_clusters increased beyond 3, confirming the natural three-way structure of the dataset.

**DBSCAN:**
- Results were highly sensitive to eps and min_samples. A k-distance plot (elbow method) was used to guide eps selection toward the 2.5–3.0 range.
- Best configuration (eps=2.5, min_samples=3) produced clusters comparable in homogeneity to Hierarchical, but classified some points as noise.
- DBSCAN's noise detection capability is an advantage for real-world noisy datasets, but less relevant here since the Wine dataset is relatively clean.

**Overall Winner:** Hierarchical Clustering with n=3 performed more consistently on this dataset. The compact, well-separated cluster structure of the Wine data aligns better with hierarchical assumptions than DBSCAN's density-based approach.

---

## Challenges and Decisions

- **PCA for visualization:** Since the Wine dataset has 13 features, 2-component PCA was applied solely for scatter plot visualization. All clustering was performed on the full 13-dimensional standardized feature space.
- **eps selection for DBSCAN:** A k-distance graph (5th nearest neighbor distances) was plotted to identify the elbow point rather than guessing eps blindly.
- **Noise handling in metrics:** Silhouette and other metrics for DBSCAN were computed only on non-noise points to avoid misleading scores from noise-labeled samples.

---

## Files

| File | Description |
|---|---|
| `MSCS_634_Lab_5.ipynb` | Main Jupyter Notebook with all steps, code, visualizations, and analysis |
| `README.md` | This file |
