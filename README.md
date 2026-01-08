# Customer churn prediction with machine learning and economic decision modeling

> ## Overview

This project builds a customer churn prediction system and, critically, connects model outputs to profit-maximizing business decisions

Rather than stopping at predictive accuracy, the project integrates an economic expected-value model to determine the optimal decision threshold for deploying retention incentives. This ensures the model is evaluated and used in a way that aligns with real-world business objectives

> ## Business Problem

+ **Context**: Cell2Cell, a U.S. telecommunications provider, faces a high annual churn rate, leading to substantial recurring revenue loss

+ **Action lever**: The company can offer targeted retention incentives (e.g., discounts) to at-risk customers, but incentives incur direct costs

+ **Objective**:

        1.  Estimate each customer’s probability of churn

        2.  Decide who should receive incentives to maximize expected profit, not just predictive accuracy

> ## Data

+ **Source**: Cell2Cell churn dataset (KDD Cup 2000, via [Kaggle](https://www.kaggle.com/datasets/jpacse/datasets-for-churn-telecom) )

+ **Size**: 71,047 customers, 58 features

+ **Challenges**: Missing data, invalid data, outliers, class imbalance (Non-churn: 71%, Churn: 29%)

> ## Methods and Techniques

+ **Data preprocessing**: Winsorization to treat outliers, group-based imputation, one-hot encoding, scaling

+ **Feature selection**: Mutual Information

+ **Class imbalance handling**: SMOTE oversampling

+ **Model**: Compare KNN, Random forest, Logistic regression and Naive Bayes' performance and choose one with highest AUC

+ **Hyperparameter tuning**: Randomized search with Cross validation

+ **Evaluation**: ROC-AUC for threshold-independent model comparison

+ **Decision optimization**: Expected-value-based economic model

> ## Result

+ **Predictive performance**: Random Forest achieves ROC-AUC ≈ 0.65

+ **Economic impact**: additional $366,679 in expected value relative to a no-intervention baseline (under stated cost and revenue assumptions)

+ **Optimal decision threshold**: t=0.367 (selected by maximizing an objective function TPR − 1.093⋅FPR)

+ **Operational trade-off at optimal threshold**:  Precision = 0.38, Recall = 0.60 (intentional prioritize recall due to higher cost of missed churners)

+ **Flexibility**: Economic value is fully parameterized and can be recalculated for different incentive costs, customer lifetime values, or incentive effectiveness rates
