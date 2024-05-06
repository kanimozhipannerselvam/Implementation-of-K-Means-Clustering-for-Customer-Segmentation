# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

# AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

# Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

# Algorithm
1. Choose the number of clusters (K). 
2. Initialize cluster centroids. 
3. Assign data points to clusters. 
4. Update cluster centroids.
5. Repeat steps 3 and 4. 
6. Evaluate the clustering results. 
7. Select the best clustering solution.

# Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: KANIMOZHI
RegisterNumber: 212222230060
*/

import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv("Mall_Customers.csv")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")

```

# Output:
## data.head()
![1](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/da2ccdd8-65b1-49c3-bc80-38502cc6e330)

## data.info
![2](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/ee0623e9-ce71-45b7-b35a-2bdcf3959e8b)

## data.isnull.sum()
![3](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/f8fc5e23-6311-4527-a23c-6da75eed872a)

## Elbow method Graph
![4](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/bcd388e8-664e-463c-bdc8-ce641a799cd5)

## KMeans clusters
![5](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/394e7408-4ac4-4d5d-8fc8-60f0ca4c4833)
![6](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/f1a7a8e9-a5aa-4dd7-8ff2-5e4d7e0384ba)

## Customer segments Graph
![7](https://github.com/kanimozhipannerselvam/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/119476060/b80e2ee7-d3c6-4ffb-85a2-749ffe64b4c0)


# Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
