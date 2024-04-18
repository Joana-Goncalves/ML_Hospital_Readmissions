# Ready to be discharged: predicting hospital readmissions

## Overview

This project addresses the challenge of hospital readmissions, focusing on diabetic patients, a significant issue that has a great impact on healthcare costs. It was developed for the "Machine Learning" course from the MSc in Data Science and Advanced Analytics, at NOVA IMS. <br>
The project resolved on developing two models: 
<li><b>Binary Classification</b>: Create a classification model that can accurately predict if a patient will be readmitted to the hospital within 30 days of being discharged. </li>
<li><b>Multiclass Classification</b>: The second objective is to develop a multiclass classifier that predicts the timeframe of a patient’s readmission, with the classes being “No”, “<30 days”, “>30 days”.</li>
 

## Python Packages Used
<li><b>Data Manipulation</b>: pandas, numpy, math, scipy</li>
<li><b>Data Visualization</b>: matplotlib, missingno, seaborn</li>
<li><b>Machine Learning</b>: sklearn, boruta, imblearn</li>
<li><b>General Purpose</b>: warnings</li><br>
<i>(Note: only models from scikit-learn could be used for this project.)</i>

## Dataset
The dataset consists of 29 features and 2 target features (one for binary, one for multiclass). It includes crucial features such as patient identifiers, demographic information, health-related details, historical healthcare utilization, admission specifics, vital signs, discharge information, length of hospital stay, lab tests, procedures, medications, and diagnostic codes. <br>
For more detailed explanation of attributes, click [here](https://github.com/Joana-Goncalves/ML_Hospital_Readmissions/blob/main/attribute_table.png).<br>
In the [Datasets folder](https://github.com/Joana-Goncalves/ML_Hospital_Readmissions/tree/main/Datasets), there are two available datasets, the train (model training and validation) and test data (performance of trained models on unseen data).

## Preprocessing
### Steps taken:
<li><b>Data Reading and Transformation</b>: Utilized Pandas to read the train file, defining 'encounter_id' as the DataFrame index. Simplified variable names for clarity and categorized variables into metric and non-metric features.</li>
<li><b>Duplicated Values</b>: Checked for duplicated rows to ensure data integrity.</li>
<li><b>Data Visualization</b>: Plotted feature distributions using histograms and box plots to identify outliers. Applied transformations to stabilize distributions and normalize data.</li>
<li><b>Outlier Handling</b>: Employed Visual Inspection method to identify and remove outliers based on box plots criteria.</li>
<li><b>Missing Values</b>: Handled missing values by dropping features with more than 50% missing data. Replaced missing values in specific features based on metadata insights and assumptions. Imputed missing values for remaining categorical variables using mode.</li>
<li><b>Feature Selection</b>: Dropped irrelevant features such as 'country' and 'patient_id' to streamline the dataset.</li>

## Feature Engineering
### Steps taken:
<li><b>Mapping Categorical Features</b>: Categorized and mapped variables like 'age', diagnosis features, 'discharge_disposition', and 'admission_source' to simplify and extract relevant information.</li>
<li><b>Handling Missing Values</b>: After mapping, missing values were handled. New features like 'recurrency', 'patient_severity', 'medication_change_ratio', 'number_prior_visits', 'lab_tests_to_medications_ratio', and 'age_times_medications' were created based on insights from the data.</li>
<li><b>Data Exploration</b>: Plotted histograms to analyze distributions of new features and check for transformations. Also, assessed correlations between new and existing features.</li>
<li><b>Encoding Categorical Variables</b>: Encoded categorical features using Label Encoder.</li>
<li><b>Data Scaling</b>: Utilized robust scaler to scale the data, maintaining distribution and handling outliers effectively.</li>

## Binary Classification
### Feature Selection
<li><b>Techniques Used</b>: Employed various feature selection techniques including Mutual Information, Boruta, Recursive Feature Elimination (RFE), Ridge Regression, Select K Best, LASSO Regression, and Chi-Square.</li>
<li><b>Optimal Features Determination</b>: Selected 14 features based on Select K Best and RFE with Cross-Validation, ensuring improved model performance and interpretability.</li>
<li><b>Feature Sets</b>: Derived two feature sets based on consensus from multiple feature selection methods, ensuring robustness.</li>

### Modelling Approach
<li><b>Model Exploration</b>: Tested multiple models including Logistic Regression, Decision Trees, Random Forest, Hist Gradient Boosting, K-Nearest Neighbors, Naive Bayes, Support Vector Machines, and Neural Networks to identify promising candidates.</li>
<li><b>Handling Class Imbalance</b>: Utilized Random Over Sampler and Random Under Sampler to address class imbalance.</li>
<li><b>Scalability</b>: Explored Min-Max, Z-score, and Robust Scaler for feature normalization.</li>
<li><b>Model Selection</b>: Narrowed down to Random Forest, Hist Gradient Boosting, and Stacking models for further evaluation.</li>

### Performance Assessment
<b>Evaluation Metrics</b>: Utilized F1 score as the primary metric for model evaluation, considering its significance in identifying incorrectly classified cases.
<table>
  <tr>
    <th>Model</th>
    <th>F1</th>
    <th>Mean Accuracy</th>
    <th>Train Score</th>
    <th>Test Score</th>
  </tr>
  <tr>
    <td>Random Forest</td>
    <td>0.70</td>
    <td>0.760</td>
    <td>0.789</td>
    <td>0.695</td>
  </tr>
  <tr>
    <td>Hist Gradient Boosting</td>
    <td>0.66</td>
    <td>0.685</td>
    <td>0.693</td>
    <td>0.658</td>
  </tr>
  <tr>
    <td>Stacking (NN + ET)</td>
    <td>0.64</td>
    <td>0.684</td>
    <td>0.690</td>
    <td>0.644</td>
  </tr>
</table>

<b>Conclusion:</b> For model selection, we opted for a Stacking model comprising a Neural Network classifier and an Extra Trees classifier due to its effectiveness in achieving balanced performance across metrics.

## Multiclass Classification
### Feature Selection
<li><b>Techniques Used</b>: Employed Mutual Information, Boruta, RFE, Select K Best, LASSO Regression, and Ridge Regression for feature selection.</li>
<li><b>Optimal Features Determination</b>: Selected 19 features based on cross-validation scores and feature importance rankings from multiple techniques.</li>

### Modelling Approach
<li><b>Model Selection</b>: Tested models including Decision Tree, Random Forest, AdaBoost, Neural Networks, and Naïve Bayes.</li>
<li><b>Handling Class Imbalance</b>: Utilized Random Under Sampler to address class imbalance and improve computational efficiency.</li>
<li><b>Consideration for Model Selection</b>: Chose models based on their interpretability, ability to handle complex relationships, and computational efficiency.</li>

### Performance Assessment
<b>Evaluation Metrics</b>: Utilized Macro-Averaging for fair evaluation of all classes, considering equal weight for each class.
<table>
  <tr>
    <th>Model</th>
    <th>F1</th>
    <th>Mean Accuracy</th>
    <th>Train Score</th>
    <th>Test Score</th>
  </tr>
  <tr>
    <td>AdaBoost</td>
    <td>0.60</td>
    <td>0.536</td>
    <td>0.597</td>
    <td>0.544</td>
  </tr>
  <tr>
    <td>Random Forest</td>
    <td>0.59</td>
    <td>0.530</td>
    <td>0.672</td>
    <td>0.590</td>
  </tr>
</table>

<b>Conclusion:</b> Adaptive Boosting slightly outperformed Random Forest with a mean accuracy score of 0.5970 against 0.59059.

## Conclusion
Based on the analysis conducted for both binary and multiclass classification tasks, we arrived at some significant conclusions. Firstly, our chosen models demonstrated promising predictive capabilities, with probabilities of patient readmission calculated at 8% for multiclass classification and 40% for binary classification. These probabilities were derived from a careful assessment of true positives and false positives within relevant classes.

Moreover, the features selected for model inclusion align well with our initial research objectives, emphasizing factors such as hospital length of stay, medication, and associated diagnoses. Notably, the 'recurrency' feature emerged as particularly influential, reflecting the heightened risk associated with repeated patient admissions.

Despite these promising outcomes, our study encountered certain limitations. We are almost certain, that we can achive better scores by engineering better features from the existing dataset. We faced some challenges in picking the right tools and techniques for our study, and the process of analyzing the data was time-consuming. Despite these challenges, our models performed similarly well.

## TODO in future:
<li>Improve feature engineering by adding more features</li>
<li>Improve final model scores</li>
<li>Add requirements.yml file to readme</li>
<li>Add installation and usage part to readme</li>
