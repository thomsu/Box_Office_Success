# Box_Office_Success
Predict movie profitability given movie budget, genres, facebook likes and many more features using logistic regression, an assortment of trees and SVM.

## Overview
The goal of this project is to identify movies for its profitability potential from facebook likes of the film and also of the main actors/actresses, IMDB votes, budget, the different genres of each film and other movie related statistics. This could be helpful for movie studios to decide whether to take on a movie project.

## Data Source and Data Preprocessing
The dataset was downloaded from https://data.world/popculture/imdb-5000-movie-dataset. There are a total of 28 data attributes and 5043 data entries. There are many missing values in most of the features. In addition, the movies were released from different time periods from 1916 to 2016. It could be problematic when comparing movies from different eras. There are also a number of features about facebook that would not apply to movies before 2005. In order to prepare the dataset for modeling, the missing values were dropped or converted to the median value, movies released earlier than 2005 were dropped, categorical features were encoded in the right format and duplicated movies were eliminated. In the end, the dataset consists of only 1899 data points and 31 features.

## Exploratory Data Analysis
The first series of box-plots check the features for outliers and skewness. 8 of the 10 continuous features were highly skewed with most of the outliers above 90 percentile. These features were log transformed in order to reduce skewness and outliers. The correlation heat-map shows that film genres like Sci-Fi/Action/Adventure, Thriller/Action/Adventure, Animation/Comedy are highly correlated. It also indicates that the log transformed features are now more highly correlated with each other than the original features.

## Model Building
Logistic regression is used as the baseline model. After some hyper-parameter tuning, the model has a decent precision and recall score of 0.57 and 0.66 respectively. The AUC of the logistic regression is 0.76.

![logreg confusion matrix](/images/logreg_cm.png)

Random Forest, AdaBoost, XGBoost and SVM were also fitted to the data. XGBoost is the best model amongst the group. It has a precision score of 0.60, a recall of 0.68 and an AUC of 0.78

![xgboost confusion matrix](/images/xgboost_cm.png)

## Optimizing Best Model
Although GridSearchCV failed to find the better parameter for the XGBoost model than the original, RandomizedSearchCV is performed with a broader range of hyper-parameters in 1000 iterations. The search did not yield the results that we were expecting. The final model is refitted to include data from the training and validation set and checked on the test set. It has a slightly better precision and recall score but with AUC unchanged.

 ![final confusion matrix](/images/final_cm.png)

 Finally, the features were evaluated in the final model with SHAP. SHAP takes a game theory approach to explain the output of the given model. It measures how well each feature contributes to the accuracy of the prediction.

 ![shap tree explainer](/images/shap_tree_explainer.png)

 ![shap summary](/images/shap_summary_plot.png)

 ![shap dependence plot](/images/shap_dependence_plot.png)
