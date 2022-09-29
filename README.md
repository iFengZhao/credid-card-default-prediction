# credid-card_default-prediction
Take home project for Credit Sesame

The Jupyter notebook in the repo documents how I built a predictive model to predict credit default using the data from https://archive-beta.ics.uci.edu/ml/datasets/default+of+credit+card+clients#Descriptive.

The notebook can be divided into the following parts
1. Data cleaning and preparation
2. Explorotary Data Analysis (some quick statistical analyses were done using SPSS)
3. Feature Engineering
4. Model Building and Hyperparameter Tuning
5. Feature Selection
6. Model Evaluation and Threshold Moving

### Model Building Process
1. Run XGBoost using original features and without tuning. This model served as the baseline.
2. Run XGBoost without tuning using original and newly generated features. Unfortunately, the newly created featues only improve the model performance slightly.
3. Conduct Bayesian Optimization using Optuna. To deal with the potential issue cause by the imbalanced data, I tested different values for scale_pos_weight to find a best value for **class-weighted XGBoost model**.
4. Since the data is imbalanced. I conducted a series experiments on the effects of different resampling methods.
- experiment 1: SMOTE oversampling on both training and testing datasets
- experiment 2: SMOTE oversampling only on training set
- experiment 3: Randomly undersampling on both training and testing datasets
- experiment 4: SMOTE Oversampling Training & Testing **After Random Undersampling**
- experiment 5: SMOTE Oversampling Training ONLY **After Random Undersampling**
 
 Note: experiment 3-5 were conducted under different sampling_strategy values ranged from 0.5 - 1.
5. After I made a decision on the final model, I filtered out half of features using RFE.

### How to further improve the predictive model?
I have multiple interviews and other take home projects to work on, so I have limited time to work on this interesting project.
If I had more time, I'd try more things to improve the model

1. Generate more features: e.g., create interaction variables among important categorical and numerical variables
2. More finetuned feature selection (e.g., RFE) and Hyperparameter Tuning
3. Try other models such as DNN and DCN.
4. Access to additional features such as demographic variables, credit score, and geo info.
5. Learn from domain knowledge experts
6. Learn from recommendation system. Develop different approaches for new customers and old customers
7. Consider building both online and offline models for default prediction
