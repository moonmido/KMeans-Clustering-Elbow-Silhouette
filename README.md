# KMeans Clustering with Elbow Method & Silhouette Score

This repository demonstrates how to apply **KMeans clustering** using scikit-learn, and how to determine the optimal number of clusters using both the **Elbow Method (SSE)** and the **Silhouette Score (SIL)**.  
It also provides academic background on clustering, centroids, and scaling.

---

## 🚀 Project Overview
- Preprocessing data with **MinMaxScaler**  
- Applying **KMeans clustering** for different values of `k`  
- Calculating:
  - **SSE (Sum of Squared Errors)** for each `k`
  - **Silhouette Score** for cluster quality  
- Visualizing:
  - **Elbow Curve** (SSE vs. k)
  - **Silhouette Score Curve**

---

## 📖 Academic Background

### 🔹 Clustering
Clustering is an **unsupervised learning technique** that groups similar data points together.  
The goal is to achieve:
- **High intra-cluster similarity**: data points within the same cluster are very similar.  
- **High inter-cluster difference**: data points from different clusters are as distinct as possible.  

### 🔹 KMeans Algorithm
KMeans works by iteratively partitioning the dataset into \(k\) clusters:

1. Choose the number of clusters \(k\).  
2. Initialize \(k\) centroids randomly.  
3. **Assignment step:** assign each point to the nearest centroid using Euclidean distance:
   \[
   \text{assign}(x_i) = \arg\min_j ||x_i - \mu_j||^2
   \]
4. **Update step:** recompute each centroid as the mean of all points in its cluster:
   \[
   \mu_j = \frac{1}{N_j} \sum_{x_i \in C_j} x_i
   \]
5. Repeat steps 3–4 until centroids stabilize or a maximum number of iterations is reached.

### 🔹 Centroids
- A **centroid** is the "center of mass" of a cluster.  
- It is not necessarily a real data point, but rather the **average of all points** in that cluster.  

Example:  
For points \((2,4), (4,6), (6,8)\), the centroid is:
\[
\mu = \left(\frac{2+4+6}{3}, \frac{4+6+8}{3}\right) = (4,6)
\]

### 🔹 Scaling (Normalization)
KMeans uses distance-based calculations. If features have different units or ranges (e.g., height in meters [1–2] vs. weight in kg [40–100]), large-scale features dominate the clustering.  
To fix this, we use **scaling**:

- **MinMaxScaler** transforms each feature into the range \([0,1]\):
  \[
  x' = \frac{x - x_{\min}}{x_{\max} - x_{\min}}
  \]
- This ensures all features contribute equally to distance calculations.

### 🔹 Evaluating the Optimal Number of Clusters
- **Elbow Method (SSE):** plot SSE vs. k, and look for the "elbow" point where adding more clusters doesn’t improve much.  
- **Silhouette Score (SIL):** measures cluster quality (range: -1 to 1).  
  - Close to 1 → well-clustered.  
  - Around 0 → clusters overlap.  
  - Negative → point may be assigned to the wrong cluster.

---

## 📂 Repository Structure
data/salaires.csv
src/Clustering_With_KMeans.ipynb
