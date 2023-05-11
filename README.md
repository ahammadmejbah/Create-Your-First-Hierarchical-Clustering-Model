# Create-Your-First-Hierarchical-Clustering-Model

A common technique for grouping things is called hierarchical clustering. It divides items into groups such that they are similar to one another and distinct from those in other groups. A dendrogram is a type of hierarchical tree that graphically depicts clusters.

The quantity of clusters need not be predetermined. To get the necessary number of clusters, the dendrogram can instead be sliced at the proper level.
Dendrograms make it simple to summarize and organize data into a hierarchy. Cluster analysis and interpretation are made simple with dendrograms.

``` python 

#Importing pandas library to read CSV data file
import pandas as pd

#Importing matplotlib.pyplot to plot the results
import matplotlib.pyplot as plt

#Reading CSV data file into Python
dataset = pd.read_csv('Movies.csv')
X = dataset.iloc[:, [0, 2]].values

#Importing scipy.cluster.hierarchy to create dendrogram
import scipy.cluster.hierarchy as sch
dendrogram = sch.dendrogram(sch.linkage(X, method = 'ward'))
plt.title('Dendrogram')
plt.xlabel('Movies')
plt.ylabel('Euclidean distances')
plt.show()

#Importing and Fitting Hierarchical Clustering to dataset
from sklearn.cluster import AgglomerativeClustering
h_clus = AgglomerativeClustering(n_clusters = 3, affinity = 'euclidean', linkage = 'ward')
y = h_clus.fit_predict(X)

# Plotting results to show the clusters
plt.scatter(X[y == 0, 0], X[y == 0, 1], s = 50, c = 'blue', label = 'Cluster 1')
plt.scatter(X[y == 1, 0], X[y == 1, 1], s = 50, c = 'red', label = 'Cluster 2')
plt.scatter(X[y == 2, 0], X[y == 2, 1], s = 50, c = 'purple', label = 'Cluster 3')
plt.title('Clusters of customers')
plt.xlabel('Production Budgest($M)')
plt.ylabel('Gross Income($M)')
plt.legend()
plt.show()

```

![image](https://github.com/ahammadmejbah/Create-Your-First-Hierarchical-Clustering-Model/assets/56669333/bad3eec7-0627-4aa7-97c7-c0abcb60bb26)
