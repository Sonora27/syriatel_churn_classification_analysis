# Predicting Customer Churn for SyriaTel

Jose Ramirez

Sources: [Kaggle](https://www.kaggle.com/becksddf/churn-in-telecoms-dataset?select=bigml_59c28831336c6604c800002a.csv)

## Business Question

SyriaTel has a significant issue with customer churn, which means that a customer will stop doing business with SyriaTel in the very near future. Major cellphone companies have churn rates that rarely exceed 2% in modern times, yet SyriaTel's churn rate is over 14%! 

I have been contracted by SyriaTel to create a model that predicts customer churn in order for them to improve their ability to retain their customers.

## Repository Structure
* pngs -- folder that contains visualizations that were vital to my analysis
* jupyter_notebooks - contain three notebooks: EDA_STAT_TEST, knn_modeling, dt_rf_modeling
* README.md
* presentation.pdf -- contains pdf version of project presentation

## Data

For my analysis, I utilized a dataset that was given to me by SyriaTel on their customer churn data. This dataset had 3,333 observations and 20 features. After performing data cleaning, statistical testing, and modeling, I was able to pair this down to 13 features.

## Statistical Tests

After performing exploratory data analysis, there were a few hypotheses I wanted to test:

* Are customers that have an international plan more likely to churn than customers who do not?

	<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Churn%20Rate%20by%20International%20Plan.png">

	* From my proportion test with a test statistic of 15.00 and a p-value of 7.15x10^-51, I can reject the null hypothesis that the proportions are equal for people that have an international plan and those who do not. As a result, I can conclude that international plan will be an important feature for modeling.

* Is area code an important feature in predicting customer churn?

	<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Churn%20Rate%20by%20Area%20Code.png">

	* From my one-way ANOVA test with a F-statistic of .089 and a P-value of .915 means that I have failed to reject the null hypothesis that the difference in churn rate for each area code is not statistically significant. As a result, I determined that area code is not an important feature and I did not use it for modeling.








