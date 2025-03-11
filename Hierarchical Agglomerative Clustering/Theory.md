**Hierarchical Clustering**

Hierarchical Clustering groups similar data points into clusters, continuing the process until a single cluster remains. A key example is the **dendrogram**, which helps determine the optimal number of clusters.

### Types of Hierarchical Clustering
1. **Agglomerative Hierarchical Clustering** (Bottom-Up Approach)
   - Each data point starts as an individual cluster.
   - Closest clusters are merged iteratively until only one cluster remains.
2. **Divisive Hierarchical Clustering** (Top-Down Approach)
   - Starts with one cluster containing all data points and recursively splits them into smaller clusters.

### Steps to Perform Agglomerative Hierarchical Clustering
1. **Make each data point a single cluster** (n clusters initially).
2. **Merge the two closest clusters**, reducing the count to (n-1).
3. **Repeat** until only one cluster remains.

### Python Implementation
#### 1. Data Preprocessing
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

dataset = pd.read_csv('Mall_Customers_dataset.csv')
X = dataset.iloc[:, [3, 4]].values
```

#### 2. Finding the Optimal Number of Clusters (Dendrogram)
```python
import scipy.cluster.hierarchy as sch

plt.figure(figsize=(10, 5))
dendrogram = sch.dendrogram(sch.linkage(X, method='ward'))
plt.title('Dendrogram')
plt.xlabel('Customers')
plt.ylabel('Euclidean Distance')
plt.show()
```

#### 3. Training the Agglomerative Hierarchical Clustering Model
```python
from sklearn.cluster import AgglomerativeClustering

hc = AgglomerativeClustering(n_clusters=5, metric='euclidean', linkage='ward')
y_hc = hc.fit_predict(X)
```

#### 4. Visualizing the Clusters
```python
colors = ['red', 'blue', 'green', 'cyan', 'magenta']
labels = ['Cluster 1', 'Cluster 2', 'Cluster 3', 'Cluster 4', 'Cluster 5']

plt.figure(figsize=(8, 6))
for i in range(5):
    plt.scatter(X[y_hc == i, 0], X[y_hc == i, 1], s=100, c=colors[i], label=labels[i])

plt.title('Clusters of Customers')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend()
plt.show()
```

### Observations
- **Cluster 1:** Average income, average spending.
- **Cluster 2:** High income, low spending (**Careful** customers).
- **Cluster 3:** Low income, low spending (**Sensible** customers).
- **Cluster 4:** Low income, high spending (**Careless** customers).
- **Cluster 5:** High income, high spending (**Target customers** - most profitable).

This clustering helps businesses identify customer segments and optimize marketing strategies.

