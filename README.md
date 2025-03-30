# BTT WiDS Datathon - Team Thalamus

---

### **👥 Team Members**

| Harsita Keerthikanth | @harsita-keerthi | Performed exploratory data analysis, data processing, and built baseline model |

| Meenakshi Sundarrajan | @Meenakshi2004 | Modified hyperparameter tuning & accuracy and model testing |

| Krit Ravichandran | @krit.rr | Performed data processing, built model, performed hyperparameter tuning |

| Srewashi Mondal | @srewashimondal | Focused on trying to improve the model through continuous testing |

---

## **🏗️ Project Overview**

**Describe:**

* The name of the Kaggle competition is WiDS: AI for Female Brain Health. Kaggle Competition Host is Women in Data Science Worldwide. Its connection to the Break Through Tech AI Program is the machine learning skills we learned throughout the program. In BTT AI, we learned essential ML concepts such as data preprocessing, training models, and working with datasets, which directly prepared us for competitions like this.

* The objective of the challenge is using fMRI data to build a model to predict both an individual’s gender and their ADHD diagnosis (target variables: 1) ADHD (1 - yes, 0 - no) and  2) female (1 - yes, 0 - no)).

Project Question: “What brain activity patterns are associated with ADHD; are they different between males and females, and, if so, how?”

* The real-world significance of the problem and the potential impact of your work is to help girls and women be diagnosed with ADHD earlier, allowing them to get more equitable accommodations.

---



## **📊 Data Exploration**

**Describe:**

* The dataset(s) used (i.e., the data provided in Kaggle \+ any additional sources) 
The dataset provided in Kaggle is part of the Healthy Brain Network (HBN) initiative by Child Mind Institute. The datasets consist of functional MRI connectome matrices, socio-demographic information, emotional assessments, and parenting data for over 1,200 children and adolescents. 

* Data exploration and preprocessing approaches
We used Pandas and NumPy to clean and organize data. To ensure all features were on the same scale, we applied StandardScaler. Using SMOTETomek, we worked on class imbalance, which is when a target class has more samples than another. We filled in missing values and dealt with outliers through imputation. The preprocessing helped ensure that the data we worked with for our model is clean and balanced.

* Challenges and assumptions when working with the dataset(s)
One challenge we faced was trying to improve our accuracy score.

**Data Visualizations:**

<img width="693" alt="Screenshot 2025-03-22 at 10 34 37 AM" src="https://github.com/user-attachments/assets/5403cdb3-0d7a-419b-9a64-0cc6b5ce4645" />
<img width="633" alt="Screenshot 2025-03-22 at 10 35 39 AM" src="https://github.com/user-attachments/assets/60bc14fc-8ec3-49ff-90cd-df5e1758f782" />
<img width="635" alt="Screenshot 2025-03-22 at 10 35 53 AM" src="https://github.com/user-attachments/assets/cc571107-39cc-4be9-84c6-f6291569c04b" />

## **🏗️ Model Development**

## **🏗️ Model Development**  

### **🔹 Baseline Models**  
We started with Logistic Regression models as our baseline for both ADHD and Sex classification. These models provided a reference point to measure improvements from tuning and ensemble methods.  

#### **📊 ADHD Baseline Model:**  
- **Accuracy:** 65.02%  
- **F1-score:** 0.74 (ADHD), 0.44 (non-ADHD)  
- **🔍 Observation:** The model was better at detecting ADHD-positive cases but struggled to correctly classify non-ADHD cases, indicating an imbalance in predictive performance.  

#### **📊 Sex Baseline Model:**  
- **Accuracy:** 72.84%  
- **F1-score:** 0.80 (Male), 0.57 (Female)  
- **🔍 Observation:** The model performed well for male classification but had lower recall for female classification, suggesting bias toward the majority class.  

---  

### **🔹 Hyperparameter Tuning**  
To improve performance, we fine-tuned the Logistic Regression models using **GridSearchCV**, optimizing parameters like solver, penalty type, and class weights to better handle class imbalances.  

#### **🚀 Tuned ADHD Model:**  
- **Best Parameters:** `solver=liblinear, penalty=l1, class_weight=balanced, C=1.0`  
- **Accuracy:** 74.07% (**+9% improvement**)  
- **🔍 Key Takeaway:** Tuning significantly improved the model’s ability to detect ADHD cases while slightly improving recall for non-ADHD cases.  

#### **🚀 Tuned Sex Model:**  
- **Best Parameters:** `solver=newton-cg, penalty=l2, class_weight=balanced, C=1.0`  
- **Accuracy:** 74.89% (**+2% improvement**)  
- **🔍 Key Takeaway:** Performance improved slightly, but female classification recall remained a challenge.  

---  

### **🔹 Ensemble Models**  
To further enhance accuracy, we combined predictions from multiple models—**Logistic Regression (LR), Random Forest (RF), and XGBoost (XGB)**—to create an ensemble model.  

#### **🏆 ADHD Ensemble Model:**  
- **Accuracy:** 76.95%  
- **F1-score:** 0.84 (ADHD), 0.61 (non-ADHD)  
- **Best Individual Model:** **XGBoost (78.60% accuracy)**  
- **🔍 Observation:** The ensemble approach improved overall classification, balancing recall across ADHD and non-ADHD cases.  

#### **🏆 Sex Ensemble Model:**  
- **Accuracy:** 75.31%  
- **F1-score:** 0.83 (Male), 0.58 (Female)  
- **Best Individual Model:** **Logistic Regression (74.89% accuracy)**  
- **🔍 Observation:** The ensemble slightly improved classification, but female classification recall remained lower than desired.  


## **Setup**

### **Clone the Repository**

To get started, clone the repository to your local machine:
<ul>
    <li><code> git clone https://github.com/your-username/adhd-sex-prediction.git </code></li>
    <li><code> cd adhd-sex-prediction </code></li>
</ul>

### **Install Dependencies**

Install the required Python dependencies by running the following:
<ul>
    <li><code> pip install -r requirements.txt </code></li>
</ul>




