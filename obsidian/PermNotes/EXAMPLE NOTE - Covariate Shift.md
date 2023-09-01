---
title: Covariate Shift
created: 2021-07-29
accessed: 2021-07-29
tags:
  - MachineLearning
related:
  - "[[Data Collection Bias]]"
  - "[[Sampling Bias]]"
---
>[!snapshot]
>Covariate shift occurs when a model is used or tested on inputs with features that have different distributions than those it was trained with.

>[!visual] Visual Aid
>![[Covariate Shift.png]]

>[!deep] Deep Dive
>Covariates are features that describe the characteristics of the input data.  Machine learning models learn to make predictions based on the features of the training data.  They do this by learning patterns within the training data. Covariate shift occurs when there is a change in the distribution of features.  There are several factors that can cause the distribution of the features to change between training and deployment/testing.  These include [[Data Collection Bias]] (i.e., training data does not accurately represent the real world usage scenario), environment changes, sensor or instrumentations differences (e.g., instrument calibration or faulty hardware), and [[Sampling Bias]] (i.e., training data is not sampled randomly). The patterns learned by the machine learning model during training may no longer hold a the real-world usage scenario where the distribution of input features has changed, thus leading to a reduction in the model's performance (i.e., accuracy and effectiveness).  
>
>There are several techniques in machine learning that can improve the model's robustness, making it less sensitive to covariate shift.

>[!Examples]
>Suppose you want to train a model to diagnose a patient's disease.  You train the model using data collected from patients in a rural community.  The features of the data include age, weight, occupation, etc.  Now, you want the trained model to diagnose patients in an urban city.  The distribution of the input features for the data obtained in the urban city is likely to be different from the distribution of the input features for the data obtained in a rural community.  Consider, for example, the change in the distribution of the occupation feature.  In a rural setting, much of the community has the occupation of a farmer, while in the urban city, very few people have this occupation. Thus, the model learned in the rural community may not be able to accurately diagnose the disease for patients in an urban city due to covariate shift.

>[!references]
>