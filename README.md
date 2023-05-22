# Food Loss and Waste 
By: Lisa Liang, Juliana Sahagun, Triston Crossland

---
# Table of Contents:

<!--ts-->
   * [Background Information](#background-information)
   * [Problem Statement](#problem-statement)
   * [Model Goals](#model-goals)
   * [Data](#data)
   * [Methods](#methods)
        * [Data Collection](#data-collection)
        * [Data Cleaning](#data-cleaning)
        * [Exploratory Data Analysis](#exploratory-data-analysis)
        * [Preprocessing](#preprocessing)
        * [Modeling](#modeling)
   * [Conclusions & Recommendations](#conclusions--recommendations)
   


## Background Information:
Our group consists of data scientists who have been contracted  by the United Nations. Our mission is to identify rational data-driven solutions for pressing domestic and global issues. Specifically, our team was tasked with building models that would address Target 12.3 of the SDG, which states “by 2030, halve the per capita global food waste at the retail and consumer level, and reduce food losses along production and supply chains including post-harvest losses.”

This work is critical as reducing food waste and loss not only has the potential to feed the hungry but also to conserve our natural resources, combat climate change, and promote economic efficiency. Our approach employs various machine learning and statistical models to understand, predict, and ultimately curb waste patterns, providing a roadmap to a sustainable future where resources are optimally utilized, and no one goes to bed hungry.

## Problem Statement:
Leveraging advanced machine learning techniques, our team is developing models that address both aspects of Target 12.3, with two primary objectives: identifying the stages of food supply where loss occurs, and predicting the percentage of food wasted in different countries.

## Model Goals:

Our classification models are designed to reliably categorize the stage of food loss–be it production, post-harvest, retail, or consumption–based on a variety of factors including the type of commodity, year, loss percentage, and regional activities. This model will provide actionable insights that could streamline the food supply chain and significantly reduce food waste.
Our regression models are designed to accurately estimate the percentage of food loss across various nations. This model factors in not only the production and environmental circumstances but also the societal and economic conditions, thus providing a comprehensive understanding of food waste. By highlighting the underlying causes, we can begin to address this global issue at its roots.

We have integrated elements of both supervised and ensemble learning into these models, striking a balance between utilizing existing knowledge and uncovering new patterns. Ultimately, our project contributes to the urgent global endeavor of minimizing food waste, thereby promoting environmental sustainability, economic efficiency, and human welfare. 


### Data:

Food Loss and Waste Data - https://www.fao.org/platform-food-loss-waste/flw-data/en/

Geographical Data - https://github.com/albertyw/avenews/blob/master/old/data/average-latitude-longitude-countries.csv

# Methods

#### Data Collection

1. Gathered a dataset from the Food and Agriculture Organization of the United Nations containing information on food loss and waste throughout the years 2000- 2021

2. Found geographical data on github containing latitude and longitude of the different countries

3. Combined both datasets to create a final data frame resulting in  additional features, enhancing the performance of the models

#### Data Cleaning:

1. Columns  'ISO 3166 Country Code’, 'url', 'loss_percentage_original', 'm49_code', 'cpc_code', and 'method_data_collection' were not relevant for us to look at for our project 

2. Columns with more than 50% nulls were dropped from the dataset

3. Looked for patterns within the rows with missing values

4. Null values in the 'activity' column were consistently associated with the phrases 'Whole supply chain' and 'FAO's annual Agricultural Production Questionnaire..'. Therefore, a decision was made to impute these missing values with 'wsc' as a placeholder, instead of using the term 'missing'

5. Remaining 49 rows with missing values were dropped from the dataset

6. Final Shape of dataframe: 27724 rows , 8 columns



#### Exploratory Data Analysis:

1. Presented summary statistics for the numerical features in the dataset

2. Plotted a histogram to visualize the distribution of values in the numeric columns

3. Constructed two histograms: one illustrating the correlations with the target column 'loss_percentage' and another displaying the correlations among the different numeric features

4. Developed two graphs showcasing the top 5 countries with the highest average percentage loss and the top 5 countries with the lowest average percentage loss

5. Created a line plot to visualize the trend in loss percentage over the years 2000-2021

6. Utilized maps to illustrate the geographical distribution of loss percentage and food supply stage for the years 2000, 2011, 2020, and 2021

7. Displayed a bar chart representing the food supply stage with the most significant amount of loss

#### Preprocessing:

1. Defined my target and relevant features for the model 

2. Performed train test split on data

3. Applied a scalar to the numeric features and one hot encoded the categorical features.

4. Instantiate models for regression and classification problem

5. Obtained a baseline score to assess the initial performance of the each model

#### Modeling:

In our regression problem, we chose to assess the performances of Random Forest, Decision Tree, Stacking (features = Random Forest, Decision Tree, Bagging; estimator = Linear Regression), and Gradient Boosting.

**Regression Models**
|Model|R2|MSE|RMSE
|---|---|---|---|
|Decision Tree|0.6063|10.5502|3.2481
|Random Forest|0.7174|7.5719|2.7517
|Stacking|0.7224|7.4384|2.7273
|Gradient Boosting|0.4874|13.7363|3.7063

**Regression Evaluation**: Overall, the best performing model was Stacking wth a R2 score of 72.24% with Random Forest following closely at 71.74%. 72.24% of the variability in the 'loss_percentage' that can be explained by the features in our model. The Mean Squared Error (MSE) averages the squared difference between estimated values and actual values. Although at 7.4384, Stacking still had the lowest score that means the predictions are decently close to the actual values. One concern we had with our models was the overfitting of the train data against the test data. Even though the scores were high, the model may not be receiving new data well to make accurate predictions. 

For our classification problem, we examined models of Random Forest, Decision Tree, and Neural Networks.

**Classification Models**
|Model|Recall|Precision|F1|Accuracy
|---|---|---|---|---|
|Random Forest|0.9628|0.9617|0.9619|0.9628
|Decision Tree|0.9641|0.9643|0.9641|0.9641
|Neural Network|0.9246|0.9146|0.9176|0.9246

**Classification Evaluation**: All models that we experimented with performed well and could be justified in use depending on your problem statement and approach. The Decision Tree demonstrated the best Accuracy score of 96.41%, meaning that given a prediction, we would have a likelihood to be correct 96.41% of the time. Despite this, we remind you that the dataset is imbalanced as 'Farm' dominates over 40% of the data while the remaining 16 labels each represent less than 20%. To further our models, we'd recommend doing imbalanced data techniques like SMOTE or AdaSyn to evaluate its results. We also assessed the F1 scores that finds the balance between the recall and precision metrics on correct predictions over a dataset. In a case of false negatives or positives, producers could distribute the incorrect resources on a Farm stage which would hinder the entire stage if the actual problem is not being resolved. Decision Tree's F1 score was 96.41% that shows its ability to balance false positives and false negatives.

## Conclusions & Recommendations
**Real-World Application Example**: Earlier, we noted that Haiti had the highest food loss percentage with over 50% of their food production being lost or wasted. In December 2022, the United Nations drew attention to the impending crisis in Haiti where approximately 4.7 million people are struggling with food insecurity. Reasons for this crisis include the "poor performance on agricultural productions and heavy dependence on food imports'' ([*source*](https://news.un.org/en/story/2022/12/1131572)) that are subject to inflation and price volatility. To understand better where food is lost or wasted the most, we could employ our regression model in predicting these values among their regions. Our classification model would extend these steps by accurately classifying the food supply stage that correlates most with that region. These initiatives could be taken on by global leaders with the ability to financially support the action plan for Haitian producers and farmers. To further our solution, we would recommend adding features that consider weather patterns (e.g. droughts, hurricanes), and evaluating the agricultural land quality that contribute to food loss. If we recognize how food is lost, we can mitigate the impact by distributing resources more effectively (e.g. more infrastructure support if it's 'Farm' that needs to be focused on).  

**Other Recommendations**
- Further Research: To improve predictions and accuracy, we recommend additional research to investigate other features that may influence loss percentage and were not included in the dataset. We could include variables like socioeconomic factors, infrastructure, technology investments, market dynamics, weather patterns. This approach will enable us to develop better models that capture the dimensionality of the problem, facilitating more effective strategies to mitigate food loss in the future.
- Focus on High Loss Stages: Our models indicate that certain stages of the food supply chain are more prone to losses. Targeting these stages with interventions could significantly reduce overall food loss.
- Policy Making: The insights derived from this analysis can guide policy-makers in formulating effective strategies for managing food loss and waste. The results highlight the need for comprehensive, stage-specific interventions.
- Investment in Technology: Technological advancements could be a crucial factor in reducing food loss. Investing in technologies for food preservation, efficient supply chain management, and accurate demand forecasting could yield significant benefits.
- Awareness and Education: Public awareness and education about food waste can have a considerable impact. Consumers need to be educated about the implications of food waste and how they can contribute to its reduction.


----
