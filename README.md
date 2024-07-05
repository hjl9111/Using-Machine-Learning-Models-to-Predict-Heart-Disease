# Using Machine Learning Models to Predict Heart Disease

**Group Members: Helen Liang, Ivy Zhao, Xiaotong Zhao**

**Task: Classification (Binary)**

**Topic: Machine Learning, Heart Disease Diagnosis Prediction**

**Language: R**

## Objective

To perform predictions to identify patients with a high risk of developing heart disease through utilization of various machine learning models as well as to speed up the diagnostic process based on the medical information provided, hence allowing for early preventive measures.

## Background

The prevalence of heart disease, a general term referring to several types of heart conditions including coronary artery disease (CAD), remains one of the leading causes of death in the United States, causing about 1 in every 5 deaths and posing a significant threat to public health.

Early detection and intervention can significantly decrease the risk of heart disease, promoting better quality of life and reducing heart disease-related mortality.

## Data

The [Heart Disease](https://archive.ics.uci.edu/dataset/45/heart+disease) dataset is provided by the **UC Irvine Machine Learning Repository**, containing combined data from the Cleveland, Hungary, Switzerland, and VA Long Beach databases.

Contains data from 920 patients. Features: 14 of 76 variables are available for public use, encompassing demographic information, physiological measurements, and patient medical history. Outcome variable: `num`, converted from continuous to factor, indicating the absence or presence of heart disease. 

## Approach

#### Data Preprocessing

Removed `ca` (number of major vessels colored) and `thal` (thalassemia), features with more than half of the observations containing missing (`NA`) values. For remaining features, missing (`NA`) values in continuous variables are replaced with median, and categorical variables are replaced with mode. 

#### Feature Selection

Performed feature selection using Forward Stepwise Selection with Adjusted R<sup>2</sup> and Backward Stepwise Selection with Cp, selecting the same 10 predictors and dropping `trestbps` (resting blood pressure). Split data into 80% training and 20% testing. 

#### Exploratory Modeling 

5 five machine learning models suitable for binary classification are used for heart disease diagnosis prediction: 

- Logistic Regression
- Support Vector Machine (SVM)
- K-Nearest Neighbors (KNN)
- Random Forest
- Gradient Boosting Machine (GBM)

The models above are also implemented with k-fold cross-validation with k = 5 to tune hyperparameters to achieve optimal model performance and avoid overfitting since a small dataset is used. 

Elastic net regularization is also used along with k-fold CV for tuning in logistic regression to avoid overfitting. 

## Evaluation

7 metrics are used to evaluate model performances for all 10 models (with and without k-fold CV):

- Training error
- Testing error
- Accuracy
- Sensitivity
- Specificity
- F1 score
- AUCROC score

GBM has the highest AUCROC score of 0.903, followed by Random Forest, Logistic Regression, KNN, and SVM with AUCROC scores of 0.896, 0.884, 0.802, and 0.791, respectively.

All models achieved promising performance on classification tasks with high accuracies above 80%. All models performed well on other evaluation metrics, including F1 score, sensitivity, specificity, and AUCROC score.

## Conclusion

In combination with all 7 metrics, Random Forest outperformed other models in predicting heart disease, which might be because random forest is an ensemble method that can effectively avoid overfitting in our small dataset. 

In the future, we plan to find a larger dataset to train the model, as the key weakness of our current model is the small dataset size. Additionally, we plan to incorporate deep learning algorithms, such as neural networks, which offer automatic feature selection and can better capture non-linear relationships.\

## References

Centers for Disease Control and Prevention. (2023, May 15). Heart disease facts. Centers for Disease Control and Prevention. 

Janosi Andras, Steinbrunn William, Pfisterer MaDhias, and Detrano Robert. (1988). Heart Disease. UCI Machine Learning Repository.
