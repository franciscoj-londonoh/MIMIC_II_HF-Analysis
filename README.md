# MIMIC-III Database: Heart Failure subtypes analysis
**Capstone Project**

**Data Scientist Nanodegree**

**Author: Francisco J. Londono**


## Introduction
Cardiovascular diseases are the leading cause of death worldwide affecting millions of each year. Among these, heart failure is becoming more prevalent, especially in an ageing population impacted by poor lifestyles (poor eating habits, sedentarism, smoking, pollution, etc.).

Heart failure is a complex, multifactorial disease process rather than a specific disease thus treatment has proven to be a challenging task as well. Even diagnosis is not a straightforward process, and differentiate between two defined subtypes of heart failure has proven to be a challenge as well. Indeed, it has been recognized two heart failure subtypes regarding affected cardiac function: systolic heart failure and diastolic heart failure. The fundamental measurement to diagnose one heart failure subtype is ejection fraction, i.e., the percentage of blood ejected after each systole. If the ejection fraction is lower than 50%, this is referred as heart failure with reduced ejection fraction, and it is related to a diminished systolic function. If ejection fraction is higher than 50%, this is referred as heart failure with preserved ejection fraction, and it is related to a diminished diastolic function of the heart. Even if this denomination is useful to support diagnosis and potential treatment, and in fact there is a prevalence of one of these two conditions, the complexity of the disease involves a deterioration of both functions: systolic and diastolic, impacting potential treatment as well.

The population more affected by heart failure is also, in general, differentiated by subtype. Systolic heart failure is more common in old men with hypertension, diabetes, and other comorbidities. Diastolic heart failure is more common in older women. In terms, of treatment, systolic heart failure has a proven route of action and drugs that help patients with symptoms and to improve the progression of the disease. In contrast, diastolic heart failure lacks a proven effective treatment, with the aggravating factor that is becoming more and more prevalent in the world’s ageing population. Systolic failure treatment has been tested in diastolic failure patients but with less optimal results. 

## [Part 1](https://github.com/franciscoj-londonoh/MIMIC_II_HF-Analysis/blob/main/Part1_MIMICdatabaseEDA.ipynb): MIMIC-III database General Exploration Data Analysis
In this context, the MIMIC-III database can provide a unique insight into the impact of heart failure and its subtypes in the daily routine of an emergency care unit, giving a more real idea of the type of population affected by the disease, the type of used treatment, and the final outcome of patients after an emergency related to the disease evolution. Thus, following there is an analysis of the MIMIC-III database, starting with an overview of the most common diagnosis of patients, then the analysis focuses on cardiovascular diseases related directly with heart failure, highlighting the population with a systolic and a diastolic heart failure diagnosis, and comparing treatment followed at the ICU. 

![EDA_HF](https://github.com/franciscoj-londonoh/MIMIC_II_HF-Analysis/blob/main/Images/3DiagnosisHF.png)

## [Part 2](https://github.com/franciscoj-londonoh/MIMIC_II_HF-Analysis/blob/main/Part2_SubsampleDataAnalysisHF.ipynb): Subsample Data Analysis (Heart Failure)
The second part of the analysis focuses on the systolic and diastolic heart failure patients data, including some common lab exams and physiological measurements, such as hemodynamics, arterial blood gas (ABG), Hematology, Chemistry, Fluids - Other (Not In Use), Blood Products/Colloids, Labs, Cardiovascular (Pacer Data), Tandem Heart, non-invasive cardiac output monitor (NICOM). Hemodynamic measurements are the most relevant measurements to determine heart failure subtype but a deep analysis of the available data in the database showed that there were too few data points, or patients with a complete dataset, affecting the potential modeling of the data. Thus, other complementary measurements were included to build a more complete DataFrame. 

## [Part 3](https://github.com/franciscoj-londonoh/MIMIC_II_HF-Analysis/blob/main/Part3_DataModelling.ipynb): Data Modelling
Finally, on the third part of the analysis, the built DataFrame was used to propose a model to classify the two heart failure subtypes based on the available physiological measurements. To perform this modelling, a pipeline was created, first imputing the data using a KNN imputer, and then a Random Forest Classifier is implemented, and a cross validation scheme used to train the model, obtaining an accuracy and a F1 score of around 98% to classify heart failure subtypes. An additional analysis on the sample population shows that both categories (systolic and diastolic heart failure) are balanced in the DataFrame, and that imputed values are around only 3.3% of the total data.

![MIMIC_HF_Modelling](https://github.com/franciscoj-londonoh/MIMIC_II_HF-Analysis/blob/main/Images/6Features.png)

## Conclusions
The initial step of this database assessment includes a general demographic data analysis, in which age and gender show interesting patterns, for example the fact that the highest percentage of ICU patients in this MIMIC database are older males. Causality for this distribution needs a deeper analysis. Then, diagnosis is selected for analysis, building a graphical description of the most common diseases for ICU entry. Cardiovascular diseases are among the top causes for ICU entry in this population, which is consistent with the impact of CVDs worldwide. Thus, an analysis in CVD patients is performed, specifically those affected by Heart Failure subtypes: Systolic and Diastolic Heart Failure. A demographic description of patients diagnosed with either one of both subtypes show that even if older individuals are more impacted by these pathological conditions, there is a gender differentiation between them. Previous studies are consistent with these differences and in the fact that treatment should be specific. However, the database shows that the treatment for each diagnosis is almost the same at ICU level. Another differentiation level is the death rates that show around a 7% higher chance of dying at the ICU for patients with a Diastolic Hearth Failure diagnosis. Further analysis of the subsample population from the MIMIC database containing patients with a diagnosis of Diastolic and Systolic Heart Failure is performed in the following Part 2.

A fundamental step to analyze the MIMIC database in the context of Heart Failure patients is to know the related available data. Making use of the lab exams and physiological measurements done at the ICU, it could be interesting to determine if there is relevant information about Heart Failure patients and specific differences between Heart Failure subtypes. Heart Failure diagnosis is done by hemodynamic analysis of medical imaging and extracted parameters. Thus, the first measurements taken for the analysis are the ones indicated with the tag "Hemodynamics". A DataFrame of Systolic Failure patients is prepared but the limited number of patients with values forces to include other measurements such as arterial blood gas (ABG) data, hematology, chemistry, fluids, blood products/colloids, labs, cardiovascular, tandem heart and non-invasive cardiac output monitor (NICOM). Then, a subsample of patients with Systolic and Diastolic Failure is selected, prepared and cleaned to build a DataFrame, including a label with the correspondent diagnosis, for modeling the data, experimenting if there is a model that can use the available data to identify and differentiate patients with Systolic Heart Failure and with Diastolic Heart Failure. The DataFrame is saved as a pickle file to be used in Part 3: Data Modeling.

A Classification model is proposed to differentiate Heart Failure subtypes. Specifically, a Random Forest Classifier implement within a pipeline that includes an imputation step. The general accuracy and F1 score of the model show values above 98%. Thus, an analysis of the feature importance for the model is also included, as an analysis of the imputation data process to assess the final results in context. The final implemented model accomplishes the classification task proposed.

The report publication can be found at: 
https://franciscoj-londonoh.medium.com/mimic-iii-database-heart-failure-sub-types-analysis-52fcc503dcd6
