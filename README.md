# BTT WiDS Datathon - Team Thalamus

## **👥 Team Members**

| Name                  | GitHub Handle        | Contribution                                                         |
|--|-|-|
| Harsita Keerthikanth  | @harsita-keerthi     | Performed exploratory data analysis, data processing, and built baseline model |
| Meenakshi Sundarrajan  | @Meenakshi2004       | Modified hyperparameter tuning & accuracy and model testing          |
| Krit Ravichander       | @krit.rr             | Performed data processing, built model, performed hyperparameter tuning |
| Srewashi Mondal       | @srewashimondal      | Focused on trying to improve the model through continuous testing    |

## **🏗️ Project Overview**

**Describe:**

* The name of the Kaggle competition is WiDS: AI for Female Brain Health. Kaggle Competition Host is Women in Data Science Worldwide. Its connection to the Break Through Tech AI Program is the machine learning skills we learned throughout the program. In BTT AI, we learned essential ML concepts such as data preprocessing, training models, and working with datasets, which directly prepared us for competitions like this.

* The objective of the challenge is using fMRI data to build a model to predict both an individual’s gender and their ADHD diagnosis (target variables: 1) ADHD (1 - yes, 0 - no) and  2) female (1 - yes, 0 - no)).

Project Question: “What brain activity patterns are associated with ADHD; are they different between males and females, and, if so, how?”

* The real-world significance of the problem and the potential impact of your work is to help girls and women be diagnosed with ADHD earlier, allowing them to get more equitable accommodations.

# **🎯 Project Highlights**

- **Built a Logistic Regression Model**: Developed baseline models for both ADHD and Sex classification using Logistic Regression to understand initial performance and set a benchmark.
  
- **Enhanced Performance Through Hyperparameter Tuning**: 
  - Used **GridSearchCV** to tune the **solver, penalty, and class weights** for Logistic Regression, improving accuracy and reducing bias towards the majority class.
  - Achieved a **9% improvement in the ADHD model** and a **2% improvement in the Sex classification model**.

- **Implemented Ensemble Learning**: 
  - Combined predictions from **Logistic Regression, Random Forest, and XGBoost** to create an ensemble model, boosting overall performance and achieving a **76.95% accuracy in ADHD** and **75.31% in Sex classification**.
  - This approach balanced performance between classes, especially improving detection for non-ADHD and female cases.

- **Explored Kaggle Dataset**: 
  - Submitted the **Ensemble Model** to Kaggle, where it achieved an accuracy of **~65%**, highlighting the challenge of model generalization to unseen data.

- **Addressed Class Imbalances**: Focused on balancing **class weights** for both ADHD and Sex models to reduce bias, leading to more balanced F1-scores across different classes.

- **Refined ADHD and Sex Classification Models**: 
  - Successfully built models that addressed specific challenges like ADHD detection accuracy and improving female detection in the sex classification task.

# **🛠️ Setup & Execution**

### **Clone the Repository**

To get started, clone the repository to your local machine:
<ul>
    <li><code> git clone https://github.com/team-thalamus/btt-team-thalamus.git </code></li>
    <li><code> cd btt-team-thalamus </code></li>
</ul>

### **Install Dependencies**

Install the required Python dependencies by running the following:
<ul>
    <li><code> pip install -r requirements.txt </code></li>
</ul>

# **📊 Data Exploration**

**Describe:**

* **Dataset:** 
The dataset provided in Kaggle is part of the Healthy Brain Network (HBN) initiative by Child Mind Institute. The datasets consist of functional MRI connectome matrices, socio-demographic information, emotional assessments, and parenting data for over 1,200 children and adolescents. 

* **Data exploration and preprocessing approaches:**
We used Pandas and NumPy to clean and organize data. To ensure all features were on the same scale, we applied StandardScaler. Using SMOTETomek, we worked on class imbalance, which is when a target class has more samples than another. We filled in missing values and dealt with outliers through imputation. The preprocessing helped ensure that the data we worked with for our model is clean and balanced.

* **Challenges and assumptions:**
One challenge we faced was trying to improve our accuracy score.

**Data Visualizations:**

<img width="693" alt="Screenshot 2025-03-22 at 10 34 37 AM" src="https://github.com/user-attachments/assets/5403cdb3-0d7a-419b-9a64-0cc6b5ce4645" />
<img width="633" alt="Screenshot 2025-03-22 at 10 35 39 AM" src="https://github.com/user-attachments/assets/60bc14fc-8ec3-49ff-90cd-df5e1758f782" />
<img width="635" alt="Screenshot 2025-03-22 at 10 35 53 AM" src="https://github.com/user-attachments/assets/cc571107-39cc-4be9-84c6-f6291569c04b" />

# **🏗️ Model Development**

## 🔹 Baseline Models
We started with Logistic Regression models for ADHD and Sex classification. This helped us understand how well the models perform without any adjustments.

