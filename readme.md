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

* Does living in a state with a high quality of life make a customer less likely to churn?

	<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Churn%20Rate%20by%20Quality%20of%20Life.png">


	* From my proportion test with a test statistic of -.40 and a P-Value .689, I was unable to reject the null hypothesis that there is not a statistically signifcant difference in churn rate for customers that live in a top quality of life states vs customers that do not. As a result, I did not use this feature in my final model.

## Modeling

For my models, I decided to prioritize recall score. This is because I wanted to reduce False Negatives. In other words, I do not want to predict a customer will not churn when they do end up in fact churning. 

In addition, I used TomekLinks and class_weight = balanced to deal with class imbalance.

### KNN
* My best KNN model ended up with a recall score of .369.

### Decision Tree
* My strongest Decision Tree model ended up with a recall score of .762.

### Random Forest
* I ended up with two strong Random Forest models. One had a recall score of .820 and the other had a recall score of .828. 

### Voting Classifier
* Using hard voting, my VotingClassifier ended up with a recall score of .754.

### XGBOOST
* Using XGBOOST, I ended up with a recall score of .754.

## Confusion Matrix of Final Model

<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Churn%20Confusion%20Matrix.png">

* In the end, I chose the Random Forest model with the  recall score of .820. I did so because it still had a very strong recall score, but it did not sacrifice F1 score in the process (.730). As you can see in the above confusion matrix, this model does not have any overpowering weaknesses.

## Conclusions

From our best model, we learned that international plan, total day charge, and customer service calls were the most important features in correctly predicting churn rate. After performing post-modeling analysis, I was able to draw these conclusions:

<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Churn%20Rate%20by%20Day%20Charge%20Amount.png">

* Customers with large day charges are far more likely to churn than customers who do not have large day charges. SyriaTel needs to reanalyze how much it charges for day minutes. This suggests that day rates are so high that frequent day users end up leaving SyriaTel .  If they end up lowering day minute rates, they could justify this reduction by raising their international rates. This would also reduce churn rate because there would be less customers that sign up for SyriaTel just for their international plan and end up leaving shortly thereafter.


<img src="https://raw.githubusercontent.com/Sonora27/syriatel_churn_classification_analysis/master/pngs/Frequency%20of%20Customer%20Service%20Calls.png">

* As the above graph shows, there is a high number of SyriaTel customers that are making frequent customer service calls. These frequent customer service callers are more likely to churn. There is some kind of service quality or billing issue that causes SyriaTel customers to call customer service so frequently. SyriaTel should investigate this further to reduce their churn rate.

## Next Steps

* Although my recall score was quite high, it came at the relative expense of my precision score. In the future, I would like to create a model that has both high recall and high precision.

* I would also like to create a model that predicts customer service calls to investigate what causes SyriaTel customers to call customer service so frequently.




