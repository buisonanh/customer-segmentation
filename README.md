# **Customer Segmentation Using RFM Analysis**

## Table of Contents
1. [Introduction](#introduction)
2. [Data Preparation](#data-preparation)
3. [RFM Calculation](#rfm-calculation)
4. [Data Scaling](#data-scaling)
5. [Clustering Analysis](#clustering-analysis)
6. [Visualizations](#visualizations)
7. [Recommendations](#recommendations)
8. [Conclusion](#conclusion)

## <a name="introduction">Introduction</a>
Customer segmentation is the process of dividing a customer base into groups of individuals that are similar in specific ways relevant to marketing. This project aims to present the results of clustering analysis conducted on the transactional data of a company’s customers, using Recency, Frequency, and Monetary (RFM) values.

## <a name="data-preparation">Data Preparation</a>

### **1. Data Overview**
The dataset consists of transactional data and item details:
- **Transactions Dataset**: Contains information about customer transactions, including `CustomerID`, `OrderID`, `ItemID`, `TransactionDate`, etc.
- **Items Dataset**: Contains details about items, including `ItemID` and `SellPrice`.

### **2. Data Cleaning**
- **Missing Values**: Both datasets were checked for missing values.
- **Duplicates**: Duplicates were identified and handled accordingly.
- **Data Merging**: The `SellPrice` from the items dataset was merged with the transactions dataset using `ItemID`.

## <a name="rfm-calculation">RFM Calculation</a>

### **1. Recency**: 
Recency was calculated as the number of days since the customer’s last transaction.

### **2. Frequency**:
Frequency was measured by counting the number of unique transactions for each customer.

### **3. Monetary**:
Monetary value was calculated by summing up the transaction amounts for each customer.

The calculated RFM scores were then merged into a single dataframe.

## <a name="data-scaling">Data Scaling</a>
The RFM values were scaled using the `StandardScaler` to standardize the data for clustering.

## <a name="clustering-analysis">Clustering Analysis</a>

### **1. K-Means Clustering**
K-Means clustering was chosen for segmenting the customers. The optimal number of clusters was determined using the **Elbow Method** and the **Silhouette Coefficient**.

#### **Elbow Method**:
The Sum of Squared Errors (SSE) was plotted against the number of clusters. The optimal number of clusters was identified at the elbow point, which was found to be 3 clusters.

#### **Silhouette Coefficient**:
The silhouette score for each number of clusters was calculated, with the highest score indicating the best clustering structure. The best number of clusters was also identified as 3.

### **2. Cluster Analysis**
Two clustering structures were tested: 3 clusters and 4 clusters. 

#### **3 Clusters (Optimal)**
- **Cluster 1: Moderate Engagement (Green)**
  - **Recency**: 934 -> 1187
  - **Frequency**: 1 -> 6
  - **Monetary**: 745 -> 16153
  - **Description**: Customers with moderate engagement levels, average spending, and less frequent transactions.

- **Cluster 2: Active Customers (Orange)**
  - **Recency**: 870 -> 940
  - **Frequency**: 1 -> 12
  - **Monetary**: 1296 -> 29255
  - **Description**: Customers with recent and frequent transactions, spending at various levels.

- **Cluster 3: High-Value Customers (Purple)**
  - **Recency**: 870 -> 934
  - **Frequency**: 10 -> 20
  - **Monetary**: 22110 -> 62539
  - **Description**: Highly engaged and valuable customers with frequent transactions and significant spending.

#### **4 Clusters**
Adding a fourth cluster provided a finer segmentation but was not as optimal based on the silhouette score. The segmentation was less distinct, and the clusters overlapped more significantly.

## <a name="visualizations">Visualizations</a>
3D scatter plots were created to visualize the distribution of the clusters across the Recency, Frequency, and Monetary dimensions. The visualizations helped to identify and confirm the natural grouping of customers within the dataset.

## <a name="recommendations">Recommendations</a>

1. **For Moderate Engagement Customers**:
   - Increase engagement through targeted communication, personalized offers, and loyalty programs.

2. **For Active Customers**:
   - Continue to nurture this segment with regular updates, exclusive deals, and engagement activities to convert them into high-value customers.

3. **For High-Value Customers**:
   - Focus on retention strategies, VIP programs, and premium services to maintain their loyalty and increase their lifetime value.

## <a name="conclusion">Conclusion</a>
This segmentation analysis provides a strategic approach to understanding and targeting different customer groups. By focusing on the specific needs and behaviors of each segment, the company can optimize marketing efforts, improve customer satisfaction, and drive revenue growth.