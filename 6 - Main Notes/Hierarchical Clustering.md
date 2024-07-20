2024-07-05 - 14:59
Status:
Tags: [[clustering]] [[Agglomerative Clustering]] [[Divisive Clustering]]
# Hierarchical Clustering

Hierarchical clustering is a general family of clustering algorithms that build nested clusters by merging or splitting them successively. This hierarchy of clusters is represented as a tree (or dendrogram). The root of the tree is the unique cluster that gathers all the samples, the leaves being the clusters with only one sample.

- **Agglomerative**: This is a "[bottom-up](https://en.wikipedia.org/wiki/Top-down_and_bottom-up_design "Top-down and bottom-up design")" approach: Each observation starts in its own cluster, and pairs of clusters are merged as one moves up the hierarchy.
- **Divisive**: This is a "[top-down](https://en.wikipedia.org/wiki/Top-down_and_bottom-up_design "Top-down and bottom-up design")" approach: All observations start in one cluster, and splits are performed recursively as one moves down the hierarchy.

In general, the merges and splits are determined in a [greedy](https://en.wikipedia.org/wiki/Greedy_algorithm "Greedy algorithm") manner. The results of hierarchical clustering are usually presented in a [dendrogram](https://en.wikipedia.org/wiki/Dendrogram "Dendrogram").

## Agglomerative

The [`AgglomerativeClustering`](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html#sklearn.cluster.AgglomerativeClustering "sklearn.cluster.AgglomerativeClustering") object performs a hierarchical clustering using a bottom up approach: each observation starts in its own cluster, and clusters are successively merged together. The linkage criteria determines the metric used for the merge strategy:

- **Ward** minimizes the sum of squared differences within all clusters. It is a variance-minimizing approach and in this sense is similar to the k-means objective function but tackled with an agglomerative hierarchical approach.
- **Maximum** or **complete linkage** minimizes the maximum distance between observations of pairs of clusters.
- **Average linkage** minimizes the average of the distances between all observations of pairs of clusters.
- **Single linkage** minimizes the distance between the closest observations of pairs of clusters.

![[Different linkage type.png]]
Agglomerative cluster has a “rich get richer” behavior that leads to uneven cluster sizes. In this regard, single linkage is the worst strategy, and Ward gives the most regular sizes. However, the affinity (or distance used in clustering) cannot be varied with Ward, thus for non Euclidean metrics, average linkage is a good alternative. Single linkage, while not robust to noisy data, can be computed very efficiently and can therefore be useful to provide hierarchical clustering of larger datasets. Single linkage can also perform well on non-globular data.

```
from sklearn.cluster import AgglomerativeClustering
import numpy as np
X = np.array([[1, 2], [1, 4], [1, 0],
              [4, 2], [4, 4], [4, 0]])
clustering = AgglomerativeClustering().fit(X)
clustering
clustering.labels_
```

## Divisive Clustering

Divisive Clustering is the technique that starts with all data points in a single cluster and recursively splits the clusters into smaller sub-clusters based on their dissimilarity. It is also known as, “top-down” clustering. It starts with all data points in a single cluster, and then recursively splits the clusters into smaller sub-clusters based on their dissimilarity.

Unlike agglomerative clustering, which starts with each data point as its own cluster and iteratively merges the most similar pairs of clusters, divisive clustering is a “divide and conquer” approach that breaks a large cluster into smaller sub-clusters

## Difference between agglomerative clustering and Divisive clustering :

| S.No. | Parameters              | Agglomerative Clustering                                                                                                                                                                                                             | Divisive Clustering                                                                                                                                                                                         |
| ----- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.    | **Category**            | Bottom-up approach                                                                                                                                                                                                                   | Top-down approach                                                                                                                                                                                           |
| 2.    | **Approach**            | each data point starts in its own cluster, and the algorithm recursively merges the closest pairs of clusters until a single cluster containing all the data points is obtained.                                                     | all data points start in a single cluster, and the algorithm recursively splits the cluster into smaller sub-clusters until each data point is in its own cluster.                                          |
| 3.    | **Complexity    level** | Agglomerative clustering is generally more computationally expensive, especially for large datasets as this approach requires the calculation of all pairwise distances between data points, which can be computationally expensive. | Comparatively less expensive as divisive clustering only requires the calculation of distances between sub-clusters, which can reduce the computational burden.                                             |
| 4.    | **Outliers**            | Agglomerative clustering can handle outliers better than divisive clustering since outliers can be absorbed into larger clusters                                                                                                     | divisive clustering may create sub-clusters around outliers, leading to suboptimal clustering results.                                                                                                      |
| 5.    | **Interpretability**    | Agglomerative clustering tends to produce more interpretable results since the dendrogram shows the merging process of the clusters, and the user can choose the number of clusters based on the desired level of granularity.       | divisive clustering can be more difficult to interpret since the dendrogram shows the splitting process of the clusters, and the user must choose a stopping criterion to determine the number of clusters. |
| 6.    | **Implementation**      | Scikit-learn provides multiple linkage methods for agglomerative clustering, such as “ward,” “complete,” “average,” and “single,”                                                                                                    | divisive clustering is not currently implemented in Scikit-learn.                                                                                                                                           |
| 7.    | **Example**             | Here are some of the applications in which Agglomerative Clustering is used :<br><br>Image segmentation, Customer segmentation, Social network analysis, Document clustering, Genetics, genomics, etc., and many more.               | Here are some of the applications in which Divisive Clustering is used :<br><br>Market segmentation, Anomaly detection, Biological classification, Natural language processing, etc.                        |


# Reference

[`Sklearn Hierarchical clustering`](https://scikit-learn.org/stable/modules/clustering.html#hierarchical-clustering)
[`AgglomerativeClustering`](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.AgglomerativeClustering.html#sklearn.cluster.AgglomerativeClustering "sklearn.cluster.AgglomerativeClustering")
[`Difference Between Agglomerative clustering and Divisive clustering`](https://www.geeksforgeeks.org/difference-between-agglomerative-clustering-and-divisive-clustering/)
