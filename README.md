**Predictive Modeling and Explainable AI Analysis of Farm Features and Practices Impacting
White Spot Disease Prevalence in Farmed Shrimps in Bangladesh**

Abstract—White Spot Disease (WSD) is a highly contagious
viral infection that can lead to the rapid death of crustacean
(shrimp, crab, prawn, etc.) populations. In our study, we implemented
different machine-learning tools and algorithms to
predict whether the prevalence of WSD in farmed shrimp will
increase, decrease, or remain unchanged based on the features
of shrimp farms in Bangladesh and their associated farming
practices. We achieved an accuracy of 72.67%.


Furthermore, we used SHAP (SHapley Additive exPlanations)
explainable AI to discover the effects of different farm features
and practices on the change in prevalence, offering valuable
insights into various trends in the data. Hence, this research
has the potential to help minimize the prevalence of White Spot
Disease in farmed shrimps in Bangladesh.



We classify changes in prevalence into three distinct classes:
• Class -1: There was a decrease of at least 10%
• Class 0: Change in prevalence was less than 10%
• Class 1: There was an increase of at least 10%

**Algorithm 1 Label generation**
𝑐𝑢𝑟𝑟𝑒𝑛𝑡 𝑝𝑟𝑒𝑣 ← the current prevalence
𝑝𝑟𝑒𝑣𝑖𝑜𝑢𝑠 𝑝𝑟𝑒𝑣 ← the previous prevalence
𝑐ℎ𝑎𝑛𝑔𝑒 ← 0
if 𝑐𝑢𝑟𝑟𝑒𝑛𝑡 𝑝𝑟𝑒𝑣 ≤ 0.9 · 𝑝𝑟𝑒𝑣𝑖𝑜𝑢𝑠 𝑝𝑟𝑒𝑣 then
𝑐ℎ𝑎𝑛𝑔𝑒 ← −1
else if 𝑐𝑢𝑟𝑟𝑒𝑛𝑡 𝑝𝑟𝑒𝑣 ≥ 1.1 · 𝑝𝑟𝑒𝑣𝑖𝑜𝑢𝑠 𝑝𝑟𝑒𝑣 then
𝑐ℎ𝑎𝑛𝑔𝑒 ← 1
else
𝑐ℎ𝑎𝑛𝑔𝑒 ← 0
end if

**Handling missing values**
Analyzing the dataset, we find that the only columns missing
values are “Temperature”, “pH”, and “Salinity.”
Since they are all continuous variables from environment
variables, we could use the mean of all the values in the
columns. However, the mean across all values is likely less
accurate than that across all the values for the corresponding
zone in which the farm with the missing value belongs.
Hence, instead of a “global mean,” we used a “zonal
mean” to fill the missing values. Algorithm 2 demonstrates
our process of handling null values for continuous features
with missing values.

**Algorithm 2 Fill Nulls with Zonal Mean**
function FILLNULLSWITHZONALMEAN(𝑑𝑓 , 𝑐𝑜𝑙)
𝑔𝑟𝑜𝑢𝑝𝑒𝑑 𝑧𝑜𝑛𝑒𝑠 ← 𝑑𝑓 .groupby(′𝑍𝑜𝑛𝑒′)
𝑧𝑜𝑛𝑎𝑙 𝑚𝑒𝑎𝑛 ←
𝑔𝑟𝑜𝑢𝑝𝑒𝑑 𝑧𝑜𝑛𝑒𝑠[𝑐𝑜𝑙].transform(′𝑚𝑒𝑎𝑛′)
𝑑𝑓 [𝑐𝑜𝑙].fillna(𝑧𝑜𝑛𝑎𝑙 𝑚𝑒𝑎𝑛, inplace = True)
return 𝑑𝑓
end function

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

