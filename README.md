# Abalone Health Investigation Report

This report will focus on the steps taken to build and complete appropriate models on the health of the Abalone populations within the seas surrounding the West coast of Australia. This is so the relative comparative investigation can be used to determine the health of the Abalone’s population, within the geographical area, for Males (M), Female (F) and Infants (I) based upon differing variables.

## Data Preparation 

##### Figure 1.1 - exploring the datasets

The two datasets for the Abalone populations (2020 and 2021) used in the investigation have columns that include sex, length (mm), diameter (mm), height (mm), whole weight (g) which represents the total weight of the abalone, shucked weight (g) which represents the
weight of the abalone meat without its shell, sell weight (g) which represents the weight of the abalone's shell and spots which represents the number of spots or rings on the abalone
shell.

### Summary Statistics

##### Figure 1.2 - Info() on datasets

##### Figure 1.3 - describe() on datasets

The datasets were further explored using describe() and info() methods and then the distributions of different features like Length, Diameter, and others were visualized using a histogram plot for the numerical columns and a bar chart for the gender column.

##### Figure 1.4 - histogram plot on both datasets

##### Figure 1.5 - bar chart plot used on the gender column

The above helped to reveal any oddities in the data as seen with the sex column having an extra category or the greater range of data in the height column within the 2020 dataset.

### Handling Missing Data

##### Figure 1.6 - counting null values and dropping them

##### Figure 1.7 - removing extra category from sex column

##### Figure 1.8 - rounding values in spots column within both datasets

Zeros in the datasets were replaced with NaN, rows with missing values were dropped as they were few in number, and the extra category in the sex column was removed. This process was carried out on both datasets. The spots column in the datasets had values that needed to be converted to whole numbers so they were rounded.Outliers

##### Figure 1.9 - outlier detection and removal using z-score method

The number of outliers were counted to determine if it was better to remove or to retain them. These outliers were few in number compared to the number of rows so it was decided that they were best removed. The outliers were removed using the z-score method.

### Descriptive Statistics on Cleaned Data

##### Figure 1.10 - describe() on both datasets

##### Figure 1.11 - histogram on numerical columns

##### Figure 1.13 - bar chart on corrected sex column

The same descriptive statistics methods and plots were used to visualize the cleaned data.

### Label Encoding

##### Figure 1.14 - label encoding the sex column

To allow for the models used in this investigation to work with all columns in the datasets, it was determined that it was best to encode the sex column. The categorical sex column values were encoded to numeric values (Male: 1, Female: 2, Infant: 3).

##### Figure 1.15 & 1.16 - distribution by sex

The features were visualized using a box plot to demonstrate their distribution by sex. This shows that on average, the female population is bigger across both datasets.

## Methodology
The models used in this investigation are k-means as it is able to create groups within data that have similarities, logistic regression for its simplicity and effectiveness in binary classification problems (healthy vs. unhealthy), and random forest’s ability to handle both categorical and numerical variables while minimizing overfitting.

### Feature Correlation

##### Figure 2.1 - correlation matrix on both datasets

##### Figure 2.2 - dropping redundant features

To gauge which columns to use in determining health, a correlation matrix is used to check for redundant columns that can be removed without any negative effects on the models. Based on the results of the correlation matrix, shucked weight(g) and sell weight(g) was
removed as it is highly correlated with whole weight(g). Diameter(mm) was removed due to its high correlation with the length(mm) and height(mm) features.

### Training Models

Length(mm) and whole weight(g) will be used as features to train the clustering model (k-means) while sex, height(mm), and spots will be used as features in the classification models (logistic regression and random forest) data.

##### Figure 2.3 - selecting features for clustering model

The above in figure 2.3 was repeated for the 2021 dataset

##### Figure 2.4 - splitting & scaling data for model (logistic regression and random forest) training and evaluation

The dataset used for classification was split into training and testing sets (70/30 split) to train and then test model performance.

##### Figure 2.5 - function to make training and evaluating the classification algorithms easier

The function shown in figure 2.5 was created to reduce repeated code and is used to make training and evaluating classification algorithms much easier with the confusion matrix, accuracy and classification report.

## Results

### KMeans

##### Figure 3.1 - KMeans clustering implementation

This code was repeated for the 2021 dataset.Logistic Regression

##### Figure 3.2 - logistic regression performance

The same code was repeated for the 2021 dataset.Random Forest

##### Figure 3.3 - random forest performance

The same code was repeated for the 2021 dataset.

## Conclusion

PCA as shown in figure 3.1 visualizes the clusters created by the KMeans clustering
algorithm. The PCA (principal component analysis) projection shows the clusters are well separated as the two groups are not overlapping. It suggests that the clustering is meaningful and captures important similarities in the data. The silhouette score also demonstrates the performance of KMeans clustering as the closer the number is to one the better the model. A score of 0.58 suggests the model is good at creating clusters.

The cluster labels created were used to train the classification models (logistic regression and random forest). The results of the training revealed that random forest was better at predicting future cluster labels as it had an accuracy score of 0.88 while logistic regression had 0.78. The classification report also had better numbers for random forest and as shown by the confusion matrix for both, random forest
had less false positives overall.

Length and weight was used to train the clustering model as it has been shown that the
relationship between length and weight can be used to assess the health of marine life (Li et al, 2023, introduction section). This relationship can be used to determine the health of marine life in different aquatic environments (Basak and Hadiuzzaman, 2019, introduction
section). 

Features that correlated highly with weight and length were removed, simplifying
the data. As revealed by the descriptive statistics performed on the datasets that are grouped by their cluster labels, the first cluster (1) had more females in the population and more abalone that tended to be heavier and taller. They also had a greater number of spots. This would seem to indicate that this cluster was healthier overall.