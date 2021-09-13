# HousePricesKaggle
## Table of contents
* [Description of the problem](#description-of-the-problem)
* [Approach](#my-approach)
* [Selected graphs](#selected-graphs)
* [Model evaluation](#model-evaluation)
* [Final Thoughts](#final-thoughts)

## Description of the problem
The dataset has been downloaded from kaggle ([here](https://www.kaggle.com/c/house-prices-advanced-regression-techniques))  
It contains the data about houses in Ames, Iowa. It contains 79 explanatory variables and an independent, continuous variable (the sale price).  

## My approach
- EDA
- Examining relationships between variables (used Pearson's correlation for numerical features, Kendall rank correlation for ordinal features, decision tree importance for nominal features)
- Feature selection based on the previous step, dropped the features that were highly correlated with each other to avoid multicollinearity
- Transforming the dataset:  
    1) Imputing missing values (for numerical features I used median, for ordinal and nominal I used the most frequent value)
    2) Scaling numerical features and the output variable
    3) Encoding ordinal and nominal features (used OrdinalEncoder for ordinal features and OneHotEncoder for nominal features)
    4) Performed cross-validation and grid-search to find the best estimator. As the scoring method I chose RMSE
- Transforming the test set
- Making predictions

## Selected graphs
<center> Correlation matrix </center>  

[![Correlation matrix](/graphs/correlation_matrix.png)]  
<center> Numerical features with high correlation with the output variable </center>  

[![High correlation](/graphs/high_correlation.png)]  
<center> Relationship between ordinal variables and the output variable </center>  

[![Ordinal relationship](/graphs/ordinal_relationship.png)]
<center> Nominal features importances </center>  

[![Importances](/graphs/importances.png)]  

## Model evaluation
SVR turned out to be the best estimator. It got 0.353 average error during the cross-validation.  

## Final thoughts
- Using IterativeImputer instead of a SimpleImputer could improve the score  
- More advanced feature engineering could improve the score  
- Possibly using ANN could lead to better results  