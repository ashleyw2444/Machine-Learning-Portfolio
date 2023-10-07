# Machine-Learning-Portfolio
The Dataset:
For this project, I worked with the World Happiness Report (WHR) data set (WHR2018Chapter2OnlineData.csv). 

The Label:
I predicted the Life Ladder (a measure of happiness) value given the values of relevant features. 
Life Ladder is defined as the value that an individual would rate their life if imagining it as a ladder
on a scale from 0 to 10 inclusive, with 0 representing the bottom of the ladder (the worst possible life) 
and 10 representing the top of the ladder (the best possible life). Using the data provided as measures 
of important factors in life, I trained a model that can predict the likely evaluation inhabitants of 
that country will make of their lives.

Type of Problem (Classification or Regression):
This was a regression problem since my model determines a numerical value as output. 
Because the data set covers 141 countries out of the total 195 (or around 72 percent of the total) in 2017, 
there is some class imbalance due to the 54 countries that are omitted.

Significance of this Problem:
This is an important problem because the label (life ladder) is a measure of inhabitants’ sense of 
life satisfaction. By creating a model that addresses this problem, a company would be able to determine 
the relevant factors that affect a human’s contentment. Organizations such as a non-profit or 
a government agency in a country suffering from issues that heavily impact their people’s livelihood 
would be able to evaluate the potential effects of programs designed to improve people’s lives 
for the greatest benefit using this model. For instance, if the model indicates that GDP is a highly significant
factor, the organization could put more priority on creating jobs and promoting business over another program 
that could have less of an effect in the case of budget or time constraints. 

Project Implementation Process:
1) Data Understanding - I first gained a general understanding of my set using the head() method and noticed the range of years
  of data that each country had. The range wasn’t uniform across all the countries, so I decided to focus
  on the most recent year 2017. After then analyzing the dataset for missing null values, I found that
  only two features had no missing values: Standard deviation of ladder by country-year and
  Standard deviation/Mean of ladder by country-year. However, considering that the total number of features
  is over a dozen, I felt that those two alone would not be sufficient for feature engineering. For this reason,
  I decided to prepare more features that had few missing values (under 10): Log GDP per capita, Social support,
  Healthy life expectancy at birth, Freedom to make life choices, Positive affect, and Negative affect,
  and Generosity. Because the dataset included data from previous years that I felt could be a good general
  estimate of the missing values, assuming there weren’t any drastic changes, I used the fillna() method
  to fill in values. This copied previous values in the column down to replace NaN values.
  While I intended this to work only for the features mentioned above, this also filled the columns
  with an extreme number of missing values, so I limited the features I tested for relevance to the features
  I intended to use as data input.
2) Data Preparation - To prepare my data, I first removed the rows that correspond to the years before
  the most recent year I have data on (which is 2017) to focus my model on the differences between countries
  and not the changes within the individual countries over time. Since some of my features had missing values,
  I filled those null values with suitable values, specifically the value the country had for that specific feature
  in a previous year, assuming not too much variation from year to year. In the case of features with completely
  missing values (such as Democratic Quality and Delivery Quality), I removed those columns to include only
  relevant data. I then split my data randomly between the training, validation, and test sets since
  the data preparation process set up my data set to be non-temporal in nature. 
3) Model Training - I trained two models to find the optimal one with the best hyperparameter values:
   a stacking model and a decision tree model. I worked with these kinds of models because I used
   a number of features, which can result in a complicated model that is ill-suited for linear regression.
   However, as decision trees can be prone to overfitting, I used multiple trees in the stacking ensemble
   method to reduce error.
4) Model Evaluation - To evaluate my models, I used the root mean squared error (RMSE) and r squared (R2)
   metrics. I found that my stacking ensemble model performed better than the default decision tree
   as the former had a lower RMSE value (indicating less error between the predictions and actual values)
   and a higher R2 value (reflecting the model fitting the data well) than the latter. 

