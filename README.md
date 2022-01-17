# Home Price EDA

## Examining Sale Price Data
The data gathered is from the Kaggle competition for House Prices – Advanced Regression Techniques. I only worked with the training data set to create an EDA. The home sale price has a low selling price of $34,900, and a high selling price of $755,000. The sale price data is positvely skewed with the median price of $163,000 while the mean price is $180,921.20.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/saleprice_describe.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/histogram_SalePrice.png?raw=true)

## Imputing Values
Before processing missing data, the train and test datasets were combined, with the 'SalePrice' column dropped, in order to make sure all preprocessing was performed on both datasets. Most missing home data mostly concerned house features being absent and were listed as NA. Here is a breakdown of features missing data:

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/missing_data.png?raw=true)

Imputation was performed on numerical data by assiging the median value of that specific feature to NA values. Between the train and test data, there were 11 numerical features missing data. Categorical data was imputed by evaluating if a NA was indicating a lack of a feature or incomplete features. For features with NA meaning no feature, NA were replaced by filling NA with a string, No_feature name, and incomplete features with NA were replaced with string, unknown. 

## Encoding categorical data
23 categorical data features were encoded using sklearn preprocessing module, LabelEncoder. 

## Creating new features
A new feature was created by spliting months from MoSold feature into Seasons. Another feature created was sorting years from YearBuilt into 30 year increments starting at 1870 and ending at 2010. The last feature created was combining GrLivArea, GarageArea, and TotalBsmtSF to create the feature TotalStructureArea. The correlations for the features were compared with the original features used to create them. Seasons and YearBuilt_bin features were less corelated to SalePrice than the features used to creat them. TotalStructureArea achieved a higher correlation than the individual features used to create it.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/created_features_corr.png?raw=true)

## Chosen features
Most features had almost no correlation to SalePrice. The 25% most positvely and 25% most negatively correlated features were evaluated and of those, 10 features were selected to use for predicting the test SalePrices. TotalStructureArea was the most postively correlated with SalePrice.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/chosen_features_corr.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/lmplot_TotalStructureArea.png?raw=true)

## Setting up training and test sets and standardizing
The training data was split into 30% for test and 70% train. (X_train, X_test, y_train, y_test = train_test_split(trained, y, test_size=0.3, random_state=10)
) Both StandardScaler and MinMaxScaler were used to standardize the data. Both versions of scaled data had the same root-mean-square-error (RMSE) for train and test data. (RMSE on Training set : 39115.049032319155, RMSE on Test set : 31232.59257935775)

## Model
Both versions of scaled data were run through the LinearRegression model, and the standard scaled data performed better than the minmax scaled data. The Kaggle score for the standard scaled linear regression prediction was 0.19060.
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/predictions/std_lg_houseprice_10.png?raw=true)

## Conclusion
The next iteration of utilizing a better model would include testing different linear regression regulations such as Ridge, lasso, and ElasticNet.



