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