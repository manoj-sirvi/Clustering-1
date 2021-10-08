# Clustering

## Task1: Data visualisation

## Task2: K-means Clustering
Height, value and wage are string data types which are also included in the dataset.

weight, Jersey no. is removed (nan value in some places).

## Task3: Hierarchical Clustering Algorithm
Hierarchical Clustering creates clusters in a hierarchical tree-like structure (also called a **Dendrogram**). Meaning, a subset of similar data is created in a tree-like structure in which the root node corresponds to entire data, and branches are created from the root node to form several clusters.

![](https://i.imgur.com/gv3z1hY.png)
### Agglomerative Clustering (Bottom-Up)
How Agglomerative Hierarchical clustering Algorithm Works:
1. Start assigning each observation as a single point cluster, so that if we have N observations, we have N clusters, each containing just one observation. 
2. Find the closest pair of clusters and make them into one cluster, we now have N-1 clusters. This can be done in various ways to identify similar and dissimilar measures.
3. Find the two closest clusters and make them to one cluster. We now have N-2 clusters. This can be done using agglomerative clustering linkage techniques.
4. Repeat steps 2 and 3 until all observations are clustered into one single cluster of size N.

#### Implementation
**Loading and Data Cleaning**
- Only the numeric data from the csv file is loaded and also some attributes such as height, weight, value and wage have been converted from string to numeric data type.

- There are some cells with *NaN* values. To counter that we tested 2 methods:
    - droping rows and columns which contain NaN values.
    - Forward fill used to fill the NA/empty values. How it works (reference: `GeeksForGeeks`):

        ![](https://i.imgur.com/f2WnhX1.png)
        ![](https://i.imgur.com/jMu5j7r.png)

**Pre-processing data**
Data is scaled and then normalized and used as input for clustering.

**Dimensionality Reduction**
To better visualize clustering in 2D, the dimension is reduced using PCA.

**Dendogram Visualization**
![](https://i.imgur.com/SKxKBcF.png)
**How to choose optimal number of clusters based on dendogram?**

*Look for the clusters with the longest ‘branches’, the shorter they are, the more similar they are to following ‘twigs’ and ‘leaves’.*

Although finally we need to check the best no of clusters practically, this is just to visualize how data is connected and the hierarchy in it.

**Visualizing Clusters**
We did agglomerative clustering with a number of clusters = {2,3,4,5,6}.
- Method 1: dropping rows and columns with NaN values

    When they are dropped, the best no of clusters with maximum silhouette score was **`k=3`**.
    - Silhouette Scores
    ![](https://i.imgur.com/qYxhENp.png)
    Scores: ``[0.22111164675866438, 0.22096734698286216, 0.24945516810697613, 0.21685147685568962, 0.1980648052767617]``
    These scores shows that 3 is the best choice for no of clusters.
    - No of clusters = 2
    ![k=2](https://i.imgur.com/RCiLb4T.png)
    - No of clusters = 3
    ![k=3](https://i.imgur.com/9LBwD3B.png)
    - No of clusters = 4
    ![k=4](https://i.imgur.com/CKNieKn.png)
    - No of clusters = 5
    ![k=5](https://i.imgur.com/2IWlLtK.png)
    - No of clusters = 6
    ![k=6](https://i.imgur.com/dxrudPM.png)

- Method 2: Forward fill to fill NaN values
    Suprisingly the answer in this is for **`k=4`** which is different from Method 1.
    - Silhouette Scores
    ![](https://i.imgur.com/cAHbbWx.png)
    Scores: `[0.22111164675866438, 0.22096734698286216, 0.24945516810697613, 0.21685147685568962, 0.1980648052767617]`
    These scores shows that 4 is the best choice for no of clusters.
    - No of clusters = 2
    ![k=2](https://i.imgur.com/8xkPCYB.png)
    - No of clusters = 3
    ![k=3](https://i.imgur.com/haRWot0.png)
    - No of clusters = 4
    ![k=4](https://i.imgur.com/HW3FuZO.png)
    - No of clusters = 5
    ![k=5](https://i.imgur.com/0RB8pWl.png)
    - No of clusters = 6
    ![k=6](https://i.imgur.com/4AIbZSC.png)

Out of both methods we chose the filling method because we feel that in the first method we are losing data and as we can see that the visualizations are kind of sparse relatively.