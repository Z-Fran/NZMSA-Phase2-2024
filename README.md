# NZMSA-Phase2-2024 


## Part1 Sales Forecasting: 1_Analysis_and_Preprocessing

### 1. Fina all variables
- Merge three dataframes into one by matching store id.

### 2. Clean data
- Deal with missing values
  - **Filling missing values** of markdowns with 0 is better than deleting them.
  - `0` is meaningful because it can presents there is no markdown on that date.

- Deal with outliers
  - Find outliers by **Boxplot** and **IQR** method.
  - Deal with outliers of unemployment by replacing with nearest values.

### 3. Feature Engineering
- Map `Type` and `IsHoiday` to numeric features.
- Split Date into Year, Month and Day so that it will be numeric.
- Use Dept and Size **create new meaningful features** according to correlation anlysis:
  - `Dept_num`: departments quantity of a store may affects sales.
  - `Size_per_dept`: average size of departments of a store may affects sales.

### 4. EDA with Visualization with Power BI
- Use pie charts to visualize the proportion of each Type, Year, Month, and IsHoliday.
    - the distribution of Year and Month are balanced
    - the distribution of Type and IsHoliday is not balanced, which may affect the model performance.
- Visualize sales varying with dates of a specific Dept of a specific Store by filtter of Power BI.
    - sales data has a contrary relationship with temperature.
    - sales data has not obvious relationship with fuel prices and unemployment.

### 5. Correlation analysis
-  Size(0.24), Dept(0.15) and Type(-0.18) have stonger correation with Weekly_Sales.
-  New feature Dept_num(0.16) and Size_per_dept (0.24) have stonger correation with Weekly_Sales.
-  The data of `Type=0` and `Type=1` are similar, but they are different from `Type=2`. We can try reclassifying them into two types. 

## Part1 Sales Forecasting: 2_Train_and_Evalution

### 1. Split dataset
- Use high correlation columns in part 1 correlation analysis
- Fix zero values of Weekly_Sales.
- Split dataset acoording to date. train:test = 4:1.
  
### 2. Train and Test models
- Train LinearRegression, KNN, RandomForest, and get scores on test dataset.

### 3. Evalution
- Compare MAE, MAPE, RMSE, R2 metrics.
  - Performance of KNN and RandomForest are similar and they are vey higher than LinearRegresiion

### 4. Ensemble Learning
- Use KNN and RandomForest to build a VotingRegressor which has a better performance.

### 5. Visualize predicted data
- Using all columns to train have a better curve fitting

## Part2 Image Classification: 3_Deep_Learning

### 1. Data preprocessing & augmentation
- RandomResizedCrop: and RandomHorizontalFlip are useful.
- RandomRotation, RandomVerticalFlip and Normalizea are unuseful.

### 2.Define the model
- ResNet
  - Classic CNN network.
  - Very easy to achieve 90%+ score on this dataset.
- ViT
  - Use transformer framework on vision tasks.
  - Training more slowly than ResNet.

### 3. Pipelines
- Design unified pipelines to train model and test on test dataset.

### 4. Train model and hyperparameters tuning
- ResNet
  - larger framework is not useful.
  - Adam and StepLR is better.
  - larger learning rate is batter (1e-3 > 1e-4).
- ViT
  - Because of slow convergence speed, MultiStepLr can set a large learning rate in the beginning to accelarate training.
  
### 5. Evaluation
  - Compare ResNet and ViT with following metrics:
    - Precision
    - Recall
    - F1 score
    - Overall Accuracy
    - ROC curve
    - AUC
    - Confusion matrix
- Accuracy and AUC of Resnet are higher than ViT.
- Both of models are more likely to confuse airplane and dog.

### Ensemble Learning
- Using Ensemble Learning method, use Resnet and ViT vote for the pridiction result.
- Weights of them is Resnet:ViT = 3:1.
