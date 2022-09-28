# Surprise Housing Assignment
> A US-based housing company named `Surprise Housing` has decided to enter the `Australian market`. The company uses data analytics to purchase houses at a price below their actual values and flip them on at a higher price. For the same purpose, the company has collected a data set from the sale of houses in Australia. The company is looking at prospective properties to buy to enter the market.


## General Information
Python libraries used: NumPy, Pandas, Matplotlib, Seaborn, Scikit-Learn, Warnings
- ### Analysis steps are as follows:
* Step 1: Data Reading
* Step 2: Data Preparation
  * Step 2.1: Null-value Inspection
  * Step 2.2: Drop Irrelevant Features and Derive New Features
  * Step 2.3: Type Conversion
  * Step 2.4: Data Imputation
  * Step 2.5: Data Transformation
* Step 3: Exploratory Data Analysis (EDA)
  * Step 3.1: Categorical Data Analysis
  * Step 3.2: Numerical Data Analysis
* Step 4: Model Building
  * Step 4.1: Dummy Encoding
  * Step 4.2: Test-Train Splitting
  * Step 4.3: Rescaling Features
  * Step 4.4: Ridge Regression
  * Step 4.5: LASSO Regression
* Step 5: Residual Analysis on Train Data
* Step 6: Model Prediction on Test Data
* Step 7: Model Comparison and Conclusion

## Observations
- ### Observations based on Exploratory Data Analysis (EDA)
The demand is the maximum for following feature values:

**Categorical Feature**

01. `MSSubClass` category `20`.     
02. `MSZoning` category `RL`.    
03. `Street` category `Pave`.
04. `Alley` category `No`.
05. `LotShape` category `Reg`.
06. `LandContour` category `Lvl`.
07. `Utilities` category `Allpub`.
08. `LotConfig` category `Inside`.
09. `LandSlope` category `Gtl`.
10. `Neighborhood` category `NAmes`.
11. `Condition1` category `Norm`.
12. `Condition2` category `Norm`.
13. `BldgType` category `1Fam'.
14. `HouseStyle` category `1Story`.
15. `OverallQual` category `5`.
16. `OverallCond` category `5`.
17. `RoofStyle` category `Gable`.
18. `RoofMatl` category `CompShg`.
19. `Exterior1st` category `VinylSd`.
20. `Exterior2nd` category `VinylSd`.
21. `MasVnrType` category `None`.
22. `ExterQual` category `TA`.
23. `ExterCond` category `TA`.
24. `Foundation` category `PConc`.
25. `BsmtQual` category `TA`.
26. `BsmtCond` category `TA`.
27. `BsmtExposure` category `No`.
28. `BsmtFinType1` category `Unf`.
29. `BsmtFinType2` category `Unf`.
30. `Heating` category `GasA`.
31. `HeatingQC` category `Ex`.
32. `CentralAir` category `Y`.
33. `Electrical` category `SBrkr`.
34. `BsmtFullBath` category `0`.
35. `BsmtHalfBath` category `0`.
36. `FullBath` category `2`.
37. `HalfBath` category `0`.
38. `BedroomAbvGr` category `3`.
39. `KitchenAbvGr` category `1`.
40. `KitchenQual` category `TA`.
41. `TotRmsAbvGrd` category `6`.
42. `Functional` category `Typ`.
43. `Fireplaces` category `0`.
44. `FireplaceQu` category `No`
45. `GarageType` category `Attchd`
46. `GarageFinish` category `Unf`.
47. `GarageCars` category `2`.
48. `GarageQual` category `TA`.
49. `GarageCond` category `TA`.
50. `PavedDrive` category `Y`.
51. `PoolQC` category `No`.
52. `Fence` category `No`.
53. `MiscFeature` category `No`.
54. `SaleType` category `WD`.
55. `SaleCondition` category `Normal`.

**Numerical Feature**

01. `LotFrontage` in between `62 and 78 units` approximately.
02. `LotArea` in between `8000 and 11000 units` approximately.
03. `MasVnrArea` in between `0 and 100 units` approximately. 
04. `BsmtFinSF1` in between `0 and 250 units`.
05. `BsmtFinSF2` in between `0 and 80 units` approximately.
06. `BsmtUnfSF` in between `0 and 240 units` approximately.
07. `TotalBsmtSF` in between `700 and 1000 units` approximately.
08. `1stFlrSF` in between `0 and 900 units` approximately.
09. `2ndFlrSF` in between `0 and 210 units` approximately.
10. `LowQualFinSF` in between `0 and 280 units` approximately. 
11. `GrLivArea` in between `0 and 1800 units` approximately.
12. `GarageArea` in between `350 and 500 units` approximately.
13. `WoodDeckSF` in between `0 and 60 units` approximately.
14. `OpenPorchSF` in between `0 and 35 units` approximately.
15. `EnclosedPorch` in between `0 and 35 units` approximately. 
16. `ScreenPorch` in between `0 and 30 units` approximately.
17. `SalePrice` in between `0 and 12.5 units (in log scale)` approximately. 
18. `PropertyAge` in between `0 and 35 units` approximately. 
19. `RemodelingAge` in between `0 and 35 units` approximately. 

**Following Numerical Features are highly correlated:**

01. `SalePrice` and `TotalBsmtSF` (positive correlation).
02. `SalePrice` and `1stFlrSF` (positive correlation).
03. `SalePrice` and `GrLivArea` (positive correlation).
04. `SalePrice` and `GarageArea` (positive correlation).
05. `SalePrice` and `PropertyAge` (negative correlation).
06. `PropertyAge` and `RemodelingAge` (positive correlation).
07. `1stFlrSF` and `TotalBsmtSF` (positive correlation).

- ### Observations based on Ridge and LASSO regressions are as follows:
01. Ridge regression 
    - The optimum value of alpha = 6.0
    - Train data: $R^2$ = 0.94 
    - Test data: $R^2$ = 0.89
    - Top 15 features (in descending order) are: `OverallQual_8`, `OverallCond_9`, `BsmtFinSF1`, `2ndFlrSF`, `Neighborhood_Crawfor`, `GarageQual_Gd`, `Neighborhood_StoneBr`, `BsmtUnfSF`, `SaleType_ConLD`, `Neighborhood_Somerst`, `GarageCars_4`, `Neighborhood_ClearCr`, `KitchenAbvGr_1`, and `OverallCond_8`.        


02. LASSO regression 
    - The optimum value of alpha = 0.0001
    - Train data: $R^2$ = 0.95
    - Test data: $R^2$ = 0.85
    - Top 15 features (in descending order) are: `OverallQual_9`, `Condition2_PosA`, `SaleType_ConLD`, `OverallCond_9`, `OverallQual_8`, `BsmtFullBath_3`, `BsmtFullBath_2`, `TotRmsAbvGrd_14`, `GarageCars_4`, `GarageQual_Gd`, `Neighborhood_Crawfor`, `Neighborhood_StoneBr`, `KitchenAbvGr_1`, `OverallCond_8`, and `2ndFlrSF`.

- LASSO removes 91 features, but at a significant cost. That is a significant drop in model accuracy. Ridge regression therefore provides the best prediction accuracy for the given model.

### Contact
Created by [@dmondal1994] - feel free to contact me!
