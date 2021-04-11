# Comparison-and-Analysis-of-different-regression-techniques-to-predict-Housing-Prices-
The objective is to first analyze the data using visualization tools and then applying different regression models in the given dataset, 
starting from basic regression models to more advanced ensembles, and observe how the error varies for each model.

A train dataset on Housing Prices has been taken from kaggle. I have uploaded the csv file alongwith.

In the project, after loading the data, it has been preprocessed by primarily dropping all the 'string' data as strings cannot be studied mathematically.
After which, the data has split for training and testing and cleaning using imputation.

This was followed by Data Visualisation where the correation was mapped to see how the numeric features are correlated with SalePrice. 

Important linear correlation between features and SalePirce are:
Features correlated with SalePrice are OverallQual(0.79), YearBuilt(0.52), YearRemodAdd(0.51), TotalBsmtSF(0.61), 1stFlrSF(0.61), GrLivArea(0.71), 
                                       FullBath(0.56), TotRmsAbvGrd(0.53), GarageCars(0.64), GarageArea(0.62)
Features not correlated with SalePrice are MSSubClass(-0.084), OverallCond(-0.078), BsmtFinSF1(-0.011), LowQualFinSF(-0.026), BsmtHalfBath(-0.017), 
                                       KitchenAbvGrd(-0.14), EnclosedPorch(-0.13), MiscVal(-0.021), YrSold(-0.029)

Below are few of the multicollinear features based on correlation matrix.
Features correlated with OverallQual are YearBuilt(0.57), YearRemodAdd(0.55), TotalBsmtSF(0.54), GrLivArea(0.59), FullBath(0.55), GarageYrBuilt(0.55), 
                                         GarageCars(0.6), GarageArea(0.56)
Features correlated with YearBuilt are YearRemodAdd(0.59), GarageYrBuilt(0.83), GarageCars(0.54)
Features correlated with YearRemodAdd is GarageYrBuilt(0.64)
Features correlated with BsmtFinSF1 are TotalBsmtSF(0.52), BsmtFullBath(0.65)
Features correlated with TotalBsmtSF is 1stFlrSF(0.82)
Features correlated with 1stFlrSF is GrLivArea(0.57)
Features correlated with 2stFlrSF are GrLivArea(0.69), HalfBath(0.61), BedroomAbvGr(0.5), TotRmsAbvGrd(0.62)
Features correlated with GrLivArea are FullBath(0.63), BedroomAbvGr(0.52), TotRmsAbvGrd(0.83)
Features correlated with FullBathc is TotRmsAbvGrd(0.55)
Features correlated with BedroomAbvGr is TotRmsAbvGrd(0.68)
Features correlated with GarageYrBuilt are GarageCars(0.59), GarageArea(0.56)
Features correlated with GarageCars is GarageArea(0.88)

The above correlations were then visualised.

Minimum and maximum threshold were applied to remove the outliers from all the numeric features in training data.
Every record less than min threshold and more than max threshold would be deleted.
Please note that wheneever possible its better idea to use outliers for analysis and prediction, it makes the model more robust. Because in real world we will always encounter the outliers!

There are two ways the outliers were deleted here.
One is 'inline deleting'. In this approach we found the outlier and deleted it straight away. This method results in deleting more number of rows. Since we are using min and max percentile threshold, everytime we delete the row, min max threshold for next feature will be calculated based on available number of records.
If we dont want do 'inline deleting' then we can collect the indexes of the outliers in 'outliers' list (it may contain duplicate indexes). And at the end the unique outlier indexes from this list would be obtained and all the rows simultaniously would be deleted. Since in this approach we are deleting all the outliers simultaniously min max threshold for all the features caluclated using same amount of data.
We can enable/diable inline deleting in below cell as and when required. In case of 'inline deleting' 'outliers' list wont contain any duplicate records.

Finally, coming to the regression modeling.
The evaluation metric use is "mean_absolute_error".

Following are the regression models tested in this project:
1. Linear Regression
2. Support Vector Regression
3. Decision Tree Algorithm based Reression
4. Random Forest Algorithm based Regression
5. XGBoost Algorithm based Regression
6. LightGBM Algorithm based Regression
7. Ridge Regression
8. Bayesian Ridge Regression
9. Ensemble: Stacked Regression and Grid Search
10. Ensemble: Averaging

The last ensemble based on averaging has been done on four of the algorithms which were
Ensemble - Stacked Regression and GridSearch (error=15841.06899614726)
LightGBM algorithm (error=16841.24460207058)
XGBoost algorithm (error=16502.604837328767)
Random Forest Algorithm (error=17982.626423430887) since they give the the least error amongst others.

The prediction by average the four above ensembles has been taken as the final result.