### 📊 ADHD Baseline Model:
- **Accuracy:** 65.02%
- **F1-score:** 0.74 for ADHD, 0.44 for non-ADHD
- **Explanation:** The model was good at detecting ADHD cases but had trouble correctly predicting non-ADHD cases. This shows the model was biased towards the ADHD class and not balanced. We need to improve the accuracy for non-ADHD cases.

### 📊 Sex Baseline Model:
- **Accuracy:** 72.84%
- **F1-score:** 0.80 for Male, 0.57 for Female
- **Explanation:** The model worked well for predicting male cases but struggled with female cases, which is a sign of bias in the data or the model not being sensitive to features that differentiate females from males.

<img width="479" alt="ADHD Baseline Model" src="https://github.com/user-attachments/assets/9e6e49af-71ba-4cde-8ff4-eb08b3d3771e" />


## 🔹 Hyperparameter Tuning
We used GridSearchCV to fine-tune the Logistic Regression models, adjusting settings like penalty types and class weights. This was done to improve performance, especially for underrepresented groups (like non-ADHD and females).

### 🚀 Tuned ADHD Model:
- **Best Parameters:** `solver=liblinear, penalty=l1, class_weight=balanced, C=1.0`
- **Accuracy:** 74.07% (+9% improvement from baseline)
- **Explanation:** By balancing class weights, the model paid more attention to non-ADHD cases, which helped improve its detection. The L1 penalty helped make the model more focused on the key features, leading to better overall performance.

### 🚀 Tuned Sex Model:
- **Best Parameters:** `solver=newton-cg, penalty=l2, class_weight=balanced, C=1.0`
- **Accuracy:** 74.89% (+2% improvement from baseline)
- **Explanation:** The tuned model improved, but female detection still lagged behind. Even though balancing the weights helped, the features in the dataset might not have been enough to distinguish female cases effectively, which led to a smaller improvement.

<img width="949" alt="Sex Baseline Model" src="https://github.com/user-attachments/assets/69cfb464-47e4-4b9b-aa7a-b10fd258be90" />

## 🔹 Ensemble Models
We tried using multiple models together (Logistic Regression, Random Forest, XGBoost) to create an ensemble model, hoping to combine their strengths and boost performance.

### 🏆 ADHD Ensemble Model:
- **Accuracy:** 76.95%
- **F1-score:** 0.84 for ADHD, 0.61 for non-ADHD
- **Best Individual Model:** XGBoost (78.60% accuracy)
- **Explanation:** The ensemble model was better at detecting both ADHD and non-ADHD cases compared to any single model. However, XGBoost performed the best individually in terms of raw accuracy, but the ensemble combined strengths from all models to create a more balanced output.

### 🏆 Sex Ensemble Model:
- **Accuracy:** 75.31%
- **F1-score:** 0.83 for Male, 0.58 for Female
- **Best Individual Model:** Logistic Regression (74.89% accuracy)
- **Explanation:** The ensemble helped a little, but female detection was still problematic. Since Logistic Regression performed almost as well as the ensemble, it suggests that the issue is more data-related rather than model-related.

<img width="466" alt="ADHD Ensemble Model" src="https://github.com/user-attachments/assets/f76e8523-10e0-4ae4-88d3-39fb23767976" /> <br>

<img width="947" alt="Sex Ensemble Model" src="https://github.com/user-attachments/assets/03786fe3-f1b3-4080-ba4c-8eb6576a16af" />

# 🎯 Final Model & Kaggle Results
After testing all models, the Ensemble Model was submitted to Kaggle because it showed the best overall performance.

- **Final Model Submitted:** Ensemble Model
- **Kaggle Accuracy:** 0.64427
- **Explanation:** The Kaggle result was lower than our training results (around 75-78%). This drop in performance suggests that the model didn't generalize well to unseen test data. This could mean there are differences between the dataset used for training and the one on Kaggle, or our model was slightly overfitting to the training data.

<img width="405" alt="Screenshot 2025-03-30 at 4 50 51 PM" src="https://github.com/user-attachments/assets/130897cf-7466-4930-9a64-510715a0af44" />


# **🖼️ Impact Narrative**

1. What brain activity patterns are associated with ADHD; are they different between males and females, and, if so, how?

    Our model found patterns in fMRI data linked to ADHD. Males and females showed some differences in brain activity, but more research is needed.

2. How could your work help contribute to ADHD research and/or clinical care?

    Our work helps improve ADHD detection, especially in females, leading to earlier diagnosis and better accommodations.


# **🚀 Next Steps & Future Improvements**
**Limitations:**
* The model struggles with female detection and non-ADHD classification.
* Accuracy drops on unseen data (Kaggle results lower than training performance).

**Future Improvements:**
* Use more advanced deep learning models.
* Try feature selection to improve model focus.
* Collect or explore more diverse datasets for better generalization.








