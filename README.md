# Predictive Modeling and Explainable AI Analysis of White Spot Disease in Farmed Shrimp

## Overview
White Spot Disease (WSD) is a highly contagious viral infection that can rapidly kill shrimp, crab, and prawn populations. This study uses machine learning to predict WSD prevalence in farmed shrimp in Bangladesh based on various farm features and practices, achieving an accuracy of 72.67%. By employing SHAP (SHapley Additive exPlanations), we also identified the impact of different farming practices on WSD trends, offering valuable insights for disease management.

## Key Features
- **Disease Focus**: White Spot Disease (WSD) in crustaceans
- **Geographic Focus**: Shrimp farms in Bangladesh
- **ML Accuracy**: 72.67%
- **Explainability Tool**: SHAP for insights into farming practices

## Methods
### Predictive Modeling
We implemented various machine learning algorithms to predict changes in WSD prevalence, classified into three categories:
- **Class -1**: Decrease of at least 10%
- **Class 0**: Change less than 10%
- **Class 1**: Increase of at least 10%

### Explainable AI with SHAP
Using SHAP values, we explored how specific farm features and practices influence changes in WSD prevalence, providing actionable insights.

## Data Handling
### Label Generation
Labels are generated based on the percentage change in prevalence:

```python
def generate_label(current_prev, previous_prev):
    change = 0
    if current_prev <= 0.9 * previous_prev:
        change = -1
    elif current_prev >= 1.1 * previous_prev:
        change = 1
    return change


**Results:**

**First grid search for Random Forest Classifier**
![First grid search for Random Forest Classifier](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/3ef5bbd9-bfdd-4c08-b103-afec02ed50dd)


**Second grid search for Random Forest Classifier**
![Second grid search for Random Forest Classifier](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/d0a501be-76fb-4a7f-8e9b-e8c0ca179471)

**Final grid search for Random Forest Classifier**
![Final grid search for Random Forest Classifier](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/12ee57e4-e7a1-40e4-892e-5775927431b6)


**First grid search for KNN classifier with uniform voting**
![First grid search for KNN classifier with uniform voting](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/06cf579a-dea5-481a-840b-0dedc836e473)


**Final grid search for KNN classifier with uniform voting**
![Final grid search for KNN classifier with uniform voting](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/98cccc4d-2024-4e87-8075-d75b5d3aa39a)

**First grid search for KNN classifier with distance-based voting**
![First grid search for KNN classifier with distance-based voting](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/639439a4-82d1-4d77-8c4c-5a939065a96d)


**Final grid search for KNN classifier with distance-based voting**

![Final grid search for KNN classifier with distance-based voting](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/0491898b-4378-463e-9a51-18e16ab497a0)


**First grid search for Multinomial Naive Bayes classifier**
![download](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/06447fab-4f3f-491e-8da5-e07336420ea3)


**Final grid search for Multinomial Naive Bayes classifier.**
![mean](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/36fe6c33-63b0-4305-bb88-cd5b9d2dc859)


**Shapley values for different features**

![SHAP VALUE](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/c4d7c451-208e-4130-8133-6ac89f6d920c)



![image](https://github.com/sultanrafeed/Predictive-Modeling-and-Explainable-AI-Analysis/assets/62619778/f7200bab-5f29-4fe1-98ed-ae3daaaef9a8)

