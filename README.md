# Food Loss and Waste 
By: Lisa Liang, Juliana Sahagun, Triston Crossland

---
# Table of Contents:

<!--ts-->
   * [Background Information](#background-information)
   * [Problem Statement](https://github.com/julianasaha/Group-Project4#problem-statement)
   * [Data](#data)
   * [Methods](#methods)
   * [Models' Results and Evaluation](#models-results-and-evaluation)
   * [Recommendations](#recommendations)
   

## Problem Statement:


## Background Information:


### Data:

Food Loss and Waste Data - https://www.fao.org/platform-food-loss-waste/flw-data/en/

Geographical Data - https://github.com/albertyw/avenews/blob/master/old/data/average-latitude-longitude-countries.csv

# Methods

**Data Collection**

1. Gathered a dataset from the Food and Agriculture Organization of the United Nations containing information on food loss and waste throughout the years 2000- 2021

2. Found geographical data on github containing latitude and longitude of the different countries

3. Combined both datasets to create a final data frame resulting in  additional features, enhancing the performance of the models

**Data Cleaning:**

1. Columns  'ISO 3166 Country Code’, 'url', 'loss_percentage_original', 'm49_code', 'cpc_code', and 'method_data_collection' were not relevant for us to look at for our project 

2. Columns with more than 50% nulls were dropped from the dataset

3. Looked for patterns within the rows with missing values

4. Null values in the 'activity' column were consistently associated with the phrases 'Whole supply chain' and 'FAO's annual Agricultural Production Questionnaire..'. Therefore, a decision was made to impute these missing values with 'wsc' as a placeholder, instead of using the term 'missing'

5. Remaining 49 rows with missing values were dropped from the dataset

6. Final Shape of dataframe: 27724 rows , 8 columns



**Exploratory Data Analysis:**

1. Presented summary statistics for the numerical features in the dataset

2. Plotted a histogram to visualize the distribution of values in the numeric columns

3. Constructed two histograms: one illustrating the correlations with the target column 'loss_percentage' and another displaying the correlations among the different numeric features

4. Developed two graphs showcasing the top 5 countries with the highest average percentage loss and the top 5 countries with the lowest average percentage loss

5. Created a line plot to visualize the trend in loss percentage over the years 2000-2021

6. Utilized maps to illustrate the geographical distribution of loss percentage and food supply stage for the years 2000, 2011, 2020, and 2021

7. Displayed a bar chart representing the food supply stage with the most significant amount of loss

**Preprocessing:**

1.
2.
3.


**Modeling:**

1.
2.
3.


# Models' Results and Evaluation 



# Recommendations






----
