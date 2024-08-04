## Summary

### 1. Split dataset
- Use high correlation columns in part 1 correlation analysis
- Fix zero values of Weekly_Sales.
- Split dataset acoording to date. train:test = 4:1.
  
### 2. Train and Test models
- Train LinearRegression, KNN, RandomForest, and get scores on test dataset.

### 3. Evalution
- Compare MAE, MAPE, RMSE, R2 metrics.
  - Performance of KNN and RandomForest are similar and they are vey higher than LinearRegresiion

### 4. Emsemble Learning
- Use KNN and RandomForest to build a VotingRegressor which has a better Performance.

### 5. Visualize predicted data
- Using all columns to train have a better curve fitting
