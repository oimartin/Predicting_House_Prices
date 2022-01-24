# Home Price EDA

## Examining Sale Price Data
The data gathered is from the Kaggle competition for House Prices – Advanced Regression Techniques. I only worked with the training data set to create an EDA. The home sale price has a low selling price of $34,900, and a high selling price of $755,000. The sale price data is positvely skewed with the median price of $163,000 while the mean price is $180,921.20.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/saleprice_describe.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/histogram_SalePrice.png?raw=true)

## Imputing Values
The train 'SalePrice' was dropped and saved as y. Most missing home data concerned house features being absent and were listed as NA. Here is a breakdown of features missing data:

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/missing_data.png?raw=true)

Imputation was performed on numerical data by assiging the median value of that specific feature to NA values. Between the train and test data, there were 11 numerical features missing data. Categorical data was imputed by evaluating if a NA was indicating a lack of a feature or incomplete features. For features with NA meaning no feature, NA were replaced by filling NA with a string, No_feature name, and incomplete features with NA were replaced with string, unknown. Imputation was done to the train data first, then the test data. 

## Encoding categorical data
Ordinal features were encoded manually, and remaining features were encoded with the Pandas get_dummies feature.

## Creating new features
A new feature created was combining above ground living area, garage area, and total basement square foot to create the feature TotalStructureArea. Another feature was Baths, which combined all columns related to bathrooms. The other new feature was the combination of square footage of the first floor and total basement square footage.The correlations for the features were compared with the original features used to create them. The columns used create the features were then dropped from both the train and test data sets.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/all_num_corr.png?raw=true)

## Chosen features
The newly created features generally did create improved correlations between SalePrice. 

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/new_features_corr.png?raw=true)

After encoding the ordinal and remaining categorical features, features were chosen if they had a correlation with SalePrice of 0.5 or higher and -0.5 or lower.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/highly_correlated_feat_corr.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/lmplot_TotalStructureArea.png?raw=true)

## Setting up training and test sets and standardizing
The training data was split into 30% for test and 70% train. (X_train, X_test, y_train, y_test = train_test_split(trained, y, test_size=0.3, random_state=10)
) Both StandardScaler and MinMaxScaler were used to standardize the data. Linear regression, ridge, lasso and ElasticNet were used to evaluate the data. The best performace was  standard scaled data with ElasticNet model (RMSE = 39504). 

## Model
Linear regression, ridge, lasso and ElasticNet were used to evaluate the data. The best performace was  standard scaled data with ElasticNet model (RMSE = 39504). The models I ran did worse than the first model I submitted to Kaggle. Most of the models I submitted this week had a score around 0.43. I believe that the model was overfitted to the training data.
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/predictions/recent_sub_1_23.png?raw=true)

## Management Research Question
This home sale prices model could be helpful for listing agents deciding at what price to first list a house depending on a variety of home factors. Similarly, this model could help consumers on the otherside of the deal to determine if the sale price is appropriate. Cities or municipalities may also be interested in better determing home sale price in order to best determine property taxes to levy on properties.

## Conclusion
A better analysis of the models used needs to be done in order to handle overfitting the training data.


