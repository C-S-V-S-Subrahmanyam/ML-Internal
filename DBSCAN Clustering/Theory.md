**DBSCAN Clustering**

### Overview
DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a density-based clustering algorithm. Unlike K-Means, it does not require the number of clusters to be predefined and is effective in identifying outliers.

### Key Concepts
- **Density-Based Clustering**: Separates high-density regions from low-density regions.
- **Distance Measure**: Typically uses Euclidean distance.
- **Outlier Detection**: Identifies noise points in sparse regions.

### Parameters
1. **Epsilon (Eps)**: The minimum distance between two points to be considered neighbors.
2. **MinPoints**: The minimum number of points required to form a cluster.

### Types of Data Points
1. **Core Points**: Have at least `MinPoints` within `Eps` distance.
2. **Border Points**: Not core points but within `Eps` of a core point.
3. **Noise Points**: Neither core nor border points.

### Algorithm Steps
1. Select a random point and find its `Eps` neighbors.
2. If the point has at least `MinPoints` neighbors, form a cluster.
3. Expand the cluster by adding its neighbors.
4. Repeat for all unclustered core points.
5. Assign border points to the nearest cluster and mark outliers.

---

## **Implementation of DBSCAN**

### **Step 1: Data Preprocessing**
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Import dataset
data = pd.read_csv('Mall_Customers_dataset.csv')
# Check for missing values
data.isnull().any().any()

# Extract features
x = data.loc[:, ['Annual Income (k$)', 'Spending Score (1-100)']].values
```

### **Step 2: Compute Parameters**
- **MinPoints**: For 2D data, use `MinPoints = 4`.
- **Epsilon (Eps)**: Compute using Nearest Neighbors.
```python
from sklearn.neighbors import NearestNeighbors
neighb = NearestNeighbors(n_neighbors=2)
nbrs = neighb.fit(x)
distances, indices = nbrs.kneighbors(x)
```

### **Step 3: Determine Epsilon Value**
```python
# Sort and plot distances
import matplotlib.pyplot as plt

distances = np.sort(distances, axis=0)
distances = distances[:, 1]
plt.figure(figsize=(5,3))
plt.plot(distances)
plt.show()
```
From the plot, identify the maximum curvature point (e.g., `Eps = 8`).

### **Step 4: Implement DBSCAN Model**
```python
from sklearn.cluster import DBSCAN

# Apply DBSCAN
dbscan = DBSCAN(eps=8, min_samples=4).fit(x)
labels = dbscan.labels_
```

### **Step 5: Visualizing Clusters**
```python
plt.scatter(x[:, 0], x[:, 1], c=labels, cmap='plasma')
plt.xlabel("Income")
plt.ylabel("Spending Score")
plt.show()
```

### **Conclusion**
DBSCAN effectively clusters data without specifying `K` and detects outliers. It works well for non-linearly separable data but may struggle with varying densities. Choosing `Eps` carefully is crucial for optimal results.

