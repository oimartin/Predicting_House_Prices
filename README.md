# Home Price EDA

## Examining Sale Price Data
The data gathered is from the Kaggle competition for House Prices – Advanced Regression Techniques. I only worked with the training data set to create an EDA. The home sale price has a low selling price of $34,900, and a high selling price of $755,000. The sale price data is skewed to the left with the median price of $163,000 while the mean price is $180,921.20.

![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/saleprice_describe.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/histogram_SalePrice.png?raw=true)

Missing home data was more related to a house not having a certain feature like a pool, so the PoolQC or pool quality was listed as NA. Most home features did not have any missing data, but about 20 features have NAs and lack a certain feature. PoolQC, MiscFeature, Alley, and Fence features had the most missing data or most house do not have pool, miscellaneous feature or a fence.
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/missing_data.png?raw=true)

Analysis before standardizing data shows correlations between home sale price and the following features: a negative correlation between KitchenAbvGr, a positive correlation between OverallQual, a positive correlation between TotRmsAbvGrd, a positive correlation for good and excellent ExterQual, a positive correlation for finished GarageFinish, a negative correlation for typical ExterQual, and unfinished GarageFinish. These features were selected because they, initially, showed some stronger affects on the SalePrice data. 


![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/lmplot_KitchenAbvGr.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/lmplot_OverallQual.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/boxplot_TotRmsAbvGrd.png?raw=true)


![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/neg_exterqual_garagefinish.png?raw=true)
![alt text](https://github.com/oimartin/Predicting_House_Prices/blob/main/figures/pos_garagefinish_exterqual.png?raw=true)

The training data was then grouped by the following features: GarageFinish,OverallQual, TotRmsAbvGrd, and KitchenAbvGr, and the following aggregate functions of SalePrice were used: min, max, mean, and median. The data was separately fitted and transformed with the StandardScaler and MinMaxScaler from scikitlearn and can be viewed in the jupyter notebook predicting_home_prices. 
