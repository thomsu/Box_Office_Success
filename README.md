# Box_Office_Success
Predict movie profitability given movie budget, genres, facebook likes and many more features using logistic regression, an assortment of trees and svm.

## Overview
The goal of this project is to identify movies for its profitability potential from facebook likes of the film and also of the main actors/actresses, IMDB votes, budget, the different genres of each film and other movie related statistics. This could be helpful for movie studios to decide whether to pick up a movie project.

## Data Source and Data Preprocessing
The dataset was downloaded from https://data.world/popculture/imdb-5000-movie-dataset. There are a total of 28 data attributes and 5043 data entries. There are many missing values in most of the features. In addition, the movies were released from different time periods from 1916 to 2016. It could be problematic when comparing movies from different eras. There are also a number of features about facebook that would not apply to movies before 2005. In order to prepare the dataset for modelling, The missings values were dropped or converted to the median value, movies released earlier than 2005 were dropped, categorical features were encoded in the right format and duplicated movies were eliminated. In the end, the dataset consists of only 1899 data points and 31 features.
